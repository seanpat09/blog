[Bootstrap](http://getbootstrap.com/) is the most popular front-end web design framework and is usually my go to when I want to quickly create a user interface that is visually appealing and mobile friendly. I'll be the first to admit that I am not that great at design (just look at this blog!), so frameworks like Bootstrap are a godsend. Using Bootstrap with Salesforce (at least the classic view) can be a huge pain because of the conflicting stylesheets from the sidebar and header:

![Conflicting Styles](http://i.imgur.com/L8GIsTy.png)

This isn't the case in Salesforce Lightning, but there are plenty of organizations that are not ready for the transition to the new interface. I knew that the answer to this problem was just to namespace the Bootstrap, but the execution involved running commands with Ruby, Sass, and Node, which for a while was just non-Salesforce magic that I dared not touch. For a few years I just avoided using Bootstrap in Salesforce, opting to just style everything myself. If you've ever felt this way, then this post is the hand holding you might be looking for.

##TL;DR
If you really don't want to do this, here's the namespaced CSS that you can just include in your project now:
https://gist.github.com/seanpat09/6207236541d701da40ce

It doesn't include the glyphicon fonts, but pretty much everything else is there. 


##Namespacing Bootstrap
(This is mainly for Mac users. Linux will largely be the same. Sorry Windows users)

Run all these commands in Terminal


###Install the dependencies on your machine
####1. Make sure you have Ruby installed

Ruby comes pre-installed on Macs, but here's how you check for sure:

```
Your-Macintosh:~ seancuevo$ ruby -v
ruby 2.0.0p481 (2014-05-08 revision 45883) [universal.x86_64-darwin14]
```

If somehow you see something like this:
```
Your-Macintosh:~ seancuevo$ ruby -v
-bash: ruby: command not found
```

Then you need to install [Ruby](https://www.ruby-lang.org/en/documentation/installation/)

####2. Install [Sass](http://sass-lang.com/install)
```
gem install sass
```
If you see any errors, trying running this:
```
sudo gem install sass
```

####3. Install [nvm](https://github.com/creationix/nvm)
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.30.1/install.sh | bash
```

####4. Install [node.js](https://nodejs.org/en/) using nvm
```
nvm install 5.0
```
You can use node in your terminal session with:
```
nvm use 5.0
```

You now have all the tools necessary to namespace Bootstrap!

###Compile a namespaced version of Bootstrap
You can run the following commands from whatever directory you want, but just make sure to stay in that directory as all the files will be written to the directory and all of the commands will be relative to it.

####1. Start node:
```
nvm use 5.0
```

####2. Install Bootstrap-sass
```
npm install bootstrap-sass
```
This creates a folder called **node_modules** in your current directory. This contains files necessary to compile bootstrap 

####3. Create the .scss file
In the same directory, create a file called sfdcBootstrap.scss with the following contents
```
.sfdcBootstrap{
    $icon-font-path: "fonts/bootstrap/";
    @import "node_modules/bootstrap-sass/assets/stylesheets/bootstrap";
}
```

This will create the bootstrap css file where only styles that descend from the .sfdcBootstrap class are affected by Bootstrap. You can name the class whatever you want, just make sure to change it in the .scss file.

####4. Compile your css file with Sass
In the same directory, run this command in Terminal:
```
sass sfdcBootstrap.scss sfdcBootstrap.css
```
You should now have a file called sfdcBootstrap.css in your directory.

####5. Build your static resource
Run this command to open your current directory in Finder:
```
open .
```

* In Finder, create another folder and put the sfdcBootstrap.css in it.
* In the node_modules folder, navigate to bootstrap-sass > assets.
* Copy the fonts folder and place that in the same folder as sfdcBoostrap.css. 
* Select both sfdcBoostrap.css and the fonts folder, right click and select **Compress 2 Items**
* Rename the resulting archive file to **sfdcBootstrap** and upload to Salesforce as a static resource.

###Use your namespaced bootstrap in your Visual Force Page
Here is a sample Visual Force page using the resource:
```
<apex:page showHeader="true" sidebar="true" controller="MassInsertProtoCtrl">
    <apex:stylesheet value="{!URLFOR($Resource.sfdcBootstrap, 'sfdcBootstrap.css')}" />
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>
    <div class="sfdcBootstrap">
      Formatted with bootstrap!
    </div
    Not formatted with bootstrap!
</apex:page>
```
Everything outside of the sfdcBootstrap div (which includes the sidebar and header) will NOT be formatted with Bootstrap

![Namespaced Bootstrap](http://i.imgur.com/bvLb6n0.png)



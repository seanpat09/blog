#The Hidden Cost of Technical Debt

The term technical debt is frequently used in the software development world to serve as a metaphor for doing things the quick and dirty way in order to get something out of the door sooner rather than later. Just like its financial analogue, accruing technical debt is not necessarily a bad thing if the value of delivering something more quickly outweighs the development costs (i.e. the interest) of fixing the quick and dirty solution in the future. However, the interest expense analogy usually stops there, ignoring the less quantifiable, more human side of debt that could end up costing more.

Technical debt often rears its head during overtime nearing a project deadline. When time is short and features can't be cut, then the first thing to go is code quality. Tests go missing, code becomes hard to read, and the project become a little less maintainable. It's not ideal, but that's fine. Developers understand that code is never going to be perfect and that delivering something a little buggy is better than tanking because they never pulled the trigger.

But then the next deadline comes and it happens again. And again. Instead of allowing for time to fix the issues from before, the developers are pushed to keep tacking on more garbage to the heaping pile of garbage that is the code base. Any blocking bug fixes, let alone features, become day long tasks because no one is quite sure how everything works anymore because everything is all over the place.

Working somewhere like this, to use a technical term, sucks. Bad code is no longer the exception, but the norm. A sense of disgust takes place of any pride in the project. Developers no longer feel like their growing, but just fighting to get around the mess they made. An us vs. them mentality grows between the development team and management.

Cutting out features and taking time to clean things up may seem like a hit to both progress and budget, but technical debt costs the most when the people that are able to pay it down say "fuck it" and leave. 

##What you can do if you are a manager

1. **Trust your developers:** You need to trust in the expertise of your developers. If they say something cannot be finished in time without sacrificing quality, you need to believe them and figure out what realistically can be done. When time is running short then cut features in lieu of sacrificing quality. Doing a few things really well is a lot better than sucking at a lot of things.

2. **Allow for time to pay back technical debt:** After something is delivered, take a sprint/iteration/etc. to clean things up before diving into the next project. It's good for the code and a productive way to do a retrospective on what was just accomplished.

3. **Don't lie about deadlines:** This might seem obvious, but I've seen managers do this. These aren't dinner reservations, don't expect them to be late and say they have one month when they actually have five weeks. Instead, you'll get something that hobbles across the finish line of one month deadline and then a slew of bug fixes that'll probably break during the last week.

##What you can do if you are a developer

1. **Communicate with your manager:** It's easy to dismiss your non-technical manager as someone who won't understand what you are doing. And the truth is, if you don't tell them, they won't understand. Let them know if you think a project is too big, if you underscoped a feature, or if you are feeling burned out. And do it sooner rather than later so they actually have a chance to do something about it.

2. **Don't overpromise:** Be realistic about what you can deliver. I've seen too many overconfident developers trying to appease managers and then scrambling at the deadline. A good manager looks to you for your expertise, so be honest.

3. **Establish a culture of good code:** This is a little out of scope for this post, but don't let people get away with bad code. Technical debt should be a conscious decision, not a lazy one.

Just like financial debt, technical debt should be treated with balance. When used correctly, it can be leveraged to produce value quickly and promote long term growth. When abused, it can create toxic build up that will eventualy paralyze a project and possibly even lead to the downfall of the company. Take steps now to manage your technical debt it before you lose not only control of the project, but also the key members of your team.
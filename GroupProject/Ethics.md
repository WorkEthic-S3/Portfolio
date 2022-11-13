# Ethics

## What is ethics?

Ethics is a branch of philosophy that looks at actions of individuals in society, and whether those actions are morally right or wrong. It's not the same as following the law of the country you reside in. Those laws are born from ethical standards accepted by a group of people, usually of the same ethnicity. Their moral standards can be influenced by a number of things, whether it be religious background or culture.

Ethics also isn't blindly accepting what society deems acceptable. Those standards can still deviate from what is ethical. If ethics were determined by whatever society deems acceptable, you'd have to find out what society thinks when debating an ethical dilemma.

## Ethics in software engineering

When it comes to technology and even more specifically software engineering, ethics come into play during different aspects of development. That can be during the development itself, the handling of user data or communication with everyone involved like: customers, colleagues or the end users.

Some of the guidelines from the Code of Ethics and Professional Conduct:

-   Contribute to society and to human well-being, acknowledging that all people are stakeholders in computing.

-   Avoid harm.

-   Be honest and trustworthy.

-   Be fair and take action not to discriminate.

-   Respect the work required to produce new ideas, inventions, creative works, and computing artifacts.

-   Respect privacy.

-   Honor confidentiality.

### Why is ethics important in software engineering

The software you create are able to reach huge audiences regardless of whether your software is trying to entertain people, automate a process in their lives or assist them during tasks they have to perform. When dealing with software that can reach these big groups of people, developers have to be aware of the consequences their actions can bring with them and make choices with the public interest in mind.

### What can a developer do to make ethical sofware?

The Code of Ethics and Professional Conduct talks about the guidelines to follow if someone works on software. Some of these might be more obvious than others. We all know that one of the first points to follow is to create software for the benefit of society, and shouldn't pose a threat to health and safety. That also means not create software for criminal goals, like exploiting the vulnerable.

Another one that might be obvious is being truthful. That doesn't only mean, not stealing and things of that nature. It also means being truthful about one's experience or knowledge when it comes to the development of computer systems. Someone should not, for example, hide their lack of experience in order to achieve something, since it may have consequences in the future.

These are just some of the points talked about in the [Code of Ethics and Professional Conduct](https://www.acm.org/code-of-ethics). It has many more, equally as important, points explained in great detail.

## Ethics in our group project

For our group project we created a webapplication for people who use parking garages to park their vehicles. This webapp allows people to make reservations for a parkingspot for a period of time to ensure they have a place to leave their car. They can also drive inside without making/having a reservation, during which the webapp will create a reservation for them, the only difference is, the time of exit is not known.

### User data

Although the webapp doesn't contain too many features, ethics still come into play. The handling of user data is an important one. It is required to handle user data responsibly and to do anything in a developer's power to ensure it is safe. This point was also brought up by one of the PO's during our first meeting.

We talked about authentication with the group, since that was one of the first features to be implemented. One can choose to create their own authentication-system, or go for a third-party system. The difference is that going for a third-party component might be much more secure, granted it's developed by developers who know what they're doing. If someone were to create their own, chances are high that there are many vulnerabilities in that system that can be abused.

So we decided to use OAuth 2.0 with Google. OAuth is a frequently used and trusted authentication system, which you can use to authenticate your users. It seemed like a very safe way to interact with user data. And since most people already have a Google account, they don't need to go through an annoying form and create a whole new one. No unnecessary user data is saved either. The only piece of data that is saved is an ID that is provided by Google. We use that ID to, for example, link a reservation to a specific user.

### Code quality

The software needs to be working well for the end users that are going to be using it. For that the code needs to be tested. We have talked about the topic of testing and are going to be implementing tests for our code to make sure nothing breaks during the development phase. Even the features that have been tested and implemented by developers need to be checked constantly to make sure a new feature hasn't broken anything, and isn't discovered when it's too late.

The team keeps an eye on each other's work aswell. For one, nobody is allowed (or able for that matter) to push code to the `main` branch. There's a seperate `development` branch from which other branches are created for specific features. When these features are finished the developer can open a `Pull Request` to merge the code with the `development` branch. Before that is able to happen, another developer has to approve the `Pull Request` first. That way we constantly keep an eye out for each other's code and make sure nothing weird is being pushed.
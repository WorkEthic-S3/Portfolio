 # Reader's Guide - Semester 3 - Gökay Atalay

My portfolio for semester 3 of the Software Engineering Bachelor's program, Fontys Hogescholen.

## 1. Introduction

This file serves as the reader's guide for my semester 3 portfolio. This portfolio contains the products I have developed during the semester. The products this portfolio contains include, but are not limited to: applications (frontend and backend), research reports, software-technology guides and more. With these products I wish to prove that I have sufficient knowledge to have reached the learning outcomes. I'll be explaining each section and provide a link to the product the section talks about.

## 2. Learning Outcomes

| # | Title                           | Description                                                                                                                             |
|---|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| 1 | Web application                 | You design and build user-friendly, full-stack web applications.                                                                        |
| 2 | Software quality                | You use software tooling and methodology that continuously monitors and improve the software quality during software development.       |
| 3 | Agile method                    | You choose and implement the most suitable agile software development method for your software project.                                 |
| 4 | CI/CD                           | You design and implement a (semi)automated software release process that matches the needs of the project context.                      |
| 5 | Cultural differences and ethics | You recognize and take into account cultural differences between project stakeholders and ethical aspects in software development.      |
| 6 | Requirements and design         | You analyze (non-functional) requirements, elaborate (architectural) designs and validate them using multiple types of test techniques. |
| 7 | Business processes              | You analyze and describe simple business processes that are related to your project.                                                    |
| 8 | Professional                    | You act in a professional manner during software development and learning.                                                              |


## 3. Researches

During the entire semester, research is a big subject. You're constantly researching, whether it's to fulfill the learning outcomes or solely for your own knowledge. The researched topic include technologies (mostly frameworks), CI/CD, Agile working, Ethics and more. I have listed the reports that have come out of these researches below.

### 3.1. CSRF

For both of the required researches I've decided to work with a classmate, Jordy. We have agreed with Leon van Bokhorst to do one of our researches about CSRF (Cross-Site Request Forgery). It's a way to perform attacks on webapps. It's important when it comes to webdevelopment to protect your webapps against such attacks.

We have created a seperate Github organization for our researches and this one resides in it's own repository.

[You can find our research here.](https://github.com/Gokay-Jordy-S3-Onderzoek/CSRF-Research)

### 3.2. CORS

For our second research we had agreed to do this one on CORS, it being a big topic in webdevelopment. Chances are high you've run into CORS and probably wasn't sure what caused it, same goes for us. By doing our second research about CORS we wanted to go in-depth to figure out how CORS works. Our research report can be found in the same organization by clicking the following link:

[You can find our research here.](https://github.com/Gokay-Jordy-S3-Onderzoek/CORS-Research)

</br>

## 4. Individual Project

<h1 align="center">
  Workethic
  <br>
</h1>

<h4 align="center">A platform where small businesses can find workers for their tasks.</h4>
</br>

Inspired by: [Young creators](https://youngcreators.co)</br>
To view the userstories, [click here](/IndividualProject/Userstories.md).

Workethic is a platform where small (or big, we don't discriminate) businesses can find workers who can take care of tasks that might need someone who knows what they're doing. 

Need a danceteacher to fill in your spot while you're on vacation? Need someone to install the brand new oven for your bakery? Just open a new task and wait for your potential candidates to apply, you'll be notified per email when that happens.

I use the SCRUM method of agile working for this project. The semester is divided into sprints, during which I focus on a specific area. I use Github projects to keep track of parts of the application I need to work on. I create issues for parts that need to be done and connect that issue to a merge when it's done. That way the project can be followed throughout it's development stage.
</br>

### 4.1. Web application

For the webapplication I've taken a look at distributed systems and how they work. I hadn't researched them before this semester, but turns out I had unknowingly worked with them, by using frontend apps to make API calls to external APIs. 

I divided the webapp into a frontend application and multiple backend applications. The frontend application, which is made in [React](https://reactjs.org/), is responsible for the presentation of the webapp and making calls to backend applications.

For the backend application, which is responsible for fetching and serving data, I've decided to use [Spring Boot](https://spring.io/projects/spring-boot). I've used C# a bunch, both before and during Fontys, so I wanted to try something else. Java is a language I've wanted to try for a while now so this was a good opportunity.

Because I went for a distributed system approach, I'll be using a different framework to create an endpoint for the creation of new records. To show the loosely-coupling of these projects, I'll be using a different framework for this project, I've chosen [ASP.Net Core](https://learn.microsoft.com/nl-nl/aspnet/core/?view=aspnetcore-6.0).

#### Projects:

-   [Frontend - React](https://github.com/WorkEthic-S3/S3-IP-FE-GokayAtalay)
-   [Backend - Spring Boot](https://github.com/WorkEthic-S3/S3-IP-BE-SpringBoot-GokayAtalay)
<!-- -   [Backend - Laravel](https://github.com/WorkEthic-S3/S3-IP-BE-GokayAtalay) -->

### 4.2. Software quality

#### Authentication

For extra security I've decided to use authentication using OAuth 2.0 from Google. It's alot safer to use external authentication services which are built by people who know what they're doing. If someone were to make their own little system, it would be prone to vulnerabilities and could more easily be attacked.

[You can find my OAuth guide in my frontend repository here.](https://github.com/WorkEthic-S3/S3-IP-FE-GokayAtalay/blob/main/Doc/OAuthDoc.md)

#### Code reviews

Before comitting, pushing and merging my code or researches, I make sure to have someone go over my code to make sure I'm not submitting anything that isn't supposed to be there. With code that can be as simple as showing someone on your laptop and have them go over it and ask questions about something they find questionable.

With our research we took a different approach. Whenever someone commits, the other person will go over the text they comitted and pushed and comment if there is something that catches your attention. Not only that, but if somebody wants to merge their research piece, the other person has to approve the PR (Pull Request), before it can be merged. Because of that we're constantly going over each other's work and making sure what we're merging is up to standard. 👍

#### Testing

For the code that I've written I've setup some tests. In my React project I used `react testing library` to write tests which checked that the correct things were displayed on screen. Like how the loginpage should only be shown if the user is not logged in and how the contents of the navbar should change after a user logs in. That way there is a guarantee that none of those things breaks when developing the application further. And if something *does* break, the tests will notify the developer when the workflow runs, because the tests are run during the workflow on Github Actions.

#### Code analysis

I have setup an automated workflow on Github Actions and have integrated Sonarcloud for code analysis. What that does is analyze my code when the workflow runs for security issues, smelly code, among other things. Sonarcloud offers a great dashboard which shows you the analysis reports, so you can see the state of your code in one page. If you want to go into details you can, because you can click on one of the cards, for example when there is a security issue. Sonarcloud will show you what causes the issue, why it's an issue and how to fix it.

### 4.3. Professional

For my researches and group project I will be working with others, which requires you to use some sort of system and structure.

For my researches I'm working with another classmate (Jordy). We created a [Github organization](https://github.com/Gokay-Jordy-S3-Onderzoek) in which we create repositories for our researches. Each repository has it's own ReadMe file, which will contain the research report.

We divide the research equally so we can work independently from eachother. The research contains a main question, and is divided into multiple subquestions. Each person gets a number of subquestions to work on and merge into the development branch. The other person can comment on commits if there are obvious changes that need to be made.

For each subquestion we create a seperate (feature-)branch, in which the person can freely work without any hassle. He writes his portion of the research in that branch. When he decides that his portion is finished, he'll open a pull-request and request a review from the other person. The other person reviews the work and either approves or denies the PR. If the PR is denied, the original author makes the changes that are needed to be made, if the PR is approved, the person can merge the two branches.

To be able to track the research better we create issues with the tasks that need to be completed, mainly an issue for each question. When a question is finished, reviewed and merged, we can close that issue and connect it to the corresponding merge.

### 4.4. UX

UX is a big part of applications, you want the customer/client to have a good time while using your product. Because if that's the case, they'll keep coming back and possibly recommend you to future customers/clients. I did some research into this topic to see what comes into play when designing UX and have noted my findings in the document below:

[UX research](/IndividualProject/UX.md)

### 4.5. Outsourcing

To end the semester we were asked to develop a feature from another student's project. This was to show whether your project was setup in a way that other developers could work in it without issues. To find my report on it view below document:

[Outsource Feature](/IndividualProject/Outsource.md)

## 5. Group Project

For our groupproject we worked on a parking garage app. It is a project given to us by the employees of Mediaan. It is an app people can use to make reservations for parkingspots, drive into the garage without a reservation, pay their fees, and more.

### 5.1. System Design

The team has been working on all kinds of documentation to show the way our application was built. We have made screen designs, architecture designs and an entity relation-diagram. These items evolved throughout the development of the app to accurately display the changes that were made based on feedback and other findings.

[You can view our system design here.](/GroupProject/System-Design.md)

### 5.2. Agile (Scrum)

During the development of our groupproject application, we used an Agile method called Scrum. By using this method during our development-process, we learnt alot about how Scrum works and how you can properly implement it's practices to improve your team-collaboration. Below I linked a file in which I explain what Agile working is and what Scrum practices we used in our groupproject.

[Agile working](/GroupProject/Agile.md)

### 5.3. Ethics

Ethics come into play in many different areas in life and has been talked about for millennia. After software became something the everyday public came in contact with, ethics in software became even more important. I did some research about ethics and ethics in software, which can be found below through the following link:

[Ethics in Software](/GroupProject/Ethics.md)

### 5.4. Cultural Differences

Culture and cultural differences is an important subject in software development, because you'll be working with other people. That becomes even more apparent when working with international students/colleagues. I did some research into this topic and have noted my findings in the file linked below:

[Cultural Differences](/GroupProject/Culture.md)

### 5.5. Business Process

With software you come into contact with business processes and have to think about them. Using your software you can increase the speed, automate and do other things with these processes. i did some reseach and noted my findings in the document below:

[Business Process](/GroupProject/BusinessProcess.md)

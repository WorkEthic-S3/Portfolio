# How to determine the quality of the UX for my project?

## Reliability

If you want users to keep coming back to your service/application, it has to be reliable. It has to be up and running and fast. Nobody is going to drive a car that keeps breaking down and stops working, after a while you just get annoyed and look for something else. Same goes for your website, pulling new users is one thing, keeping them is another, with the following points you can help your website/webapp keep the users that are already using it.

### Uptime

Something worse than an application with broken links and buttons, is an application that itself is broken, and down. A service that can’t be accessed might as well not exist. You want to guarantee that your application is 99.99% up to not disappoint customers. You could have the best web application but if the browser shows a “Can’t access” screen, then that would be a waste of effort.

But no matter how much effort you put into keeping your webapp online, things can always go wrong. In that case, you do want to be notified when your app goes down. You can use monitoring services to keep track of the state of your app. You can set them up to notify you when your app is down so you can start looking into the issue as soon as possible.

There are many tools that provide this service but one of them is [robot.alp](https://robotalp.com/en/website-monitoring). Robotalp seems easy to setup and has different kinds of monitoring.

### Fast loading

Before I get into fast loading, one thing you want to do is let the users know that your application is loading something in the first place. Not just a white screen in which nothing is happening, but some sort of icon to show that an operation is taking place. One way to do this is show a spinner while data is being fetched for example.

<img src="../Images/spinner.gif" width="80%"/>

Everyone knows how annoying it is when a webpage loads for too long. If it takes too long a user might change their mind on using your application and might go elsewhere. You want to optimize your application to lower loading times. Best case scenario is if your application loads almost instantly when a resource is requested. That will provide a great user experience.

To achieve this one needs to get rid of unnecessary gunk in your code. For example fancy shmancy JavaScript code that barely adds any value. Or a resource that gets requested but is not used, will unnecessarily increase loading times and worsen the user experience.

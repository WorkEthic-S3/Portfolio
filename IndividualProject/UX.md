# How to determine the quality of the UX for my project?

## Functionality

Whenever a user visits your application, it should always be working as intended. If a potential customer visits your website to take a look at your service, but sees that the website is broken, he or she will instantly lose trust and have no faith in your product. All the components in it should be working so as to not scare someone away.

### Working links

Your application will be full of links that link to other pages or maybe even an external page. A user clicks on a link with an expectation to be directed somewhere. When that doesn’t happen a user can be left disappointed. Make sure the links in your code point to existing routes that can be defined in your app.

Navigation links take a url portion as an attribute which you can use to specify to which url the app should navigate.
```html
<a href="/tasks" className="px-3 py-2 mx-3 mt-2">Tasks</a>
```

That piece of url should be registered as a route to show the user the correct page.

```javascript
<Routes>
    <Route path='/' element={<Home/>}/>
    <Route path='/login' element={<Login/>}/>
    <Route path='/tasks' element={<Tasks/>}/>
</Routes>
```

As you can see the path `/tasks` is registered in my `App.js` file, to point that path to a specific page, in this case `Tasks`.

That can be tested using, for example, React Testing Library. RTL is a library which you can use to test what the user sees. If you expect to be shown a specific page when being redirected somewhere, but that doesn’t happen, then the test will throw an error.

### Buttons

When a button is clicked it should run the operation succesfully and notify the user of said operation. If an operation fails for whatever reason, it should be handled in your code and shown to the user to let them know of the error that just occurred.

<img src="../Images/error-message.png" width="80%"/>

Above message is shown when something goes wrong fetching the data from the backend. The user is shown no specific data on the request or response, but is only shown a general message notifying them that an operation took place but failed.

<img src="../Images/console-error-message.png"  width="80%"/>

Although above console message is shown whether or not you catch the error, this adds no value since a normal guest of your webapp has no idea this is being output. It's also not professional to just leave the message there and do nothing with it, and just leave the user to wonder what's happening because the screen stays on white.

<img src="../Images/success-message.png" width="80%">

Same goes for successful events. When a user successfully creates a task, the user should be notified if the operation goes well. Only redirecting them with no message still doesn't help the user fully understand the status of the operation. That's why when an operation is successful, a success message should be shown to inform the user of the status.

You can watch recordings of users clicking around on your website to see whether the links and operations work properly. You can use tools like [Crazy Egg](https://www.crazyegg.com/recordings?utm_source=google&utm_medium=blog) to create these recordings.

## Reliability

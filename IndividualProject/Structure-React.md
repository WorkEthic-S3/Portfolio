# Structure React Project

While I was working on my projects, a structure came to life to help me during the development process. It helps the developer find code and expand the codebase without any issues. When stuff does goes wrong portions of the code can be found easily, because of how everything is put into components. I would like to explain a bit on how my project is structured and how everything works.

## Table of contents
1. [Routing](#routing)
    1. [Index.js](#indexjs)
    2. [App.js](#appjs)
2. [Saving data within application](#saving-data-within-application)
3. [Pages](#pages)
4. [Components](#components)
5. [Services](#services)
    1. [setUserSession](#setusersession)
    2. [getUserSession](#getusersession)
    3. [deleteUserSession](#deleteusersession)

## Routing

### Index.js

My `index.js` file contains only a small change but a necessary one. To make the routing in my application work I use a package called [React Router](https://github.com/remix-run/react-router). This package contains a `BrowserRouter` component which I use in my `index.js` file to wrap my `App` component.

```javascript
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <ChakraProvider>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </ChakraProvider>
);
```

### App.js

`App.js` contains a bit more than the previous file. Now that the app is wrapped in a router component, we can define our routes which will be used throughout our app. Every page which a user will be able to navigate to, should be mentioned in this file with an appropriate route attached.

```javascript
return (
    <div className="App">
        <userContext.Provider value={value}>
        <Navbar/>
        <Routes>
            <Route path='/' element={ <Tasks/> }/>
            <Route path='/login' element={<Login/>}/>
        </Routes>
        </userContext.Provider>
    </div>
);
```
*An example of some routes.*

As you can see in the example above, in the `return` we open and close a `Routes` component. In this component, for each individual route, we can specify which `path` leads to which page. The components (Tasks and Login) mentioned in the `element` property are seperate components which act as pages.

## Saving data within application

One can save all sorts of data in the application. In my case I save the logged in user, to be able to use their data in whichever page I might need to. There are a couple of ways to do this, the most used methods being [Redux](https://redux.js.org/) and [Context](https://reactjs.org/docs/context.html). I chose for context in this project, because this wasn't going to be a huge part of the application, so context seemed enough to work with.

I start of by creating a new context component called `userContext.js`. After that we can use the `createContext()` method to create the context itself.

```javascript
import React from 'react';

export const userContext = React.createContext({user: {}});
```

That component needs to be passed to the other components in our app, that happens in the `App.js` component. This is the same component talked about in the [routes chapter](#appjs), but I removed the routes to save us come duplicate code. In this component we wrap all our pages using the `userContext.Provider` component. Ofcourse the name might be different if your context component also has a different name. 

You can see that we pass in a variable to the `value` property. This variable should contain the value that should be able to be accessed throughout the app, in this case, our user.

```javascript
return (
    <div className="App">
      <userContext.Provider value={value}>
        <Navbar/>
        // routes
      </userContext.Provider>
    </div>
);
```
The value variable is built up like this. It is an object containing the user-state and two methods. The state contains the user itself, and the two methods log the user in and out. I did this so we can call these methods in other pages without having to spread them around the app.

```javascript
const [stateUser, setStateUser] = useState(null);
let user;

const value = {
    user: stateUser,
    userLogin: LoginUser,
    userLogout: LogoutUser,
};

function LoginUser(userObj){
    console.log('Logging user in');
    console.log(userObj);
    setStateUser(userObj);
}

function LogoutUser(){
    console.log('Logging user out');
    service.deleteUserSession();
    setStateUser(null);
    navigate("/login");
}
```

This data can be used in other pages by accessing the context. In order to do that, one needs to use the `useContext` hook provided by React.

```javascript
const context = useContext(userContext);
```

## Pages

In the `src/Pages/` directory I placed all my page components. These components represent a webpage and will contain multiple smaller components. With this structure you don't put everything into one component but rather split it up over multiple components, making everything easy to read and find. The user sees no difference, but the developer has a better time developing the application.


## Components

In the `src/Components` directory I put all the individual components which may be used in the page components. Another advantage of seperating these components to seperate files is that the developer may re-use these, if needed. That prevents the developer from having to copy + paste the code in another file, preventing code duplications.

## Services

Services are files which contain the logic of the application. In this application I keep track of users using `SessionStorage`. This allows me to keep track of active sessions when a user is logged in. That session can be used to fill the `userContext` which is used in the app.

There are three main methods that are used in this service.


### setUserSession

This method creates a user session in the webbrowser used. From this point on the the user is logged in. When the webbrowser tab is closed however, the session is lost and user will need to login again.

### getUserSession

This method will return the user session in the browser. If the user is not logged in, thus there being no session alive, the method will return `null`. If a user *is* logged in, a user object will be returned which can be used in the application to access some general data of the user.

### deleteUserSession

This method deletes the session (if there is one), which will log the user out of the application.

```javascript
export default class UserService extends React.Component {
    constructor(props){
        super(props);
    }

    setUserSession(user){
        if(user != null){
            sessionStorage.setItem('sessionUser', user);
        }
    }
    
    getUserSession(){
        return sessionStorage.getItem('sessionUser');
    }

    deleteUserSession(){
        sessionStorage.removeItem('sessionUser');
    }
}
```


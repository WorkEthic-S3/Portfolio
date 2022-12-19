# Outsourcing Individual Project Feature

To wrap up this semester our teacher has asked us to outsource one of our to-be-completed features to another student. Only a really small feature, which shouldn't take even two days to complete. The point is not to do some extra webdevelopment, but to see whether your project is correctly setup in a way that other developers can work in it without any issue. Much of the emphasis this semester was lookinng at your project setup, so that everything is as transparent and clear as possible, which is going to help you in case you work on a project with multiple people, or a whole team. Project in this context meaning application, repositories, documentation and everything else that may be used.

## Project I worked on

I worked on the project of a fellow student called Jordy. We had worked together a bit during the semester, and so figured it would be a good choice to be working on each other's projects.

His project is a concept for a company called Whirlwind FX and a product called [SignalRGB](https://www.signalrgb.com/). SignalRGB is a program for desktop which can be used to control the RGB of your peripherals, mainly keyboard. Within the program you can upload effects that draw images, and SignalRGB will synchronize your keyboard with that effect, allowing your keyboard to play that same effect.

His application is a platform where users of the program can upload their own effects. Now there's no way to, so this project hopes to solve that problem.

![Alt Text](../Videos/signalrgb-example.gif)

## Feature I worked on

The project has some basic functionality in place. One can login using their Google account to access the application. After logging in you can navigate to a page where you can upload an effect saved on your desktop. This effect will then be saved in a database. Also you can view all existing effects. The application retrieves all effects, regardless of who uploaded them or when they were uploaded.

One feature that wasn't present however, was the feature to view one's own effects alone. Without this the user can only navigate to the homepage where all effects will be rendered. After the feature is done a user will be able to navigate to a page using a button which will only render the user's effects.

## Development

The project consists of two applications, a frontend application created in React and a backend application created in Spring Boot. The React application is responsible for the UI, rendering all the screens and the info the user needs to see. The Spring Boot application is responsible for the backend logic and retrieving or writing data from/to the database.

### React

#### useEffect (MyEffectsPage)
I started off by creating a new page called `MyEffectPage.js` which is the main component representing the page. To easily test this code I wrote the call that retrieves the data in the new page, which takes the user as props.

The `useEffect` runs once per render of the component. It calls the `getEffectsByUser` method which is located in the `EffectService`.

```javascript
useEffect(() => {
    if(props.stateUser != null){
        setMyEffects(effectService.getEffectsByUser(props.stateUser.sub));
    }

}, [])
```

#### EffectService
`getEffectsByUser` is an async method in the `EffectService` class that calls an endpoint from the backend project that lives under `http://localhost:8080/api/effects/{id}`. The id of the user is place in the `id` placeholder in the URL which the backend will receive and use to determine which user's effects to look for.

```javascript
async getEffectsByUser(id){
    return await axios.get(ACCOUNT_BASE_REST_API_URL + "/user/" + id).catch((error) => {
    });
}
```

#### MyEffectsPage
The code below is the page component which is will contain all childcomponents that will together become the full page. In this component I reuse the `EffectTableComponent` that already exists and takes the effects as props. The component takes the effects and transforms them so that they can be played in the webbrowser.

```javascript
return (
    <div data-testid="myEffectsPage-1">
        <div>
            <h1 style={{ textAlign: "center", marginTop: "20px", color: "white" }}>MY EFFECTS</h1>
        </div>
        <EffectTableComponent effects={stateMyEffects}/>
    </div>
)
```

### Spring Boot

#### EffectController
To begin I created a new controller method which will handle the calls reponsible for effects by user. The `GetMapping` annotation shows how the URL should end for this endpoint to recognize the call. The `id` placeholder should contain a userid, which Spring Boot takes as a `PathVariable` which it can use in it's calls.

The controllermethod then calls a method from a `EffectService`, to which the controllermethod passes the id as an argument. It takes the data and returns a response which the React application will receive. 

```java
@GetMapping("/user/{id}")
public ResponseEntity<?> getEffectsByUser(@PathVariable String id){
    List<SignalEffect> effects = effectService.getEffectsByUser(id);
    return ResponseEntity.ok().body(effects);
}
```

#### EffectService

The `EffectService` contains all the logic and I added a method which is going to make a call to a repository which will filter the data by userid. 

```java
public List<SignalEffect> getEffectsByUser(String id) {
    return effectRepository.findBySubjectId(id);
}
```

#### EffectRepository

The repository accesses the database and retrieves the data needed. I've added a method which will filter the data by `SubjectID`.

```java
List<SignalEffect> findBySubjectId(String id);
```
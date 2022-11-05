# System Design - Parking Garage App

For the company Mediaan we were given two projects to choose from. They gave short presentations about both and told us in short what kind of applications they both were. One of them was a restaurant app, the other was a parking garage app. After a short talk with the team we decided to just vote, and whichever app got the most votes was the project we were going to on. Parking garage won the vote.

## Frontend designs

There are some things that need to be designed and thought about before an app can be developed. One of the most important things (, because it is what's immediately seen) is the frontend. You can have all the logic in the world, but if there is no design to back it up, it looks like you have very little working.

We made some frontend designs for some of the screens we were going to need. We sent them off to the POs and implemented their feedback.

<img src="../Images/reservations-design.png" alt="reservations" width="200" height="450" />
<img src="../Images/cars-design.png" alt="reservations" width="200" height="450" />

</br>

## ERD Diagram

Another important part of the application is the database. All of the data is going to be stored there so it needs to be designed well so development can go smoothly. We started with a diagram, and constantly made small changes based on new findings to make the database work better.

We have a bunch of tables working together that are connected with relations. We had to think about what data needs to be saved, and what data can be calculated inside of the applcation. This database model has also been placed in migration files so that teammembers can generate the database below by typing one command into their IDE.

<img src="../Images/ClassDiagram_Proftaak.png" alt="reservations" width="450" height="400" />

## Architecture Design


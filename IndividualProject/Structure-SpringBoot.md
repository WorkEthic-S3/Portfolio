# Structure Spring Boot project

While I was working on my projects, a structure came to life to help me during the development process. It helps the developer find code and expand the codebase without any issues. When stuff does goes wrong portions of the code can be found easily, because of how everything is put into components. I would like to explain a bit on how my project is structured and how everything works.

## Table of contents
1. [Controllers](#controllers)
2. [Services](#services)
3. [Repositories](#repositories)
4. [Models](#models)

## Controllers

My controllers receive the incoming requests and execute a piece of code responsible for handling that request. Each controller method returns a proper response with the data inside it. On top of the file using CORS we decide which origins are allowed to send requests to our controller.

Using the `CrossOrigin` annotation we can specify which origin is allowed to send requests. If another origin tries to send requests it will be blocked and the client machine won't see the result but only an error message in their console.

Using the `RequestMapping` annotation on top of our controller we can specify how the controller methods can be called. In the example below the annotation notes that in order to make a call to this controller, the url needs to contain `/tasks`.

```java
@RestController
@RequestMapping("/tasks")
@CrossOrigin(origins = "http://localhost:3000")
public class TaskController {
```

## Services

Services are classes that contain the main logic of the application. These are seperated in case they need to be re-used, but also for easier testing. In this structure one can test each component seperately to check whether the component returns the expected result. In my service I have multiple methods which are responsible for generic operations like `create`, `getAll` and `getById`.

```java
@Service
public class TaskService implements ITaskService {
    @Autowired
    private TaskRepository taskRepository;

    public Task createTask(Task task) {
        return taskRepository.save(task);
    }

    public List<Task> getAllTasks() {
        return taskRepository.findAll();
    }

    public Optional<Task> getTaskById(long id) {
        return taskRepository.findById(id);
    }
}
```

## Repositories

Repositories are responsible for communication with the database. They execute queries to read data from, or write data to, the database. These methods get called from service classes whenever they are needed. I have one interface which extends `JpaRepository`, which provides me with all the generic methods I need. If I need a custom method not provided by the repository, I can mention it manually in below interface and creat it myself.

```java
@Repository
public interface TaskRepository extends JpaRepository<Task, Long> {

}
```

## Models

Models are classes that describe what entities in the application look like. These properties show also be the same as the database columns. Using these models one can read data from a database and write to it.

```java
@Getter
@Setter
public class TaskDTO {
    public long id;
    public String title;
    public String body;
    public String userId;
    public String userName;
    public String userPicture;
    public LocalDateTime created_at;
}
```
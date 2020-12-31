# Spring Boot Master Class

## N Tier Architecture

`Client` (Request) --> `RestFul API Layer` (GET, POST, PUT, DELETE) --> `Service Layer` (Business Logic) --> `DAO Layer` (Interact with Databases) --> `Your Favorite Database` (Postgres, MySQL, MongoDB, FakeDB) ---> `Data` (Back to the Client)


## Dependency Injection

`Spring`, `Guice`, `Dagger` : They take care of managing all objects, and allow us to use object wherever necessary

Use annotation:

Example:

```
@Inject
public EmailService(ContactListService contactListService) {
    this.contactListService = contactListService;
}
```

Here we are not instantiating a `new contactListService` by using `@Inject`


Then we tell Spring to instantiate the object by going to the ContactListService service:

```
@Service
public class ContactListService {
    public ContactListService(){}
}
```

Because Spring is clever enough this Object is created by default as Singleton, if you inject it into multiple classes, it will re-use the same instance

These days apps are usually horizontally scaling, we do not deal with a lot of multithreading in today's world. Apps are scaled by spinning up multiple instances/containers.


`@RestController` <-- using this annotation makes your methods REST API, add `@RequestMapping` for defining HTTP Method
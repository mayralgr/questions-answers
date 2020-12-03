# How does spring @Autowired annotation works in a REST API? 

The `@Autowired` annotation marks a constructor, setter method, or config method as to be autowired or linked by spring’s dependency injection. 

In a `REST API`, the `@Autowired` annotation allows that once the classes annotated with `@Controller ,@Service ,@repository o @RestController, etc.,` are created in runtime, it makes the links between them. 

For example:  

If we have 

A @Repositoty called ShopRepository 

```Java
@Repository
public class ShopRepository {
  public List<Item> searchAll() {
      ...
  }

  ...
  
}
```
 
If we want to use it in a service we use the @Autowired  to do this link 

```Java
@RestController  

public class ShopRestService {  

    @Autowired  
    ShopRepository repository; 
    ...

} 
```

With this, it is avoided to use the 
```Java
    repository = new ShopRepository()
```
##### as spring finds the dependency, inject it and make an instance. 

### How ?

* Spring does a scan of the classes in the context (the container of the application), helped by the annotations, to create beans (objects that are the backbone of the application) of them
* Spring does a second scan to inject the dependency, it searches for the bean (by its name) and if it finds it, it injects the dependency by calling the constructor. If does not exist, it throws an exception

# Read: 13 - Related Resources and Integration Testing

## [Related data in Spring](https://www.baeldung.com/spring-data-rest-relationships)

### 1. One-to-One Relationship

**1.1. The Data Model**

- One-to-one relationship is using  -> the `@OneToOne` annotation.
- The `@RestResource` annotation is optional and can be used to customize the endpoint.
- We must be careful to have different names for each association resource.

```
@OneToOne
@JoinColumn(name = "secondary_address_id")
@RestResource(path = "libraryAddress", rel="address")
private Address secondaryAddress;
```

if we add this code to class and we have in that class other resource called Adress,
we'll face conflict, so that we can solve it by by specifying a different value for the rel attribute or by omitting the RestResource annotation so that the resource name defaults to secondaryAddress.
  
**1.2. The Repositories**
'In order to expose these entities as resources, let's create two repository interfaces for each of them, by extending the CrudRepository interface:'
`public interface LibraryRepository extends CrudRepository<Library, Long> {}`
`public interface AddressRepository extends CrudRepository<Address, Long> {}`
Note, we'll assume that we will have two classes (Library and address), and each one is Entity that includes @Id, @Column, and @OneToOne.

**1.3. Creating the Resources**

- To add a Library instance:

```
curl -i -X POST -H "Content-Type:application/json" 
  -d '{"name":"My Library"}' http://localhost:8080/libraries
```

For curl on Windows,  escape the double-quote character inside `'{"name":"My Library"}'`.

- and The API returns the JSON object.
as in

```
 "name" : "My Library",
  "_links" : {
    "self" : {
      "href" : "http://localhost:8080/libraries/1"
    } , etc.......
```

- Before we create an association, sending a GET request to this endpoint will return an empty object.
so, if we want to add an association, we must first create an Address instance also.
and we'll have the result of the POST request inside a JSON object.

**1.4. Creating the Associations**

- We can establish the relationship by using one of the association resources.
This is done using the HTTP method PUT.

```
curl -i -X PUT -d "http://localhost:8080/addresses/1" 
  -H "Content-Type:text/uri-list" http://localhost:8080/libraries/1/libraryAddress
```

- 'If successful, this returns status 204. To verify, let's check the library association resource of the address:'
`curl -i -X GET http://localhost:8080/addresses/1/library`
we'll return the Library JSON object.

- To remove an association -> call the endpoint with DELETE.

---

### 2. One-to-Many Relationship

- Is defined using the `@OneToMany` and `@ManyToOne` annotations.
- Also we can have the optional `@RestResource` annotation.

**2.1. The Data Model**

```
@Entity
public class Book {

    @Id
    @GeneratedValue
    private long id;
    
    @Column(nullable=false)
    private String title;
    
    @ManyToOne
    @JoinColumn(name="library_id")
    private Library library;
    
    // standard constructor, getter, setter
}
```

```
public class Library {
 
    //...
 
    @OneToMany(mappedBy = "library")
    private List<Book> books;
 
    //...
 
}
```

---

### 3.Many-to-Many Relationship

- Is defined using the `@ManyToMany` annotations.

```
public class Author {

    @Id
    @GeneratedValue
    private long id;

    @Column(nullable = false)
    private String name;

    @ManyToMany(cascade = CascadeType.ALL)
    @JoinTable(name = "book_author", 
      joinColumns = @JoinColumn(name = "book_id", referencedColumnName = "id"), 
      inverseJoinColumns = @JoinColumn(name = "author_id", 
      referencedColumnName = "id"))
    private List<Book> books;

    //standard constructors, getters, setters
}
```

```
public class Book {
 
    //...
 
    @ManyToMany(mappedBy = "books")
    private List<Author> authors;
 
    //...
}
```

## [Baeldung: Spring Integration Testing](https://www.baeldung.com/integration-testing-in-spring)

- Independencies :we'll need the latest junit-jupiter-engine, junit-jupiter-api, and Spring test dependencies.

### Spring MVC Test Configuration

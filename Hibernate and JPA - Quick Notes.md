
# Hibernate and JPA - Quick Notes

## What Is Java Persistence API?
The Java Persistence API **provides a specification** for persisting, reading, and managing data from your Java object to relational tables in the database.

As JPA is just a specification, it means that there is no implementation of it.

## What is the object-relational mapping?
object-relational mapping is a **mechanism** which is **used** to develop and **maintain a relationship between an object and the relational database. It converts attributes of programming code into columns of the table.

## What Is Hibernate Framework?
**Hibernate is a JPA implementation.

**Hibernate is an object-relational mapping solution for Java environments. Object-relational mapping or **ORM** is the **programming technique to map application domain model objects to the relational database tables**. Hibernate is a Java-based ORM tool that provides a framework for mapping application domain objects to the relational database tables and vice versa.

## What is a Entity in Hibernate?
### What are the properties of an entity?


## **What is the role of Entity Manager in JPA?**
An entity manager is responsible for the following operations.

* The entity manager implements the API and encapsulates all of them within a single interface.
* The entity manager is used to read, delete and write an entity.
* An object referenced by an entity is managed by entity manager.

## What are the different directions of entity mapping?
The direction of a mapping can be either **unidirectional** or **bidirectional**. In unidirectional mapping, only one entity can be mapped to another entity, whereas in bidirectional mapping each entity can be mapped or referred to another entity.

## What are the different types of entity mapping?
 -   **One-to-one mapping:**  The one-to-one mapping represents a single-valued association where an instance of one entity is associated with an instance of another entity. In this type of association, one instance of source entity can be mapped with at most one instance of the target entity.
-   **One-To-Many mapping:**  The One-To-Many mapping comes into the category of collection-valued association where an entity is associated with a collection of other entities. In this type of association, the instance of one entity can be mapped with any number of instances of another entity.
-   **Many-to-one mapping**  The Many-To-One mapping represents a single-valued association where a collection of entities can be associated with the similar entity. In the relational database, more than one row of an entity can refer to the same row of another entity.
-   **Many-to-many mapping**  The Many-To-Many mapping represents a collection-valued association where any number of entities can be associated with a collection of other entities. In the relational database, more than one row of one entity can refer to more than one row of another entity.

## What are the different types of identifier generation?
Following are the types of id generation strategy required to specify with @GeneratedValue annotation: -

* Automatic Id generation - In this case, the application doesn't care about the kind of id generation and hand over this task to the provider. If any value is not specified explicitly, the generation type defaults to auto.
* Id generation using a table - The identifiers can also be generated using a database table.
* Id generation using a database sequence - Databases support an internal mechanism for id generation called sequences. To customize the database sequence name, we can use the JPA @SequenceGenerator annotation.
* Id generation using a database identity - In this approach, whenever a row is inserted into the table, a unique identifier is assigned to the identity column that can be used to generate the identifiers for the objects.

## What is OrphanRemoval - Hibernate
[hibernate-framework-orphanremoval-com-hibernate](https://www.devmedia.com.br/hibernate-framework-orphanremoval-com-hibernate/30854)

## Hibernate Best Practices
* By default hibernate set the field values directly, without using setters. So if you want hibernate to use setters, then make sure proper access is defined as @Access(value=AccessType.PROPERTY).
* Always check the primary key field access, if it’s generated at the database layer then you should not have a setter for this.
* Avoid Many-to-Many relationships, it can be easily implemented using bidirectional One-to-Many and Many-to-One relationships.
* Do not treat exceptions as recoverable, roll back the Transaction and close the Session. If you do not do this, Hibernate cannot guarantee that in-memory state accurately represents the persistent state.

## @Lob
`@javax.persistence.Lob` signifies that the annotated field should be represented as BLOB (binary data) in the DataBase.

Common use of `@Lob` is to annotate a `HashMap` field inside an Entity to store some of the object properties which are not mapped into DB columns. That way all the unmapped values can be stored in the DB in one column in their binarry representation. Of course the price that is paid is that, as they are stored in binary format, they are not searchable using the JPQL/SQL.

```java
@Lob
@Basic(fetch = FetchType.LAZY)
@Column(name = "DATA", columnDefinition = "BLOB", nullable = false)
private byte[] data;
```

## What is The JPQL?
Java Persistence query language is a part of JPA specification that defines searches against persistence entities.

## Type Of Cascading Hibernate

## Reference 
[https://www.journaldev.com/3633/hibernate-interview-questions-and-answers#entity-final-class](https://www.journaldev.com/3633/hibernate-interview-questions-and-answers#entity-final-class)
[https://www.edureka.co/blog/interview-questions/hibernate-interview-questions/#Q1._What_is_Hibernate?](https://www.edureka.co/blog/interview-questions/hibernate-interview-questions/#Q1._What_is_Hibernate?)
[https://www.javatpoint.com/jpa-interview-questions](https://www.javatpoint.com/jpa-interview-questions)


# Hibernate and JPA - Quick Notes

## What Is Java Persistence API?
The Java Persistence API **provides a specification** for persisting, reading, and managing data from your Java object to relational tables in the database.

As JPA is just a specification, it means that there is no implementation of it.

## What Is Hibernate Framework?
**Hibernate is a JPA implementation.

**Hibernate is an object-relational mapping solution for Java environments. Object-relational mapping or **ORM** is the **programming technique to map application domain model objects to the relational database tables**. Hibernate is a Java-based ORM tool that provides a framework for mapping application domain objects to the relational database tables and vice versa.



## @Lob
`@javax.persistence.Lob` signifies that the annotated field should be represented as BLOB (binary data) in the DataBase.

Common use of `@Lob` is to annotate a `HashMap` field inside an Entity to store some of the object properties which are not mapped into DB columns. That way all the unmapped values can be stored in the DB in one column in their binarry representation. Of course the price that is paid is that, as they are stored in binary format, they are not searchable using the JPQL/SQL.

```java
@Lob
@Basic(fetch = FetchType.LAZY)
@Column(name = "DATA", columnDefinition = "BLOB", nullable = false)
private byte[] data;
```

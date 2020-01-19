
# Hibernate and JPA - Quick Notes



## @Lob
`@javax.persistence.Lob` signifies that the annotated field should be represented as BLOB (binary data) in the DataBase.

Common use of `@Lob` is to annotate a `HashMap` field inside an Entity to store some of the object properties which are not mapped into DB columns. That way all the unmapped values can be stored in the DB in one column in their binarry representation. Of course the price that is paid is that, as they are stored in binary format, they are not searchable using the JPQL/SQL.

```java
@Lob
@Basic(fetch = FetchType.LAZY)
@Column(name = "DATA", columnDefinition = "BLOB", nullable = false)
private byte[] data;
```

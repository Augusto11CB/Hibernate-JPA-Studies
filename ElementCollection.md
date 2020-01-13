
# ElementCollection

### Annotations
* @ElementCollection
* @CollectionTable
* @Embeddable
* @AttributeOverrides
	* @AttributeOverride

Mapping a collection of basic as well as embeddable types using JPA’s **@ElementCollection** and **@CollectionTable** annotations

Use ElementCollection to deal with a collection of non-entities, in other words, a collection of simple types (Strings, etc.) or a collection of embeddable elements (class annotated with **@Embeddable**).

It also means that the elements are completely owned by the containing entities: they're modified when the entity is modified, deleted when the entity is deleted, etc. They can't have their own lifecycle.

## Basic Information
**@ElementCollection:**
* the relation is managed (only) by the entity in which the relation is defined
* table contains id reference to the owning entity plus basic or embedded attributes

**@OneToMany / @ManyToMany:**
* can also be managed by the other entity
* join table or column(s) typically contains id references only

## Example of an ElementCollection relationship annotations

```java
@Entity
public class Employee {
  @Id
  @Column(name="EMP_ID")
  private long id;
  ...
  @ElementCollection
  @CollectionTable(
        name="PHONE",
        joinColumns=@JoinColumn(name="OWNER_ID")
  )
  private List<Phone> phones;
  ...
} 
```

```java
@Embeddable
public class Phone {
  private String type;
  private String areaCode;
  @Column(name="P_NUMBER")
  private String number;
  ...
}
```



## Reference 
[ElementCollection Example + Spring Boot](https://www.callicoder.com/hibernate-spring-boot-jpa-element-collection-demo/)

# Enum Mappings - Kotlin



1. Definition of Class EnumType
2. Enum object 
3. Entity Class Using enum


```kotlin
//Enum object
enum class StateEnum{  
    SP, RJ, ES, MG
}
```

```kotlin
//Entity Class Using enum
class StateEnumType: EnumType<StateEnum>() {  
    @Throws(HibernateException::class, SQLException::class)  
    override fun nullSafeSet(  
        st: PreparedStatement,  
  value: Any?,  
  index: Int,  
  session: SharedSessionContractImplementor  
    ) {  
        if (value == null) {  
            st.setNull(index, Types.OTHER)  
        } else {  
            st.setObject(  
                index,  
				value.toString(),  
				Types.OTHE
			 )  
        }  
    }  
}
```

```kotlin
//Entity
@Entity  
@Table(name = "tb_country")  
@TypeDefs(  
    value =  
  [TypeDef(name = "state_enum_type", typeClass = StateEnumType::class)]
)
class Country(
	@Enumerated(EnumType.STRING)  
	@Column(name = "tp_pessoa_pagador")  
	@Type(type = "state_enum_type")  
	val capital: StateEnum?,
)
```

```kotlin
```

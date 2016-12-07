# PropertiesAndFields


### Val vs Var

```
Val er private final og kommer med en default getter metode.

Var er private og kommer med en default getter og setter metode.

Fuld syntax for deklarering af var eller val:
var <propertyName>: <PropertyType> [= <property_initializer>] 
hvor type ikke er nødvendig hvis man kan udlede det fra instantieringen
```

### Calling Methods in Other Classes

```
Classes i kotlin kan kaldes ved at skrive classname();
Det som classname(); gør er at den instantierer en ny instans af classen.


```
```java
F. eks i java
Class1 class = new Class1();
```


```kotlin
I Kotlin
var class = class1();
```

```
Then you get access to all public functions by using
class.myfoo();
```

## Example of Useage

### Class1 (Class)


```kotlin
val isEmpty: Boolean = true;
var aaa: String = "defaultValue"
```



### Class2 (Class)

```kotlin
var NewInstanceOfClass1 = Class1();
NewInstanceOfClass1.aaa = "20";
var a = NewInstanceOfIClass1.aaa;
Log.d("her er a -- ", a); // a bliver 20.
``` 


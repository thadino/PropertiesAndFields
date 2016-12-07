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

## Example of Usage

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


## Example of Usage with custom accessors

```
Vi kan skrive custom accessors ligesom normale funktioner inde i property deklarationen.

Klasser i kotlin kan ikke have felter. Dog nogle gange kan det være 
en nødvendighed at have et backing field når man bruger custom accessors. 
For disse formål, tilbyder kotlin en automatisk backing field som kan tilgås via field indentifier.
```

### Class1 (Class)


```kotlin
    var aaa = "hej"
        get() = field + " med dig"
```



### Class2 (Class)

```kotlin
var NewInstanceOfClass1 = Class1();
NewInstanceOfClass1.aaa = "20";
var a = NewInstanceOfIClass1.aaa;
Log.d("her er a -- ", a); // a bliver 20 med dig.
``` 


## Backing Properties

```
Som eksemplet viser nedenfor kan man ved hjælp af backing properties få adgang til en anden property
i instantieringen af en property.
```

### Eksempel på Backing Properties
```kotlin
fun Context.toast(message: String)
{
  Toast.makeText(this, message, Toast.LENGTH_LONG).show()
}

var lars: String = "hej "

var cph: String = ""
    get() {
        if (lars == "lars"){
            return lars.toUpperCase()
        }
        if (lars == "linuxmanden"){
            lars = "kasper"
            return lars
        }
        return lars
    }
    
   class Class : AppCompatActivity()  {
        lars = "koen";
        toast(cph); // returnere koen
        lars = "lars";
        toast(cph); // returnere LARS (lars i uppercase)
        lars = "linuxmanden";
        toast(cph); // returnere kasper
    }
```


## Compile-Time Constants
```
Properties hvilke værdier ikke er kendt når compileren kører kan blive markeret som 
compile time constants ved at bruge const.

For at bruge const er der visse regler der skal følges:
Den skal være Top-level eller medlem af et objekt.
Den skal være Initialiseret med value af typen string eller en primitiv type.
Du må ikke lave custom getter.


I kotlin er constants globale og kan kaldes i alle dine klasser og værdien kan ikke ændres.

```

### Eksempel på Constrants

```kotlin
Class1
const val myconst: String = "dubi "
```

```kotlin
Class2
Log.d("", myconst); // returnere dubi
```


## Late-Initialized Properties

```
Properties som ikke må være null  er nødt til at blive deklareret i constructoren. 
Dog er dette ikke altid muligt. F. eks ved opsætningen af en unit test. 
Her kan man ikke putte en not-null property ind i constructor.
For at håndtere dette kan man bruge lateinit.


```

### Eksempel på lateinit:
```kotlin
public class MyTest {
    lateinit var subject: TestSubject

    @SetUp fun setup() {
        subject = TestSubject()
    }

    @Test fun test() {
        subject.method()  // dereference directly
    }
}
```

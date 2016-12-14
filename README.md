# PropertiesAndFields


### Val vs Var

```
Val kommer med en default getter metode.

Var kommer med en default getter og setter metode.

Fuld syntax for deklarering af var eller val:
var <propertyName>: <PropertyType> [= <property_initializer>] 
hvor type ikke er nødvendig hvis man kan udlede det fra instantieringen
```

### Calling Methods in Other Classes


Classes i kotlin kan kaldes ved at skrive `Classname()`
Det som `Classname()` gør er at den instantierer en ny instans af klassen.




F. eks i java
`Class1 class = new Class1()`


I Kotlin
`var class = class1()`



Then you get access to all public functions by using
`class.myfoo()`

## Example of Usage

### Class1 (Class)


```kotlin
class Class1{
    val isEmpty: Boolean = true;
    var aaa: String = "defaultValue"
}
```



### Class2 (Class)

```kotlin
class Class2{
    var NewInstanceOfClass1 = Class1();
    NewInstanceOfClass1.aaa = "20";
    var a = NewInstanceOfIClass1.aaa;
    Log.d("her er a -- ", a); // a bliver 20.
}
``` 


## Example of Usage with custom accessors


Vi kan skrive custom accessors ligesom normale funktioner inde i property deklarationen.

Klasser i kotlin kan ikke have felter. Dog nogle gange kan det være 
en nødvendighed at have et backing field når man bruger custom accessors. 
For disse formål, tilbyder kotlin en automatisk backing field som kan tilgås via `field` indentifier.


### Class1 (Class)

```kotlin
class Class1{
    var aaa = "hej"
        get() = field + " med dig"
}
```



### Useage

```kotlin
var NewInstanceOfClass1 = Class1();
NewInstanceOfClass1.aaa = "20";
var a = NewInstanceOfIClass1.aaa;
Log.d("her er a -- ", a); // a bliver 20 med dig.
``` 


## Backing Properties


Som eksemplet viser nedenfor kan man ved hjælp af backing properties få adgang til en anden property
i instantieringen af en property.


### Eksempel på Backing Properties
```kotlin
class Class3{

private var lars: String = "hej "

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
    set(value){
    lars = value;
    }
}

   fun main()  {
   val c3 = Class3()
        c3.cph = "koen";
        println(cph); // returnerer koen
        c3.cph = "lars";
        println(cph); // returnerer LARS (lars i uppercase)
        c3.cph = "linuxmanden";
        println(cph); // returnerer kasper
    }

```


## Compile-Time Constants

Properties hvilke værdier er kendt når compileren kører kan blive markeret som 
compile time constants ved at bruge `const`.

For at bruge const er der visse regler der skal følges:
Den skal være Top-level eller medlem af et objekt.
Den skal være Initialiseret med value af typen `String` eller en primitiv type.
Du må ikke lave custom getter.


I kotlin er constants globale og kan kaldes i alle dine klasser og værdien kan ikke ændres.
Dette kan lade sig gøre da variablen er skrevet i compile time 
(Dvs at const variablen er smidt ind i B i compile time og ikke run time)



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


Properties som ikke må være null  er nødt til at blive deklareret i constructoren. 
Dog er dette ikke altid muligt. F. eks ved opsætningen af en unit test. 
Her kan man ikke putte en not-null property ind i constructor.
For at håndtere dette kan man bruge lateinit.


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

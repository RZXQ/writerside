# Objects and their properties

A typical [object-oriented](https://hyperskill.org/learn/step/4727) program consists of a set of interacting **objects**. Each object has its own state separated from others. Each object is an instance of a particular class (type) that defines common properties and possible behavior for its objects.

All classes from the standard library (**`String`**, **`Date`**) and classes defined by programmers are **reference** **types** which means that [variables](https://hyperskill.org/learn/step/4727) of these types store addresses where the actual objects are located. In this regard, the comparison and assignment operations work with objects differently than with primitive types.

## Creating objects

The keyword **new** creates an object of a particular class. Here we create a standard string and assign it to the variable **`str`**:

```java
String str = new String("hello");
```

The variable **`str`** stores a reference to the object **"hello"** located somewhere in the heap memory.

In the same way, we can create an object of any class we know.

Here is a class that describes a patient in a hospital information system:

```java
class Patient {
    String name;
    int age;
}
```

Here is an instance of this class:

```java
Patient patient = new Patient();
```

Despite the fact that **`String`** is a standard class and **`Patient`** is our own class, both classes are regular [reference types](https://hyperskill.org/learn/step/4727). However, there is a big difference between those classes and we will discuss it below.

## Immutability of objects

There is an important concept in programming called **[immutability](https://hyperskill.org/learn/step/4727)**. Immutability means that an object always stores the same values. If we need to modify these values, we should create a new object. A common example is the standard **`String`** class. Strings are [immutable objects](https://hyperskill.org/learn/step/4727) so all string operations produce a new string. [Immutable types](https://hyperskill.org/learn/step/4727) allow you to write programs with fewer errors.

The class **`Patient`** is not immutable because it is possible to change any field of an object.

```java
Patient patient = new Patient();

patient.name = "Mary";
patient.name = "Alice";
```

In the following topics, we will look at the existing immutable classes as well as learn how to create new ones and when to use them.

## Sharing references

More than one variable can refer to the same object.

```java
Patient patient = new Patient();

patient.name = "Mary";
patient.age = 24;

System.out.println(patient.name + " " + patient.age); // Mary 24

Patient p = patient;

System.out.println(p.name + " " + p.age); // Mary 24
```

It is important to understand that two variables refer to the same data in memory rather than two independent copies. Since our class is mutable, we can modify the object using both references.

```java
patient.age = 25;
System.out.println(p.age); // 25
```

## Nullability

As for any reference type, a variable of a class type can be **null** which means it is not initialized yet.

```java
Patient patient = null;
```

This is a common feature in Java available for classes since they are reference types.



> Attempting to access a reference that points to **null** will result in an **exception**. It indicates that you're trying to perform an operation on a non-existent object. We'll deal with this topic in the following topics.

## Conclusion

By now, not only have we already worked with some classes from the standard library but also learned how Java allows us to create our own classes. In this topic, we've discussed that the nature of custom classes' objects and standard library ones are based on the same principles.

Keep in mind, that classes defined by programmers are **reference types**. When objects are created by the **new** operator it returns a reference in memory where the created objects are located. With this reference, we can get access to fields and change them. Several variables can refer to the same object through a reference. It is also possible to create two independent objects with the same field's content. It's important to understand that references to such objects are different. However, not all objects allow changing their state after creation. Such a feature is called **immutability**.
# Static members

All objects in a class share the same fields and methods, even though the values of [object fields](https://hyperskill.org/learn/step/3534) usually differ. A class can also possess fields and methods that are common to all objects. We refer to these as **[static members](https://hyperskill.org/learn/step/3534),** [declared](https://hyperskill.org/learn/step/3534) with the `static` keyword.

## Class variables

A **[class variable](https://hyperskill.org/learn/step/3534) ([static field](https://hyperskill.org/learn/step/3534))** is a field declared with the `static` keyword. It can hold any primitive or [reference type](https://hyperskill.org/learn/step/3534), just like a regular [instance field](https://hyperskill.org/learn/step/3534). A static field has the same value for all instances of the class. it belongs to the class, rather than to an instance of the class.

If you want all instances of a class to share a common value, like a [global variable](https://hyperskill.org/learn/step/3534), it's preferable to declare it as static. This approach can help save memory as all the created objects share a single copy of a static variable.

You can directly access static variables by the class name. To access a static field, you should write:

```java
ClassName.fieldName;
```

Now let's take a look at an example. Here is a class with two public static variables:

```java
class SomeClass {

    public static String staticStringField;

    public static int staticIntField;
}
```

We can set their values and retrieve them:

```java
SomeClass.staticIntField = 10;
SomeClass.staticStringField = "it's a static member";

System.out.println(SomeClass.staticIntField); // It prints "10"
System.out.println(SomeClass.staticStringField); // It prints "it's a static member"
```









> Typically, declaring **non-final** **public static fields** is not a good practice. In this case, we use them simply as an example.
> {style="note"}








You can also access the value of a static field through an instance of the class.

```java
SomeClass.staticIntField = 30;

SomeClass instance = new SomeClass();

System.out.println(instance.staticIntField); // It prints "30"
```

Now let's dive into a more complex example. This class has a static field named `lastCreated`. The field records the date of the last created instance.

```java
public class SomeClass {

    public static Date lastCreated;

    public SomeClass() {
        lastCreated = new Date();
    }
}
```

Every time a new object is created, the value of the static field changes in the class constructor.

The following code creates two instances and prints intermediate results:

```java
System.out.println(SomeClass.lastCreated);

SomeClass instance1 = new SomeClass();
System.out.println(SomeClass.lastCreated);

SomeClass instance2 = new SomeClass();
System.out.println(SomeClass.lastCreated); 
```

Here's what I got as a result:

```java
null
Sun Aug 20 17:49:24 YEKT 2017
Sun Aug 20 17:49:25 YEKT 2017
```

## Class constants

Static fields with the `final` keyword are **[class constants](https://hyperskill.org/learn/step/3534)**, which means they cannot be changed. According to the naming convention, constant fields should always be written in uppercase with an underscore (`_`) to separate parts of the name.

The standard class `Math` , for example, contains two static constants:

```java
public static final double E = 2.7182818284590452354;

public static final double PI = 3.14159265358979323846;
```

Constants are often public, but it's not a rule.

To see how they work, let's declare a class named `Physics` with two static constants:

```java
class Physics {

    /**
     * The speed of light in a vacuum (m/s)
     */
    public static final long SPEED_OF_LIGHT = 299_792_458;

    /**
     * Electron mass (kg)
     */
    public static final double ELECTRON_MASS = 9.1093837e-31;
}
```

To use the constants, let's write the following code:

```java
System.out.println(Physics.ELECTRON_MASS); // 9.1093837E-31
System.out.println(Physics.SPEED_OF_LIGHT); // 299792458
```

Since those fields are constants, we cannot change their values. If we try to do it, we'll get an error:

```java
Physics.ELECTRON_MASS = 10; // compile-time error
```

## Class methods

A class may have **[static methods](https://hyperskill.org/learn/step/3534)** as well as static fields. Such methods are also known as **[class methods](https://hyperskill.org/learn/step/3534)**. A static method can be accessed by the class name and doesn't require an object of the class.

Static methods can be called directly with the class name. To access a method, you should write

```java
ClassName.staticMethodName(args);
```

A static method may have arguments like a regular instance method or it may well have no arguments. But, unlike instance methods, static methods have several special features:

- a static method can access only static fields and cannot access non-static fields;
- a static method can invoke another static method, but it cannot invoke an [instance method](https://hyperskill.org/learn/step/3534);
- a static method cannot refer to `this` keyword because there is no instance in the static context.

Instance methods, however, can access static fields and methods.









> Static methods are often used as **[utility methods](https://hyperskill.org/learn/step/3534)**that are the same for the whole project. As an example, you can create a class with only static methods for performing typical math operations.









The Java class library provides a lot of static methods for different classes. Here are just a few of them:

- the `Math` class has a lot of static methods, such as `Math.min(a, b)`, `Math.abs(val)`, `Math.pow(x, y)` and so on;
- the `Arrays` class has a lot of static methods for processing arrays such as `toString(...)`;
- `Long.valueOf(...)`, `Integer.parseInt(...)`, `String.valueOf(...)` are static methods too.

Here is a class with one constructor, a static method and an instance method.

```java
public class SomeClass {
    
    public SomeClass() {
        invokeAnInstanceMethod(); // this is possible here
        invokeAStaticMethod();    // this is possible here too
    }
    
    public static void invokeAStaticMethod() { 
        // it's impossible to invoke invokeAnInstanceMethod() here
    }
    
    public void invokeAnInstanceMethod() { 
        invokeAStaticMethod();  // this is possible
    }
}
```

This example shows that you can invoke a static method from the instance context (constructors and instance methods), but you can't invoke an instance method from a static context.

The only way to call an instance method from a static one is to provide a reference to this instance as an argument. You can also create objects of other classes and call their methods in a similar way. Here's an example:

```java
public static void invokeAStaticMethod(SomeClass someClassInstance) {

    // calling instance method from static context by passing instance as an argument
    someClassInstance.invokeAnInstanceMethod(); 

    // calling instance and static methods of AnotherClass instance
    AnotherClass anotherClassInstance = new AnotherClass();
    anotherClassInstance.invokeAnotherClassInstanceMethod();
    anotherClassInstance.invokeAnotherClassStaticMethod();
}
```

An example of a static method is the `main` method. It should always be static.

## Conclusion

In this topic, we discussed static fields and methods and some situations where we can use them. It is important to remember that static members cannot access the values of object fields since there is no instance context (`this`). Nonetheless, they are a good option for providing a set of common constants (together with `final`) and utility methods for the whole project. We will consider other helpful ways of using static members in the next topics.
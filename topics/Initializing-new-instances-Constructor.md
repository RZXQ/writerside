# Initializing new instances. Constructor

**Constructors** are special methods that initialize a **new object** of the class. A constructor of a class is invoked when an instance is created using the keyword `new`.

A constructor is different from other methods in that:

- it has the same name as the class that contains it;
- it has no [return type](https://hyperskill.org/learn/step/3535) (not even `void`).

Constructors initialize **instances** (objects) of the class. They set values to the fields when the object is created. Also, constructors can take parameters for initializing fields by the given values.

## Using constructors

Here is a class named `Patient`. An object of the class has a name, an age, and a height. The class has a constructor with 3 parameters to initialize objects with specific values.

```java
class Patient {

    String name;
    int age;
    float height;

    public Patient(String name, int age, float height) {
        this.name = name;
        this.age = age;
        this.height = height;
    }
}
```

Let's go further and create some instances of the class using the constructor we've written:

```java
Patient patient1 = new Patient("Heinrich", 40, 182.0f);
Patient patient2 = new Patient("Mary", 33, 171.5f);
```

Now we have two patients, Heinrich and Mary, with the same fields, but the values of those fields are different.

## Keyword this

In the example above, `Patient` constructor takes three parameters:

```java
this.name = name;
this.age = age;
this.height = height;
```

To initialize the fields, the keyword `this` is used, which is a reference to the current object. Usually, the keyword `this` is used when an instance [variable](https://hyperskill.org/learn/step/3535) and a constructor or a method variable share the same name. This keyword helps to disambiguate these situations.

If you write something like `name = name`, it means that you're assigning the `name` variable to itself, which, of course, doesn't make any sense. Frankly speaking, you may distinguish two objects simply by assigning another name to the variable, like `name = newName`. It is not prohibited, but it is considered bad practice since these variables point to the same thing. These are the reasons why the keyword `this`is extremely useful with constructors, fields, and methods. The absence of extra variables makes the code look clearer and less overloaded.

## Default and no-argument constructor

The compiler automatically provides **a default no-argument constructor** for any class without constructors.

```java
class Patient {

    String name;
    int age;
    float height;
}
```

We can create an instance of the class `Patient` using the no-argument [default constructor](https://hyperskill.org/learn/step/3535):

```java
Patient patient = new Patient();
```

In this case, all fields will be filled with the default values of their types.

If you define a specific constructor, the default constructor will not be created.

We can also define a constructor without any arguments, but use it to set default values for fields of a class. For example, we can initialize `name` with `"Unknown"`:

```java
class Patient {

    String name;
    int age;
    float height;

    public Patient() {
        this.name = "Unknown";
    }
}
```

Such no-argument constructors are useful in cases when any default value is better than `null`.

## To sum up

- Any Java class has a constructor to initialize objects;
- A constructor has the same name as the class containing it;
- A constructor has no return type, not even `void`;
- If a class has no explicit constructors, the Java compiler automatically provides a default no-argument constructor;
- If we want to introduce new variables to denote the same thing, make the code clearer and less loaded with extra variables, the keyword `this` is used.

## Conclusion

**Constructors** are special methods used to initialize class objects when they are created using the `new` keyword. They have the same name as the class they belong to and have no return type (not even void). Constructors are necessary for initializing class objects and can take parameters to initialize fields with specific values. The `this` keyword is used in the constructor to reference the current object. If a class doesn't have explicit constructors, the Java compiler automatically provides a default no-argument constructor.
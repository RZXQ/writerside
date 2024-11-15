# Instance methods

As you know, a class is one of the fundamental concepts in Java. You develop the logic of a program by creating fields and methods inside classes. Fields describe an object's properties and methods describe what an object does. In this topic, we will go on to discuss the nature of methods in Java. All methods can be divided into two groups: **instance** and **static**. We were mostly focused on the static ones previously, so now let's learn more about [instance methods](https://hyperskill.org/learn/step/3495) to better understand the differences between the two.

## What's the difference?

Let's look at the code below. Here we have a class named `Human` with two fields and two methods.

```java
class Human {
    String name;
    int age;

    public static void printStatic() {
        System.out.println("It's a static method");
    }

    public void printInstance() {
        System.out.println("It's an instance method");
    }
}
```

The modifier `public` isn't important for us now. It just means that other classes can also get access to our methods.

As you see, the methods `printStatic` and `printInstance` have differences in [declaration](https://hyperskill.org/learn/step/3495). When you see a method, you can easily understand: if there is a word `static`, then the method is **static**; if there is no word `static`, then the method is an **instance** one.

Now let's see what this really means!

## Understanding: static and instance

To invoke a [static method](https://hyperskill.org/learn/step/3495) we don't need to create an object. We just call the method with the class name.

```java
public static void main(String[] args) {

    Human.printStatic(); // will print "It's a static method"
}
```

In other words, you can say that a static method belongs to a class (because we don't need an object).

An instance method requires a different invocation. As you already guessed, to invoke an instance method we have to create an object first. Otherwise, there is no way to use an instance method.

It's called an instance method because an instance is a concrete representation of an object.

Here we call the method `printInstance` for two different objects:

```java
public static void main(String[] args) {
        
    Human peter =  new Human();
    peter.printInstance(); // will print "It's an instance method"

    Human alice =  new Human();
    alice.printInstance(); // will print "It's an instance method"
}
```

So, we can say that an instance method is a method that belongs to each object that we created of the particular class.

## Instance methods: features

Instance methods have a great advantage: they can access fields of the particular object of the class.

To illustrate the feature, let's modify our class `Human`. We have one static method `averageWorking` and two instance methods: `work` and `workTogetherWith`.

```java
class Human {
    String name;
    int age;

    public static void averageWorking() {
        System.out.println("An average human works 40 hours per week.");
    }

    public void work() {
        System.out.println(this.name + " loves working!");
    }

    public void workTogetherWith(Human other) {
        System.out.println(this.name + " loves working with " + other.name + '!');
    }
}
```

The keyword `this` represents a particular instance of the class.

It's easier to understand by an example:

```java
public static void main(String[] args) {
        
    Human.averageWorking(); // "An average human works 40 hours per week."

    Human peter =  new Human();
    peter.name = "Peter";
    peter.work(); // "Peter loves working!"

        
    Human alice =  new Human();
    alice.name = "Alice";
    alice.work(); // "Alice loves working!"

    peter.workTogetherWith(alice); // "Peter loves working with Alice!"
}
```

Look, now we have different outputs for the method `work` because two different objects have different values for `name`. First, we created `peter` and gave him a name, then by invoking `peter.work()` we actually saw his name in the output. We did the same with `alice` and also saw her name in the output.

Look at the `workTogetherWith` method. The keyword `this` allows us to access a field of the particular object and distinguish it from the same field of another object.





> In this case, keyword `this` is optional, so the code will work the same without it. But it's a good practice to add it to avoid confusion.





Of course, instance methods can take arguments and [return values](https://hyperskill.org/learn/step/3495) just as you saw in the previous topics. Return values can be of any type including the same type as the defined class.

## Summary

In Java, every method should be declared within a class. The difference between instance and the static methods lies in whether they interact with an object or not. Let's recap:

- static method is associated with the class as a whole;
- an instance method can only be invoked through an instance of a class, so that you have to create an object first;
- instance methods can access the fields of the class with `this` keyword.

Instance methods allow programmers to manipulate particular objects of a class. And because of it, they give us more functionality and are used more often than static methods!
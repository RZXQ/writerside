# Multiple conditions: switch

You already know how to shape the [control flow](https://hyperskill.org/learn/step/3504) of a program using [if-else statements](https://hyperskill.org/learn/step/3504). Perhaps, you have faced situations in which you had to stack and nest multiple if-else statements to get the desired result. In this topic, you will learn an alternative way to deal with multiple choices: **the [switch statement](https://hyperskill.org/learn/step/3504)**. It enhances code readability, efficiency, and organization compared to lengthy `if-else` chains, making it valuable for handling multiple conditions.

## When a conditional statement is not so good

Suppose you need to write a program that performs different actions depending on the value of a variable. For example, choosing an action from the menu of a game. To do that you can use a conditional statement with multiple branches as shown below.

```java
int action = ...; // a certain value from 1 to 4
        
if (action == 1) {
    System.out.println("Starting a new game...");
} else if (action == 2) {
    System.out.println("Loading a saved game");
} else if (action == 3) {
    System.out.println("Displaying help...");
} else if (action == 4) {
    System.out.println("Exiting...");
} else {
    System.out.println("Unsuitable action, please, try again");
}
```

Of course, this code handles the task. But if your conditional statement has a lot of branches, it can be hard to understand for people.

## Three keywords: switch, case, and default

**The switch statement** provides a way to choose between multiple cases based on the value of a single variable (not an [expression](https://hyperskill.org/learn/step/3504)!). The [variable](https://hyperskill.org/learn/step/3504) can be an integer number, character, string, or enumeration. The last two types will be examined further in the following topics.

With the switch statement, the previous code will look like this:

```java
switch (action) {
    case 1:
        System.out.println("Starting a new game...");
        break;
    case 2:
        System.out.println("Loading a saved game");
        break;
    case 3:
        System.out.println("Displaying help...");
        break;
    case 4:
        System.out.println("Exiting...");
        break;
    default:
        System.out.println("Unsuitable action, please, try again");
}
```

As you can see, this code is well-structured and easier to read than the equal [conditional statement](https://hyperskill.org/learn/step/3504). We have not explained the keywords `switch`, `case`and `break` yet, but you can already guess what they mean.

## The general form of the switch statement

The most general form of the switch statement is the following

```java
switch (variable) {
    case value1:
        // do something here
        break;
    case value2:
        // do something here
        break;
    
    //... other cases
    
    case valueN:
        // do something here
        break;
    default:
        // do something by default
        break; // it can be omitted
}
```

The `switch` and `case` keywords are always required here. The keywords `break` and `default` are optional. The keyword `break `stops the execution of the whole switch statement, not just one case.

If a `case` does not have the `break` keyword, the following `case` will be executed as well, including the `default` case. The `default` case is also executed if there's no other `case` that matches the variable value. The `break` keyword in the `default`branch is optional and can be omitted.

A `case` section may contain any block of code, even a nested `switch` statement, however, it is recommended to avoid deeply nested code structures whenever possible.

## An example with "zero", "one" and "two"

Let's consider another example. The following code outputs the names of integer numbers or a default text. This switch statement has three base cases and a single default case.

```java
int val = ...;
switch (val) {
     case 0:
         System.out.println("zero");
         break;
     case 1:
         System.out.println("one");
         break;
     case 2:
         System.out.println("two");
         break;
     default:
         System.out.println("The value is less than zero or greater than two");
} 
```

If `val` is 0, the code prints:

```java
zero
```

If `val` is 1, the code prints:

```java
one
```

if `val` is 10, the code prints:

```java
The value is less than zero or greater than two
```

If you forget the keyword `break` in a case, the compiler won't consider it an error. Let's remove it from the second case (case 1) and assign 1 to `val`. The program prints:

```java
one
two
```

Omitting the `break` keyword is not a good practice. Try to avoid it.

Java 12 introduced some new features allowing to use **switch** as an [expression](https://hyperskill.org/learn/step/16036).

## Conclusion

When you have a limited number of cases to choose from, switch statements can help you avoid extensive if-else constructions. For that, you need the `switch`keyword to introduce the value to evaluate, and `case` for each of the possible values. Do not forget to also use the `break` keyword to avoid executing extra cases and `default` branch to indicate the default behavior.
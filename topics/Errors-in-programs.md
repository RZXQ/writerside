# Errors in programs

Suppose, you're writing a Java program. Different errors may occur during its compilation or execution. We will divide all possible errors into two groups: **[compile-time errors](https://hyperskill.org/learn/step/3536)** and **[run-time errors](https://hyperskill.org/learn/step/3536)**.

Let's look at cases where errors occur and how to avoid them.

## Compile-time errors

Compile-time errors are errors that prevent a Java program from being compiled:

- a [syntax error](https://hyperskill.org/learn/step/3536): an incorrect keyword, a forgotten `;` symbol at the end of a statement;
- a bad source code file name;
- invoking a non-existing method;
- and many others.

Consider an example of compile-time errors. The following program should output the string **"Hello!"** but it does not compile.

```java
public class MyClass {

    public ztatic void main(String[] args) {
        System.out.printn("Hello!");
    }
}
```

There are two errors in this program:

- a typo in the keyword `static`;
- incorrect name of the method `println`.

If you fix these mistakes, it will be possible to compile this program.

To avoid such errors, programmers use a modern IDE (Integrated Development Environment) with a static code analyzer. This tool allows programmers to identify compile-time errors before the compilation. In addition, it is able to highlight warnings about more complex errors and weak places in your code, as well as tips on how to improve the code.

Over time, you will write code that contains fewer or even no compile-time errors.

## Run-time errors

Run-time errors (also known as "bugs") are errors that occur when the program is running. Run-time errors will cause your program to behave unexpectedly or may even stop the execution.

There are two subtypes of run-time errors:

- **[logic errors](https://hyperskill.org/learn/step/3536)** – when a program produces a wrong result because the code is not correct (for example, instead of **"Hello!"**, your program outputs **"Hi!"**);
- **unhandled exceptional events** like division by zero, not found files, and other unexpected cases.

We will learn how to handle exceptional events (exceptions) in further lessons.

Avoiding such run-time errors is a more difficult task than avoiding compile-time errors. If your program compiles successfully, there are no guarantees that it does not have bugs. There are different strategies to find such errors:

- to **debug** your program;
- to write **automated tests** for your program;
- to use the practice of **[code review](https://hyperskill.org/learn/step/3536)** as part of the development process. In general, this practice stands for a case, where one or more developers visually inspect the source code of a program.

## Conclusion

- Compile-time errors happen when a program fails to compile. They include typos and incorrect method invocations.
- Static code analyzers in IDEs help to spot compile-time errors before program compilation.
- Run-time errors, or bugs, occur after compilation when a program is running. They may result in unexpected program behavior and crashes.
- Debugging is a useful instrument to identify run-time errors in your program.
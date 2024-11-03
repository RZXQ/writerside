# Random class

A **[random number](https://hyperskill.org/learn/step/4910)** is a number that is almost impossible to predict, like the result of throwing a dice. A random number generator can provide you with such a number when you need it, and you will probably need it quite often. For example, it comes in handy when you're trying to create a password nobody can guess, make the next unpredictable move in a game, or generate a lot of random data for testing purposes. Random generators are widely used in cryptography, machine learning, games, and more.

## Pseudorandom numbers and seeding

Before we start exploring how to generate random numbers in Java, let's focus on one important point. The random numbers we are going to discuss aren't truly random because they can always be determined by an initial value, called **seed**.





> Every time we get a new random number, we actually get the next number in a predefined sequence. These numbers are often called **[pseudorandom](https://hyperskill.org/learn/step/4910)**, and they are not completely unpredictable! We can calculate them all if we know the initial value and the algorithm of the [sequence](https://hyperskill.org/learn/step/4910). That initial value is called a **seed**.



It is guaranteed that the same seed produces the same sequence if the same Java runtime version is used because the algorithm is the same. However, that is good enough for practical tasks. These generators are quite important because of their speed in number generation and their reproducibility.

## Creating a pseudorandom generator

Java provides the `Random` class to generate pseudorandom values of different types, such as `int`, `long`, `double`, and even `boolean`. We will consider how to use this class only for numbers.

First of all, we need to import it:

```java
import java.util.Random;
```

We have two constructors to create an object of this class:

- `Random()` creates a new random generator and sets the **seed** of the generator to a value that is very likely to be distinct from any other invocation of this constructor:

```java
Random random = new Random();
```

- `Random(long seed)` creates a new random generator with the specified initial value of its internal state:

```java
Random random = new Random(100000);
```

If we don't specify a seed, the generator will give us a new sequence every time. But if we specify the seed, the sequence will be calculated based on it.

Regardless of what constructor we used, we have a generator called `random` that can produce random numbers.

## The basic methods

After we've created a generator, we can invoke one of the following methods of it:

- `int nextInt()` returns a pseudorandom value of the `int` type;
- `int nextInt(int n)` returns a pseudorandom value of `int` type in the range from `0`(inclusive) to `n` (exclusive);
- `long nextLong()` returns a pseudorandom value of `long` type;
- `double nextDouble()` returns a pseudorandom value of `double` type between `0.0` and `1.0`;
- `void nextBytes(byte[] bytes)` generates random bytes and places them into a user-supplied byte array.

All the listed methods produce uniformly distributed values.

Let's take a look at an example:

```java
Random random = new Random();
System.out.println(random.nextInt(5)); // it may print 0, 1, 2, 3, 4
```

If we start this code multiple times, the result is different (or it may happen to be the same).

If we need to reproduce the same sequence of random numbers, we may specify a seed to the constructor:

```java
Random random = new Random(100000);
System.out.println(random.nextInt(5)); // it may print 0, 1, 2, 3, 4
System.out.println(random.nextInt(5)); // it may print 0, 1, 2, 3, 4
```

in this case, while starting the program multiple times, we will always get the same numbers in the output.





> **Note:** an object of the `Random` class can generate Gaussian distributed pseudorandom double numbers by invoking the `nextGaussian()` method. This distribution may be required for some statistical analysis and machine learning applications, but it is not that common in general programming.



## An example: printing pseudorandom numbers

Let's suppose that we need a program that prints out a specified number of pseudorandom integers within a given range (boundaries included). Unfortunately, the `Random` class does not provide a method to generate numbers in a range. Let's use it as an opportunity to practice and create it from scratch!

As you remember, the `nextInt(n)` method produces a pseudorandom integer from `0` (inclusive) to `n`(exclusive).

![Pseudorandom number from 0 to n image](https://ucarecdn.com/655547bc-1f49-4156-8ed5-bda751413f14/)

We want to use it to generate numbers within a specific range, for example, from 2 to 5, including both boundaries.

![the numbers from 2 to 5 inclusive image](https://ucarecdn.com/c0f1974f-0476-448d-b664-04e95a746362/)

Let's take the length of the interval plus one: 5 – 2 + 1 = 4. It allows us to generate any number from 0 to 3 by using the `nextInt(4)` method.

![take interval from 0 to 3 inclusive image](https://ucarecdn.com/f46f53d9-9af0-4191-8a64-4f66af44497c/)

Now imagine that we shift the interval to the value of the lower border (2) as we need.

![interval from 2 to 5 inclusive image](https://ucarecdn.com/c1baea68-4005-4b91-a0ce-dd3480031789/)

This way, we can generate any numbers from 2 to 5, including both boundaries.

The illustrated idea can be implemented by a simple code line:

```java
int next = random.nextInt(upper - lower + 1) + lower;
```

Here is the complete program that prints 4 pseudorandom integers within a given range:

```java
import java.util.*;

public class RandomNumbersDemo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int lower = scanner.nextInt();
        int upper = scanner.nextInt();
        Random random = new Random();

        int intervalLength = upper - lower + 1;

        System.out.println(random.nextInt(intervalLength) + lower);
        System.out.println(random.nextInt(intervalLength) + lower);
        System.out.println(random.nextInt(intervalLength) + lower);
        System.out.println(random.nextInt(intervalLength) + lower);
    }
}
```

For example, we have to generate numbers exactly within the range from 20 to 30 (inclusive):

```java
20 30
```

An output example:

```java
25
26
30
20
```

As you can see, dealing with the `Random` class is simple enough. Don't be afraid to introduce a bit of randomness into your programs :)

## Conclusion

Java provides the `Random` class to work with pseudorandom data. To work with it, we need to decide whether we need a predictable result or not. In the first case, we can use a known seed, and in the second case we can simply use the default seed which is generated based on the current system time. Remember that random sequences are only guaranteed to be the same if they are generated with the same version of Java runtime, but they can be different in different Java versions or different programming languages even for the same seed.
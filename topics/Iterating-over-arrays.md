# Iterating over arrays

## Processing Arrays Using Loops

It's quite useful to process an array by going through it with a loop. The `length` property of an array can help you avoid an `ArrayIndexOutOfBoundsException`.

You can fill an array with the square of its element's index. The example below shows how:

```java
int n = 10; // the size of an array
int[] squares = new int[n]; // creating an array with the specified size

System.out.println(Arrays.toString(squares)); // [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

/* iterating over the array */
for (int i = 0; i < squares.length; i++) {
    squares[i] = i * i; // set the value by the element index 
}

System.out.println(Arrays.toString(squares)); // [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

The code above creates a ten-element array, initially all zeros. Then it sets each element's value to the square of its index. It turns the array into a string, displaying all elements inside square brackets and print this string on the screen.

Next, let's see how to use a loop to check an array's elements order.

The program below verifies if the provided array is sorted in ascending order. It prints "OK" if it is, and "BROKEN" if not.

```java
int[] numbers = { 1, 2, 3, 4, 5, 10, 6 }; // the order is broken

boolean broken = false; // suppose the array is well-ordered

/* iterating over the array */
for (int i = 1; i < numbers.length; i++) {
    
    if (numbers[i] < numbers[i - 1]) { // if the order is broken
        broken = true; // write a result
        break;         // terminate the loop
    }
}

if (broken) {
    System.out.println("BROKEN");
} else {
    System.out.println("OK");
}
```

In this program, for the provided array, the output is `"BROKEN"`.

You can also use while and [do-while loops](https://hyperskill.org/learn/step/3602) for array iterations, but these aren't typically used as often.

## Reading an array from the standard input

You can also use a loop to read all the elements of an array from the standard input.

For example, the following input consists of two lines. The first line has the length of the array and the second line has all its elements.

```java
5
101 102 504 302 881
```

We will read these numbers using `Scanner` (other tools for reading can also be used) and then output all the numbers we read.

```java
Scanner scanner = new Scanner(System.in);
        
int len = scanner.nextInt(); // reading a length
int[] array = new int[len];  // creating an array with the specified length
        
for (int i = 0; i < len; i++) {
    array[i] = scanner.nextInt(); // read the next number of the array
}

System.out.println(Arrays.toString(array)); // output the array
```

The program outputs:

```java
[101, 102, 504, 302, 881]
```

## Using the for-each loop

Since Java 5, there has been a special form of the for-loop known as **for-each**. It's used to iterate through each element of an array, string, or collection. With it, you don't have to deal with indices.

Here's what it looks like:

```java
for (type var : array) { 
    //statements using var
}
```

And here's how to read it: for each element `var` of type `type` in the array `array`, execute the [statements](https://hyperskill.org/learn/step/3602) in the body.

Let's take a closer look at the components. `type`specifies the variable type that will store one array element during each iteration. Usually, this type matches the array element's type. The `var` [variable](https://hyperskill.org/learn/step/3602)holds one array element in each iteration. Its value changes with each iteration to store the next element.

Let's now compute the number of `'a'` letters in a given character array using a **[for-each loop](https://hyperskill.org/learn/step/3602)**:

```java
char[] characters = { 'a', 'b', 'c', 'a', 'b', 'c', 'a' };

int counter = 0;
for (char ch : characters) {
    if (ch == 'a') {
        counter++;
    }
}

System.out.println(counter); // it outputs "3"
```

We can achieve the same result with a standard for-loop:

```java
char[] characters = {'a', 'b', 'c', 'a', 'b', 'c', 'a'};

int counter = 0;
for (int i = 0; i < characters.length; i++) {
    if (characters[i] == 'a') {
        counter++;
    }
}

System.out.println(counter); // it outputs "3"
```

The for-each loop does have some limitations. You can't use it to modify an array because the variable we use for iterations doesn't hold the actual array element, only a copy. You also can't retrieve an element by its index as the index isn't used. Lastly, we can't move through an array with more than one step per iteration: we iterate through each element one-by-one.

The lack of indices makes the code more readable. The for-each loop also helps us avoid a `ArrayIndexOutOfBoundsException`. These benefits make it a popular choice for array iteration.

## Conclusion

Using loops is a convenient way to handle an array of elements. Loops let you perform various algorithms, go through an array, and read inputs from the standard input. The for-each loop, a specific for-loop kind, is frequently used to go through each element of an array, string, or collection without using their indices. Although it has some limitations, it aids in code readability and prevents `ArrayIndexOutOfBoundsException`.
# Characters and Strings

## Learning Goals

- Go more in depth about characters and ASCII values
- Discuss escape sequences
- Explain character arrays and strings

## Introduction

So far, we have seen the `char` data type reference in passing, and we know it
stores a single character or ASCII value, but we really haven't used it or
talked too in-depth about it. In this section, we will explore characters some
more, talk about what an ASCII value is, point out a few special characters,
and explain how it might relate to the `String` class.

## The `char` data type

A `char` is a primitive data type that takes up to 2 bytes of memory. We may
recall from the Variables' lesson that a `char` stores a single character or an
ASCII value.

`char grade = 'A';`

The above code is how we would initialize a `char` data type. A `char` variable
can be assigned a value by enclosing the character in single quotes, such as
'A'.

The `char` data type can also be considered a numeric value. If we remember
from the Type Casting lesson, we said that a `char` could be upcasted to an
`int`, `long`, `float`, or `double`. This means, in Java, it treats `char` as
a number. We might be wondering, "But how?" since 'A' is clearly a letter and
not a number. But all characters can actually be converted to a decimal number!
This brings us to what an ASCII table is:

![ASCII Table](https://curriculum-content.s3.amazonaws.com/java-mod-2/chars-and-strings/ASCII-Table.png)

[Medium: ASCII Table in Java Programming](https://medium.com/@aidafarihabaharunsuratman/did-someone-actually-use-ascii-table-in-java-programming-9710a65c6ed9)

An **ASCII Table** is a tabular representation that links characters to decimal
values. We can see what each letter represents using this ASCII table. We can
also see that the uppercase characters have different values from the lowercase
letters. This means that 'A' would not be the same as 'a' in Java!

Let's consider our example again: `char grade = 'A';` We can see in the ASCII
table that the character 'A' has a decimal value of 65. Does this mean, that if
we set `char grade` to the number 65 that it would be the same as setting it to
'A'?

```java
char firstGrade = 'A';
char secondGrade = 65;
if (firstGrade == secondGrade) {
    System.out.println("Wow! 'A' is the same as 65!");
} else {
    System.out.println("Told you 'A' wasn't the same as 65!");
}
```

The output to the code above is:

```plaintext
Wow! 'A' is the same as 65!
```

As we can now see, the definition of a `char` data type makes more sense when
we say "stores a single character or an ASCII value" since we could set it to
either a numeric value or use single quotes to wrap a character! For readability
in Java, we tend to set `char` data types to the characters using single quotes
instead of using the decimal values. In other words, `char grade = 'A';` is
preferred over `char grade = 65;`.

## Escape Sequences

Java also has several special characters. These special characters can be
accessed using the backslash character '\', also known as the **escape**
**character**. Whatever follows the escape character is known as an
**escape sequence.**

For example, if we want to use a double quotation mark within a `String`, we
can use the escape sequence `\"`. The backslash escapes the double quote and in
turn, tells Java that we are to use the double quote within the `String` and not
end the `String` (since we usually wrap `String` values in double quotes). Let's
look at an example of this:

```java
System.out.println("\"You must be the change you wish to see in the world.\" - Mahatma Gandhi");
```

Output:

```plaintext
"You must be the change you wish to see in the world." - Mahatma Gandhi
```

Notice how the backslashes are not printed but the double quote immediately
following the backslash is printed. This is because the escape character
notifies Java that we are to print the escape sequence instead that results in
just a double quotation mark. Java also treats the escape sequence as one
character - meaning `\"` would be considered one character, not two.

Consider the table of escape sequences:

| Escape Sequence | Display      |
|-----------------|--------------|
| `\t`            | Tab          |
| `\n`            | New Line     |
| `\'`            | Single Quote |
| `\"`            | Double Quote |
| `\\`            | Backslash    |

A few notes on the escape sequences: The tab and new line characters are
representatives of whitespace. Consider the example below of how to use these
characters:

```java
String firstString = "Hello\tWorld!";
String secondString = "What a beautiful\nday!";

System.out.println(firstString);
System.out.println(secondString);
```

Output:

```plaintext
Hello   World!
What a beautiful
day!
```

We can see in the above output that when we placed the character `\t` between
"Hello" and "World!", it placed a tab or an indent between the two words. In the
`secondString`, we place a `\n` character between the words "beautiful" and
"day!". When we print that to the screen, it will actually write the word "day!"
on a new line separate from "What a beautiful".

## Strings and Character Arrays

A sequence of characters can be treated as a single unit... and that is
where the `String` data type comes in. But we also just learned about arrays. So
wouldn't an array of characters be the same thing as a `String`?

The answer is: no - but pretty close!

In Java, there are a few differences between a `String` and a `char[]`:

1. A `String` is a sequence of characters where a `char[]` is a collection of
   `char` data types. In a `char[]`, each element could be treated independently
   and separately. For example, we could have a character array of grades:
   `char[] grades = {'A', 'B', 'C', 'D', 'F'};`.
2. A `String` is an immutable type whereas a `char[]` is still mutable.
3. We can use a `+` to concatenate two `String` values together but cannot do
   the same for a character array.
4. The `String` class has built-in methods that we will cover in the next couple
   of lessons. But a `char[]` does not have any built-in methods; however, we
   can pass it in as a parameter to the `Arrays` class as we saw with the method
   `Arrays.sort()`.

There is a way for us to convert a character array into a `String` though and
vice versa!

To convert a character array into a `String`, we could make use of the `String`
constructor:

```java
char[] gradesAsCharArray = {'A', 'B', 'C', 'D', 'F'};
String gradesAsString = new String(gradesAsCharArray);
```

To convert a `String` into a character array, we can actually use a method of
the `String` class called `toCharArray()`. We will learn more about the methods
within the `String` class in the next lesson, but here is how we can use that
method to go from a `String` to a `char[]`.

```java
String gradesAsString = "ABCDF";
char[] gradesAsCharArray = gradesAsString.toCharArray();
```

## Resources

- [Medium: ASCII Table in Java Programming](https://medium.com/@aidafarihabaharunsuratman/did-someone-actually-use-ascii-table-in-java-programming-9710a65c6ed9)

# Checkout

## Logical operators and comparing Strings

In this exercise you will get experience using "and", "or", and "not" in Java using the logical operators `&&`, `||`, and `!`. You will also learn how to compare String objects, which operates differently than the comparison of primitives.

## Logical Operators

There are three logical operators in Java, summarized in the following table.

|logical operator | meaning | example |
| --- | --- | ---|
| `&&`  | and | `a < 3 && b > 10` |
| `\|\|` | or | `a < 3 \|\| b > 10` |
| `!` | not | `!(a < 3)` |

If needed, see the [text book for more info on logical operators](http://greenteapress.com/thinkapjava/html/thinkjava008.html#toc52)

## String comparison

There are two categories of data types in Java: primitives (such as `int`, `double`, `boolean`, and `long`), and objects (such as `Scanner` and `String`). For primitives, the equality operator, `==`, compares the values.

For objects, however, the `==` has a different meaning (it determines if two objects are the _exact same_ object in memory). Usually, this is not what we want. Instead, we use methods to compare objects. These methods return boolean values, so we can use them in `if` statements and `while` loops just as we would when comparing primitives. Here is how to determine if two String objects contain exactly the same characters:

| String method | meaning | example | in English |
| --- | --- | --- | --- |
| `equals` | do the two Strings have exactly the same characters? (case sensitive) | `while(z.equals("Hello")) { }` | Loop executes as long as z consists of _exactly_ the characters `Hello` |
| `equalsIgnoreCase` | do the two Strings have exactly the same characters? (ignoring case) | `while(z.equalsIgnoreCase("Hello")) { }` | Loop executes as long as z consists of the characters `Hello`, in any combination of uppercase and lowercase letters |

>[!NOTE]
> Strings are a special kind of object in Java. To improve performance and reduce memory usage Java uses string interning. In computer science, string interning is a method of storing only one copy of each distinct string value, which must be immutable. Interning strings makes some string processing tasks more time- or space-efficient at the cost of requiring more time when the string is created or interned. The distinct values are stored in a string intern pool.
>
> Because of String interning, using `==` will work similar to primitive types. This is different behavior than EVERY single other object in Java so get in the habit of using the ".equals" method with Strings.

## Shop smart. Shop KowMart

Create a new class inside called `Checkout`

This will be a point-of-sale program for a self-checkout counter. Here's the final product in action:

```text
KowMart express self-checkout (10 item limit)
How many items (1-10)?
0
How many items (1-10)?
11
How many items (1-10)?
3
Cost of next item?
1.20
Cost of next item?
.95
Cost of next item?
3.30
Do you want a bag (costs .05 extra if you have 3 or less items)?
yes
Your total with 6% MI tax is 5.829999999999999
```

__The program first asks how many items there are, then adds up the cost of all the items, asks if they want a bag, and finally give the total amount due including tax__. Start with the following code.

```java
       //Create Scanner object and print greeting.
        Scanner keyboard = new Scanner(System.in);
        System.out.println("KowMart express self-checkout (10 item limit)");

        //Ask how many items
        int items;
        do {
            System.out.println("How many items (1-10)?");
            items = keyboard.nextInt();
        } while( TODO );

        //Add up the cost of each item (while loop, repeat items times)
        //Ask if a bag is needed
        //Add the cost of bag, if necessary.
        //Add in tax.
        //print out the total.
```

Using our new logical operators, __fill in a while that loops as long as they give a number that is less than 1 or greater than 10__. Your program should now act like this:

```text
KowMart express self-checkout (10 item limit)
How many items (1-10)?
0
How many items (1-10)?
11
How many items (1-10)?
3
```

Next, __make a double variable called cost__, for storing the cost of an item entered by the user, and __make another double variable called total__, which will store the total cost of all the goods they are buying (initially this should be set to 0).

Also, __create a counter variable, for instance, k, and set it to 0__. Then __write a second loop, a while loop that repeats as long as k is less than items, the number of items entered above__. Inside this loop:

1. ask for the cost of each item
2. read the cost using your Scanner already defined, and
3. add the current cost to the total (don't worry about checking for negative dollar amounts - we trust our customers and maybe they are entering a coupon). Now you are this far:

```text
KowMart express self-checkout (10 item limit)
How many items (1-10)?
0
How many items (1-10)?
11
How many items (1-10)?
3
Cost of next item?
1.20
Cost of next item?
.95
Cost of next item?
3.30
```

Now ask if they want a bag. Get the user's input and store it into a `String` variable. If they have 3 or less items and they said anything other than "no", then charge them an extra 5 cents (use one of the equality methods of the `String` class, from the table at the start of this lab). There __isn't__ a String method called `notEqual`, but we can make do with a logical operator. For example, if you have a String variable called s and you want an expression that tests to see if it is not equal to "hello", then the following code does it: `!s.equals("hello")`

Finally, add sales tax. That's just a simple matter of multiplying the total by 1.06, and then printing it out.

```text
KowMart express self-checkout (10 item limit)
How many items (1-10)?
0
How many items (1-10)?
11
How many items (1-10)?
3
Cost of next item?
1.20
Cost of next item?
.95
Cost of next item?
3.30
Do you want a bag (costs .05 extra if you have 3 or less items)?
yes
Your total with 6% MI tax is 5.829999999999999
```

To avoid printing out all those 9's above, you can change the last print statement to use a format command. It looks like this: `System.out.printf("Your total with 6%% sales tax is $%1.2f\n",total);` and what it does is print out the value of total using the format instruction `1.2f` which means floating point output with 2 digits after the decimal point.The `\n` symbol advances to the next line after the print.

If you are looking for an extra challenge: write a loop so that it keeps asking them if they want a bag until they either say "yes" or "no".

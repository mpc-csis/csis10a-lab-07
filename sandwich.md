# Sandwich

## Using while loops and do...while loops

In this exercise you will practice using while loops and do...while loops.

## Dr. Kow's Hamburger Palace

__Create a new Java project__. Then create a class file called `Sandwich.java`. Please make sure you add a standard comment header (name, date, etc).

This program will make a virtual sandwich. Since our laptops are lacking the robotic actuators and other materials to make a sandwich, we will print it out on the screen. Here's a preview of the final product:

```text
******************************
*                            *
*                            *
*                            *
*                            *
*                            *
* Dr. Kow's Hamburger Palace *
*                            *
*                            *
*                            *
*                            *
*                            *
******************************

How many layers of lettuce do you want?
2
How many layers of tomatoes do you want?
1
Here's your sandwich:

(_________)
 ~~~~~~~~~
 ~~~~~~~~~
 [  ] [  ]
 *********
(_________)
```

__Start by outlining our program.__

```java
//Print the Hamburger Palace sign.
//Create a Scanner object for user input
//Ask how much of the toppings the user wants (reject negative numbers)
//Print out the result to the screen
```

### Writing the program

Print out the hamburger palace sign. Printing out the "Hamburger Palace" sign involves printing the same line a number of times. Rather than a whole bunch of System.out.println statements, we will use a while loop to do this.

```java
//Print the Hamburger Palace sign.
System.out.println("******************************");
int line = 0;
while(line < 5) {
    System.out.println("*                            *");
    line = line + 1;
}
System.out.println("* Dr. Kow's Hamburger Palace *");  //...or whatever title you prefer
```

Your program output should now look like this (feel free to change the name of the restaurant):

```text
******************************
*                            *
*                            *
*                            *
*                            *
*                            *
* Dr. Kow's Hamburger Palace *
```

__Now write a second while loop__, so that you get this result:

```text
******************************
*                            *
*                            *
*                            *
*                            *
*                            *
* Dr. Kow's Hamburger Palace *
*                            *
*                            *
*                            *
*                            *
*                            *
******************************
```

Next, use a [Scanner](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/Scanner.html) object to capture a users input. Don't forget the import statement.

```java
       //Create a Scanner object for user input
        Scanner keyboard= new Scanner(System.in);
```

Now we will __ask how many layers of lettuce they want__. If they enter a negative int like -7 or -3, we will reject the input and make them enter something that makes sense. A "do...while" loop is well-suited to this sort of task, since the interior of the loop is guaranteed to execute at least once. Notice that in the following code, we don't need to initialize lettuce when we declare it. That's because the Java compiler realizes that it must get assigned some value in the do...while loop.

```java
       //Ask how much of the toppings the user wants (reject negative numbers)
        int lettuce;
        do {
            System.out.println("How many layers of lettuce do you want?");
            lettuce = keyboard.nextInt();
        } while(lettuce < 0);
```

Now that you know how much lettuce to print, it's time to __print out the whole burger. Start by printing the symbols for your bun.__  Then use a while loop (not a do...while loop) to print all the layers of lettuce. You'll need to figure out what condition should be inserted in the while statement where it says `/* TODO */` and convert the comments in the while loop into java statements.

```java
        //print the bun

        //this while loop should repeat as many times as the number stored in variable lettuce
        int line = 0;
        while( /* TODO */ ) {
            // print a line of lettuce symbols like ~~~~~~~~~~~
            // add one to variable line
        }
```

Your program should work like this now:

```text
******************************
*                            *
*                            *
*                            *
*                            *
*                            *
* Dr. Kow's Hamburger Palace *
*                            *
*                            *
*                            *
*                            *
*                            *
******************************

How many layers of lettuce do you want?
-1
How many layers of lettuce do you want?
-2
How many layers of lettuce do you want?
3
Here's your sandwich:

(_________)
 ~~~~~~~~~
 ~~~~~~~~~
 ~~~~~~~~~
 *********
(_________)
```

__Try running it again and ask for 0 layers of lettuce__. Notice how it gives you a sandwich without lettuce? Do you understand why?

__Modify your program so that it also asks for tomatoes before printing out the sandwich__. It should keep asking until the user gives a number of tomato layers which is 0 or greater. Finally, make it __print out the tomato layers__. Here is the final program:

```text
******************************
*                            *
*                            *
*                            *
*                            *
*                            *
* Dr. Kow's Hamburger Palace *
*                            *
*                            *
*                            *
*                            *
*                            *
******************************

How many layers of lettuce do you want?
-1
How many layers of lettuce do you want?
2
How many layers of tomatoes do you want?
-4
How many layers of tomatoes do you want?
-3
How many layers of tomatoes do you want?
3
Here's your sandwich:

(_________)
 ~~~~~~~~~
 ~~~~~~~~~
 [  ] [  ]
 [  ] [  ]
 [  ] [  ]
 *********
(_________)
```

### Encapsulation

What if we want to repeat the program without re-executing it? For instance, maybe we need to serve the next customer, and the next. We could build a large loop around all of our code in main( ) and have it repeat a certain number of times, or as long as there are more customers.

A better way is to encapsulate what we already have in a method. Let's do this now:

1. RENAME your main method to something like burger
2. create a new main method. In this new main method, call burger one time
3. compile and execute. The program should behave the same as before.
4. add a loop around your call to burger. In the body of the loop,
     before calling burger, print the message, "Next customer!"
     make the loop repeat 5 times

OPTIONAL CHALLENGE: after each burger, ask if there are more customers, enter 1 for yes, 0 for no,  and keep repeating the loop until the user enters 0. 

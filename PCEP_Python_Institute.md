---
layout: default
---

# Python Institue (PCEP) exercices

### Some exercices from Python Essentials Part1
<br />
ref: https://edube.org/

![Octocat](./assets/img/PythonEssentials.png)

---




## Operators and expressions
<br />
ref. https://edube.org/learn/pe-1/lab-operators-and-expressions-11
Estimated time

15-20 minutes
Level of difficulty

Easy
Objectives

    improving the ability to use numbers, operators, and arithmetic operations in Python;
    using the print() function's formatting capabilities;
    learning to express everyday-life phenomena in terms of programming language.


### Scenario

Your task is to prepare a simple code able to evaluate the **end time** of a period of time, given as a number of minutes (it could be arbitrarily large). The start time is given as a pair of hours (0..23) and minutes (0..59). The result has to be printed to the console.

For example, if an event starts at **12:17** and lasts **59 minutes**, it will end at **13:16**.

Don't worry about any imperfections in your code - it's okay if it accepts an invalid time - the most important thing is that the code produce valid results for valid input data.

Test your code carefully. Hint: using the `%` operator may be the key to success.

### CODE
``` python

hour = int(input("Starting time (hours): "))
mins = int(input("Starting time (minutes): "))
dura = int(input("Event duration (minutes): "))

time_hour = (hour+dura//60 + (mins+dura%60)//60)%24
time_min = (mins+dura%60)%60
print("It will end at " + str(time_hour) + ":" + str(time_min))

```
---
<br />

## Break and Continue

ref. https://edube.org/learn/pe-1/lab-the-break-statement-stuck-in-a-loop-3


Estimated time

10-20 minutes
Level of difficulty

Easy
Objectives

Familiarize the student with:

    using the break statement in loops;
    reflecting real-life situations in computer code.

### Scenario

The break statement is used to exit/terminate a loop.

Design a program that uses a while loop and continuously asks the user to enter a word unless the user enters "chupacabra" as the secret exit word, in which case the message "You've successfully left the loop." should be printed to the screen, and the loop should terminate.

Don't print any of the words entered by the user. Use the concept of conditional execution and the break statement.

q
``` python
secret = "chupacabra" 
counter = 0
while True:
    word = str(input("Enter a word: "))
    if word == secret:
        break
    counter += 1
    print("Looooooping.", counter)
print("You've successfully left the loop.")

```
---
<br />


## The continue statement - the Ugly Vowel Eater
ref. https://edube.org/learn/pe-1/lab-the-continue-statement-the-ugly-vowel-eater-3

Estimated time

10-20 minutes
Level of difficulty

Easy
Objectives

Familiarize the student with:

    using the continue statement in loops;
    reflecting real-life situations in computer code.

### Scenario

The continue statement is used to skip the current block and move ahead to the next iteration, without executing the statements inside the loop.

It can be used with both the while and for loops.

Your task here is very special: you must design a vowel eater! Write a program that uses:

    a for loop;
    the concept of conditional execution (if-elif-else)
    the continue statement.

Your program must:

    ask the user to enter a word;
    use user_word = user_word.upper() to convert the word entered by the user to upper case; we'll talk about the so-called string methods and the upper() method very soon - don't worry;
    use conditional execution and the continue statement to "eat" the following vowels A, E, I, O, U from the inputted word;
    print the uneaten letters to the screen, each one of them on a separate line.

Test your program with the data we've provided for you.

Test data

Sample input: Gregory
```
Expected output:
G
R
G
R
Y
```
Sample input: abstemious
``` 
Expected output:
B
S
T
M
S
```
Sample input: IOUEA
```
Expected output:
??
```

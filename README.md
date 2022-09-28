# CSE 11 Fall 2022 PA1 - Grade Calculator
**Due date: Thurs, Oct 6 @ 11:59PM PDT**

There is an FAQ post [TODO] on Piazza. Please read that post first if you have any questions.

## Goal:
Programming Assignment 1 is an introduction to Java programming. In this PA, you will get exposure to primitive data types, variables, keyboard input, console output, if-else logic, and loops. 

## Overview
There are 3 parts in this assignment. All are required before the deadline.

- Part 1: Integrity of Scholarship Agreement [Google Form, 1 point]
- Part 2: Pre-class Survey [Survey, 2 points]
- Part 3: Grade Calculator [Gradescope, 97 points]
    - Implementation [97 points]
    - Style [0 points]

**Note:** The grade for the Financial Aid Survey will appear on Canvas so your score on Gradescope will be out of 99 points.

## Part 1: Academic Integrity [1 point]
We take Academic Integrity (AI) very seriously at UCSD. Before beginning the assignment please fill out the [AI form](https://forms.gle/X3Qs2DrHUaxDpP959). **You must fill this out in order to recieve points for any assignments.**

## Part 2: Surveys [2 points]
Please fill out this [Financial Aid Survey](https://canvas.ucsd.edu/courses/39523/quizzes/116494) on Canvas to help us understand the background and goals of the students in this course and meet the new financial aid requirement.

Additionally, fill out the [Pre-Class Survey](https://forms.gle/cYerU7snvoQYyMRy8). 

The surveys are worth one point each. You will receive credit for submitting it, but your specific answers will not affect your grade in the course in any way.

## Part 3: Grade Calculator [97 points]

Write a program called `GradeCalculator` that
- reads a student's scores for programming assignments, midterm, and final
- calculates their overall score by applying weights 
- outputs the overall score and its corresponding letter grade

### Setup
Please follow [our tutorial](https://piazza.com/class/l871flmwsqy8i/post/13) on Piazza to have Java 17 installed on your machine in order to complete this assignment. Additionally, familiarize yourself with some bash commands (optional):
- Essential Commands: https://www.hongkiat.com/blog/web-designers-essential-command-lines/
- Unix reference sheet: https://files.fosswire.com/2007/08/fwunixref.pdf


### Implementaion Details
Your file should be named as `GradeCalculator.java` and contains a single class `GradeCalculator` which has only 1 method: `main`.


There are a few restrictions on the implementation. 
- You should not import anything other than `java.util.Scanner`. If you import any other libraries, you may get a 0 for this part, even though if you had passed all the test cases.
- You should not use `System.exit`. Doing so will cause Autograder to throw exceptions and you'll get "EXCEPT" for all of your test cases.

To get started on this PA, follow Section 2 in the [instructions](https://piazza.com/class/l871flmwsqy8i/post/13) again but create a folder for "PA1" at the location of your choice and open that folder in Visual Studio Code (VS Code). Then create a class named `GradeCalculator` with a `main` method and save it as `GradeCalculator.java`.

#### Input

The program reads user inputs from `System.in` using a [Scanner](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html) (*remember to import it*). When an user runs `java GradeCalculator`, the input should be taken in via the keyboard and should contain exactly 2 lines detailing the number of programming assignments $n$. You can safely assume that all our inputs will follow this format.

The first line contains $n + 1$ space-separated integers: $n \hspace{1mm} ␣ \hspace{1mm} pa_1 \hspace{1mm} ␣ \hspace{1mm}pa_2\hspace{1mm} ␣ \hspace{1mm}pa_3 \hspace{1mm} ...  \hspace{1mm} pa_n$ ($␣$ means a space), where 
- $n$ is an integer representing the number of programming assignments
- $pa_1\hspace{1mm} ␣ \hspace{1mm}pa_2\hspace{1mm} ␣ \hspace{1mm}pa_3 \hspace{1mm} ...  \hspace{1mm} pa_n$ are integers representing the score for each programming assignment

The second line contains 2 space-separated integers: the first one represents the midterm score and the second one represents the final score.

If any score is less than 0 or greater than 100, or if the number of programming assignments $n$ is equal to 0, print `invalid input`. You may assume that $n$ will be non-negative.

#### Calculation
1. find the average score of programming assignments
2. calculate the overall score by using the *Grade Breakdown* table below

    | Type                    | Weight|
    | ----------------------- | ----- |
    | Programming Assignment  | 50%   |
    | Midterm Score           | 12.5% |
    | Final Score             | 37.5% |

3. determine letter grade using the overall score
    - 90 <= overall score <= 100: `A`
    - 80 <= overall score < 90: `B`
    - 70 <= overall score < 80: `C`
    - 60 <= overall score < 70: `D`
    - 0 <= overall score < 60: `F`

#### Output

Write the output to the standard output, which prints the overall score in the first line and the letter grade in the second line. There should be a **newline character** at the end of line. 
**Note:** `System.out.println()` method prints the text on the console and the cursor remains at the start of the next line at the console (i.e. it appends a newline character at the end of the line, so you **do not** need to add a newline character by yourself if you are using `System.out.println`). 
**Please follow the exact output format, or otherwise you will not get any credit.**

### Style
On this assignment, we will give you feedback on style but **not deduct points** for problems with style. For future assignments, we will be grading the following for style on all files you submit:


1. File header
2. Class header
3. Method header(s)
4. Inline comments
5. Proper indentation
6. Descriptive variable names
7. No magic numbers
8. Reasonably short methods (if you have implemented each method according to specification in this write-up, you’re fine). This is not enforced as strictly.
9. Lines shorter than 80 characters
10. Javadoc conventions (@param, @return tags, /** comments */, etc.)

A full style guide can be found [here](https://github.com/CaoAssignments/style-guide/blob/main/README.md) and a sample styled file can be found [here](https://github.com/CaoAssignments/style-guide/blob/main/SampleFile.java). If you need any clarifications, feel free to ask on Piazza.


### Example Input and Output

#### Example 1

- Input
    ```
    > java GradeCalculator
    5 90 100 91 95 84
    80 90
    ```
    First line: there are 5 programming assignment scores: 90, 100, 91, 95, and 84. 
    
    Second line: the midterm score is 80 and the final is 90. 
- Output
    ```
    89.75
    B
    ```
    $\frac{90 + 100 + 91 + 95 + 84}{5} \times 0.5 + 80 \times 0.125 + 90 \times 0.375 = 89.75$
    
    The overall score is in between 80 and 90, so the letter grade is B.


#### Example 2

- Input
    ```
    > java GradeCalculator
    8 90 85 82 98 95 87 65 84
    70 65
    ```

- Output
    ```
    76.0
    C
    ```
    $\frac{90 + 85 + 82 + 98 + 95 + 87 + 65 + 84}{8} \times 0.5 + 70 \times 0.125 + 65 \times 0.375 = 76.0$
    
    The overall score is in between 70 and 80, so the letter grade is C.

#### Example 3
- Input
    ```
    > java GradeCalculator
    3 110 99 90
    20 30
    ```

- Output
    ```
    invalid input
    ```
    *Note: As long as there is an invalid programming assignment score, we stop scanning exam scores. In this case, since the first PA score is above 100, print out the `invalid input` directly.*

#### Example 4
- Input
    ```
    > java GradeCalculator
    8 9 85 82 98 95 87 65 84
    -10 100
    ```

- Output
    ```
    invalid input
    ```

### Testing
Try the example inputs described above. Do you get the same results as their corresponding outputs? Now try some of your own inputs, do you get the results you would expect? 

*Note: The total programming assignment scores will always be fully divisible from the given $n$ (the number of PAs).*


### Submission & Grading
To turn in your work for this part, submit the following file(s) to Gradescope.
 - `GradeCalculator.java`


You can submit as many times as you want on Gradescope, and you will see the results right after each submission. **Only for this PA**, you are able to see all the test cases and results when you submit your assignment to Gradescope. It is your responsibility to test your program comprehensively. 

**Important:** Even if your code does not pass all the tests, you will still be able to submit your homework to receive partial points for the tests that you passed. **Make sure your code compiles on Autograder in order to receive partial credit. The name of the file needs to be `GradeCalculator.java`, otherwise no point.** 

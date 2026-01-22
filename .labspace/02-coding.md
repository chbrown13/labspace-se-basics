# Coding

Coding is writing instructions in a language computers understand. Software engineering is more than coding, however writing code is an important component. One of the first things you need to know to be a successful software engineer is a programming language. Developers should also be able to quickly learn new programming languages and transfer knowlede between languages, which can be very difficult to do.[^1] For example, the following scripts print `hello world!` in different programming languages:

```js no-run-button no-copy-button
    console.log( "hello world!" );
```

```python no-run-button no-copy-button
    print("hello world!")
```

```ruby no-run-button no-copy-button
    print 'hello world!'
```
```java no-run-button no-copy-button
class HelloWorld {
    public static void main(String[] args) {
        System.out.println("hello world!");
    }
}
```

## Write-Compile-Execute

In general, all of coding can be summed up by the **Write -> Compile -> Execute** process:

### Write
Also known as "Code" (code-compile-execute), this phase involves giving instructions to the computer by creating a program with source code. This program is:
– Written in a programming language (i.e. Java)
– Human-readable
– Written using a text editor or integrated development environment (IDE)

### Compile
Compilation translates the program from one language to another that can be understood by hardware. **Bytecode** is an intermediate language that has been compiled from source code and translated into low-level code. Some programming languages have distinct compilation steps (i.e. Java) while others compile during execution (i.e. Python). 

### Execution
The computer or a virtual machine reads and acts on the translated instructions from the written program. When either Compilation or Execution fails, return to Writing to update the source code.

## 📝 Activity

 Complete the program below in any programming language of your choice. You can create a new file by pressing **Ctrl + n** or selecting "New File" in the welcome page below.


> **Fizz Buzz**
> 
> Fizz buzz is a classic [children's game](https://en.wikipedia.org/wiki/Fizz_buzz) and [programming challenge](https://leetcode.com/problems/fizz-buzz/). Write a program that prints each number from 1 to 20. If the number is divisible by 3, print `Fizz` instead. If the number is divisible by 5, print `Buzz` instead. And if the number is divisible by 3 and 5, then print `FizzBuzz`. 

_Tips:_

* When you are finished, save the program with the name "fizzbuzz" in a source code file (i.e., `fizzbuzz.c` for C programs).You will need this later to submit for the workshop assignment.
* This is a simple activity to practice programming, not an interview. You will not be graded based on the quality of your code and are not expected to come up with the most efficient solution. 
* The labspace environment contains limited programming languages---so you may not be able to run your program within this labspace. (If desired, you may install language frameworks at your own leisure).
* Your program should generally include at least contain some type of loop structure, conditional statements, and print statements.

[^1]: Shrestha, et al. _"Here we go again: Why is it difficult for developers to learn another programming language?."_ Proceedings of the ACM/IEEE 42nd International Conference on Software Engineering (ICSE). 2020. [[pdf](http://nischalshrestha.me/docs/cross_language_interference.pdf)]
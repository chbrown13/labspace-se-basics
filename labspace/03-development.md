# Development Environments

## Shells

A shell is a computing environment where commands can be interpreted, evaluated, and its output displayed (_i.e._, an instance of a read–eval–print loop (REPL, see below)). A good shell provides access to a rich set of commands and allows simple programming of commands, which can be used to create powerful scripts and tools.

**But with great power comes great responsibility**. Commands and their options can be [terse, inconsistent, and difficult to learn](https://aws.plainenglish.io/why-learning-linux-is-so-frustrating-and-how-to-make-it-easy-a1f2c8d6a5cd). A steep learning curve often prevents novices from enjoying the eventual payoff. If you've hardly used a command line environment before, you might want to go review this more thorough tutorial: [software carpentry: shell-novice](http://swcarpentry.github.io/shell-novice/index.html)---this page is more of a discussion of common tasks and mistakes, advanced topics, and resources.

You may also want to reference the online book, [the Unix Workbench](https://seankross.com/the-unix-workbench/).

### Shell Basics

Depending on your operating system and desktop manager, you have many ways to open up a shell. There may even be several different choices for shell programs.

> *Tip*: This labspace is based in a Linux shell in your browser. For more details on using a shell environment on your own machine, see [Appendix A](#appendix-a-shells-outside-the-labspace).


### Commands

99% of the reason you use shells is to run useful commands. Some useful commands, including several used throughout this workshop, are provided below:

##### Essential commands

* **`ls`**: list content of a directory.
* **`cd`**: change directories to a new path.
* **`mkdir`**: make a new directory.
* **`pwd`**: output current directory
* **`cp`**: copy files
* **`rm`**: rm files
* **`touch`**: make a new file/update status**
* **`cat`**: output the contents of a file.
* **`head`**: output the first lines of a file.
* **`tail`**: output the last lines of a file.
* **`grep`**: search files for a key phrase.
* **`wget`**: retrieve file from the web.
* **`cut`**: extract output of a file (columns)
* **`awk`** and **`sed`**: Magic commands for extracting, searching, and transforming content.

##### Combining commands

Command can run sequentially or conditionally:

```bash no-run-button
command1 ; command2
(command1 ; command2) # in a sub-shell
command1 || command2  # do command2 only if command1 fails
command1 && command2  # do command2 only if command1 succeeds
```

## 📝 Activity

Complete the following to try using shell commands in the VS Code terminal for this labspace:

Try running this command that combines these shell commands.

```bash
echo "Hello World" > shells-test.txt && cat shells-test.txt
```

Now, try using the `||` operator. 

```bash
cat shells-test.txt || echo "backup plan"
```

See what happens in this case.

```bash
cat filedoesnotexist.txt || echo "backup plan"
```


## Integrated Development Environments

Integrated Development Environments (IDEs) enable software engineers to complete various activities related to writing a computer program. IDEs often provide a variety of features to support software development, including syntax highlighting, autocomplete, static analysis tools, debugging functionality, refactoring, multiple language support, integrations with git, code searching, and more...

Originally, software engineers wrote program code using [punched cards](https://en.wikipedia.org/wiki/Punched_card) in languages such as FORTRAN. You tried out an IDE in the previous activity. This Docker labspace is based on [VS Code](https://code.visualstudio.com/), one of the most popular and widely used coding editors. You will get the chance to try out two other development environments for yourself.

## REPL

A **Read-Eval-Print Loop (REPL)** is an interactive interpreter for programming languages. This concept originated with LISP, but many other languages today (Python, Ruby, JavaScript, Haskell, etc.) use REPL's to provide interactive programming language environments that bypass the compile stage of the write-compile-execute cycle. REPLs are useful for simple experimentation and developing quick functions with languages.

There are 4 components to REPL environments:

    * _Read_ reads in input from the keyboard
    * _Eval_ evaluates code passed to it
    * _Print_ formats and displays the output
    * _Loop_ continues until the REPL is terminated

## 📝 Activity

Complete the following to try out a REPL environment:

1. Open the terminal in the VS code editor (Select "Terminal" in the bottom panel or press **Ctrl+Shift+`**)
2. Type `node` into the terminal and press **Enter**.

```bash no-run-button
node
```

3. This will enter you into the REPL environment. The following script will print "Hello CS3704!":

```bash no-run-button
console.log("Hello CS3704!");
```

4. This should print the `Hello CS3704!` message to the console (in addition, you may see an `undefined` message indicating the `console.log` function returns **`undefined`**.


5. The command below will create a function `add` that adds two numbers input as parameters:

```bash no-run-button
const add = (a, b) => { return a + b }
```

6. In the terminal, you can now use this function. Type `add(x, y)` to add two given numbers _x_ and _y_.

Ex) `add(37,04)` should return `41`

7. Press **Ctrl+D** to exit the REPL environment.

## VI 
Before the modern coding editors and cloud-based IDES, software engineers wrote code using editors in the console or terminal. One example is `vi`, an open source terminal-based development environment referred to as "[the programmer's editor](https://www.vim.org/about.php)". Vim (Vi Improved) is a more configurable version offering syntax highlighting, plugins, and more advanced commands. This coding environment is minimal, and it is a common joke in software engineering communities that `vi` is difficult to exit out of...

<img src="/images/vi1.jpg" width="400" height="400" />

<img src="/images/vi2.png" width="400" height="400" />

## 📝 Activity

 Complete the following activities to practice using the vi coding environment. A brief reference guide is also provided at the bottom of this document.

##### **vi Practice**

1. Open the terminal in the VS code editor (Select "Terminal" in the bottom panel or press **Ctrl+Shift+`**)
2. Type "vi" into the terminal and press **Enter**. This will open the vi coding editor.

```bash no-run-button
vi
```


3. Press "i" to enter Insert Mode. 
4. Once in Insert mode, you can type and navigate as you would in a normal text editor. To use print statements in JavaScript, you would use the `console.log(" ");` command. Add a line to this document that prints out a relevant message (i.e., "Practicing using vi") in the file.
5. To exit, press **Esc** then type `:wq practice.js` to save the file under the filename `practice.js` and exit. Congrats---you successfully exited vi! 🎉 To run the file in the terminal, use the following command:

```bash no-run-button
node practice.js
```

---

##### **Reflection**
1. Open a new text file in the vi editor called `reflection.txt`. 

```bash no-run-button
vi reflection.txt
```

2. Go into insert mode to add which development environments or IDEs you typically use for programming, and explain why.
3. Save the file and exit the vi editor. Use the following command to display the content of your file in the terminal.
```bash no-run-button
cat reflection.txt
```

4. Open the file in the vi editor to add your responses to the following questions. Use the reference table below to help navigate and edit the file. Please keep your responses brief (no more than 2-3 sentences each).

(a) What development environment or IDE do you typically use for programming? (answered in Step 2)

(b) Do you have experience using vi or other terminal based editors?; 

(c) What are the advantages/disadvantages of using terminal-based editors for coding in practice? 

5. Save the file and exit the vi editor.

### Reference Table

| Action | Key(s) |
| :--- | :--- |
| **Move Cursor** | `h` (left), `j` (down), `k` (up), `l` (right) |
| **Insert Text** | `i` |
| **Exit Insert Mode** | `Esc` |
| **Delete Character** | `x` |
| **Delete Line** | `dd` |
| **Undo** | `u` |
| **Save & Quit** | `:wq` |
| **Quit without Saving** | `:q!` |

---

## Appendix A: Shells Outside the Labspace

> You don't need any of this to complete the workshop — everything below is for when you're working on your own machine instead of in this container.

### Accessing and Using Shells

* **Mac**: you can run the Terminal in Applications and pin to your Dock.

* **Windows**: You access a shell in several ways. You can right click on the Windows Icon in the Task Bar and open a terminal window. You can also type in the name of the shell program in the search bar (e.g., Cmd/Powershell). 

> *Tip*: IDES, such as VS Code provide easy access to a terminal (View ⇨ Terminal).

### Deciding on a Terminal/Shell for Windows

In windows, you can use Cmd, Powershell, or emulated shells, such as Bash for Git, or Bash with [Windows Linux Subsystem (WSL)](https://learn.microsoft.com/en-us/windows/wsl/about). 

`Cmd` is tried and true, and if you [made windows awesome](setup/configure-shell.md), will mostly what you want to do. The downsides are that interactions such as copy/paste are a little clunky. However, if open up a terminal with Cmd through Code, then this problem is mostly eliminated. `Powershell` is a powerful shell, with great scripting support. However, the syntax is esoteric and inconsistent with any other shell you may use. For example, running common linux commands like `cd ~ && ls` does not work in Powershell.

Enumlated shells are useful for getting a _linux-like_ experience in Windows. Unfortunately, there are **many downsides to using emulated shells**. One downside is that you may be limited in accessing other executables/environments on windows. 
For example, with `WSL`, you are actually running commands inside a small virtual machine, which limits your ability to run commands from windows. In general, using `WSL`, will turn on Hyper-V, which essentially breaks virtualization for tools, such as VirtualBox. In `Git Bash`, node packages and environment settings you setup will not work as expected when running in Cmd/etc. Furthermore, you never truly escape Windows, for example, Windows style newline endings `'\r\n'` may exist in files you edit, which will break bash scripts. Another common problem is that when you install packages, you will often get libraries for linux binaries, which then will not work when running outside of the emulated shell.

As a result, emulated shells seem helpful, but often create more problems than they solve.

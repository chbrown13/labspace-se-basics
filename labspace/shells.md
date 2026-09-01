# Shells

A shell is a computing environment where commands can be interpreted, evaluated, and its output displayed (i.e., an instance of a read–eval–print loop (REPL)). A good shell provides access to a rich set of commands and allows simple programming of commands, which can be used to create powerful scripts and tools.

**But with great power comes great responsibility**. Commands and their options can be [terse, inconsistent, and difficult to learn](http://www.pgbovine.net/command-line-bullshittery.htm). A steep learning curve often prevents novices from enjoying the eventual payoff. If you've hardly used a command line environment before, you might want to go review this more thorough tutorial:
[software carpentry: shell-novice](http://swcarpentry.github.io/shell-novice/index.html)---this page is more of a discussion of common tasks and mistakes, advanced topics, and resources.

You may also want to reference the online book, [the Unix Workbench](https://seankross.com/the-unix-workbench/).

## Shell Basics

Depending on your operating system and desktop manager, you have many ways to open up a shell. There may even be several different choices for shell programs.

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

### Commands

99% of the reason you use shells is to run useful commands.

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

```bash
command1 ; command2
(command1 ; command2) # in a sub-shell
command1 || command2  # do command2 only if command1 fails
command1 && command2  # do command2 only if command1 succeeds
```

Try running this command that combines these shell commands.

```bash|{type: 'command'}
echo "Hello World" > shells-test.txt && cat shells-test.txt
```

Now, try using the `||` operator. 

```bash|{type: 'command', }
cat shells-test.txt || echo "backup plan"
```

See what happens in this case.

```bash|{type: 'command', failed_when: "!stdout.includes('backup plan')"}
cat filedoesnotexist.txt || echo "backup plan"
```

##### Command I/O

The UNIX shell commands push data from sources through filters along pipes. Normally, each command runs as a process and reads and writes data the following way:

* **Standard input (stdin)**: get information from keyboard.
* **Standard output (stdout)**: write information as output to console.
* **Standard error (stderr)**: write error information as output to console.

Pipes and redirects change stdin and stdout from default sources. For example, we can change the stdin of a process to be piped from the output of another process. Or rather than printing to the console, we can get a process to write to a file.

```bash
command              # default standard in and standard out
command < inputFile  # redirect of inputFile contents to command as standard in
command > outputFile # redirect command output to outputFile as standard out
command1 | command2  # pipes output of command1 as standard in to command2
```

**Neat trick**: Copy the value of a file into your clipboard!

Windows: `clip < file.txt` Mac: `pbcopy < file.txt` 

```bash|{type:'command', platform: 'darwin'}
pbcopy < ~/.ssh/id_rsa
```

```bash|{type:'command', platform: 'win32'}
clip < %HOME%/.ssh/id_rsa
```

## Activity: Data Wrangling with bash

Download data with `wget`.

```bash|{type:'command', stream: true}
wget -nc https://s3-us-west-2.amazonaws.com/producthunt-downloads/ph-export--2016-04-01.tar.gz --show-progress --progress=bar:force 2>&1
```

Create a directory to store the tar file contents

```bash|{type:'command'}
mkdir product-hunt 
```

Extract the archive and verify csv files exist inside the product-hunt folder.

```bash|{type:'command'}
tar -zxvf ph-export--2016-04-01.tar.gz -C product-hunt/
ls product-hunt/
```

Data wrangling. 

List the column headers inside the "users.*.csv" file

```bash|{type:'command'}
head -n 1 product-hunt/users--2016-04-01_14-36-26-UTC.csv
```

Extract a column of text from a file, using `cut`, skip over first line with `tail`, and then preview first 10 rows with `head`.

```bash|{type:'command'}
cut -f 4 -d ';' product-hunt/users*.csv | tail -n +2 | head 
```

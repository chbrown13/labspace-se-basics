# Integrated Development Environments

Integrated Development Environments (IDEs) enable software engineers to complete various activities related to writing a computer program. IDEs often provide a variety of features to support software development, including syntax highlighting, autocomplete, static analysis tools, debugging functionality, refactoring, multiple language support, integrations with git, code searching, and more...

Originally, software engineers wrote program code using [punched cards](https://en.wikipedia.org/wiki/Punched_card) in languages such as FORTRAN. You tried out an IDE in the previous activity. This Docker labspace is based on [VS Code](https://code.visualstudio.com/), one of the most popular and widely used coding editors. You will get the chance to try another out for yourself.

## VIM 
Before the modern coding editors and cloud-based IDES, software engineers wrote code using editors in the console or terminal. One example is `vi`, an open source terminal-based development environment referred to as "[the programmer's editor](https://www.vim.org/about.php)". Vim (Vi Improved) is a more configurable version offering syntax highlighting, plugins, and more advanced commands. This coding environment is minimal, and it is a common joke in software engineering communities that `vi` is difficult to exit out of...

<img src="resources/imgs/vi1.jpg" width="400" height="400" />
<img src="resources/imgs/vi2.png" width="400" height="400" />

## 📝 Activity

 Complete the following activity to practice using the vi coding environment. A brief reference guide is also provided at the bottom of this document.

> **`vi`**

1. Open the terminal in the VS code editor (Select "Terminal" in the bottom panel or press Ctrl+Shift+`)
2. Type "vi" into the terminal. This will open the vi coding editor.

```bash
vi
```


3. Press "i" to enter Insert Mode. 
4. Once in Insert mode, you can type and navigate as you would in a normal text editor. Add the line "# CS5704 SE Basics Workshop" to the top of the file.
5. To exit, type ":wq README.md" to save the file under the filename README.md and exit. Congrats---you successfully exited vi!
6. Open the README file in the vi editor to add your name and PID to the document.

```bash
vi README.md
```

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
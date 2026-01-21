# Integrated Development Environments

Integrated Development Environments (IDEs) enable software engineers to complete various activities related to writing a computer program. IDEs often provide a variety of features to support software development, including syntax highlighting, autocomplete, static analysis tools, debugging functionality, refactoring, multiple language support, integrations with git, code searching, and more...

Originally, software engineers wrote program code using [punched cards](https://en.wikipedia.org/wiki/Punched_card) in languages such as FORTRAN. You tried out an IDE in the previous activity. This Docker labspace is based on [VS Code](https://code.visualstudio.com/), one of the most popular and widely used coding editors. You will get the chance to try another out for yourself.

## VI 
Before the modern coding editors and cloud-based IDES, software engineers wrote code using editors in the console or terminal. One example is `vi`, an open source terminal-based development environment referred to as "[the programmer's editor](https://www.vim.org/about.php)". Vim (Vi Improved) is a more configurable version offering syntax highlighting, plugins, and more advanced commands. This coding environment is minimal, and it is a common joke in software engineering communities that `vi` is difficult to exit out of...

<img src="/.labspace/images/vi1.jpg" width="400" height="400" />

<img src="/.labspace/images/vi2.png" width="400" height="400" />

## 📝 Activity

 Complete the following activities to practice using the vi coding environment. A brief reference guide is also provided at the bottom of this document.

##### **vi Practice**

1. Open the terminal in the VS code editor (Select "Terminal" in the bottom panel or press **Ctrl+Shift+`**)
2. Type "vi" into the terminal. This will open the vi coding editor.

```bash
vi
```


3. Press "i" to enter Insert Mode. 
4. Once in Insert mode, you can type and navigate as you would in a normal text editor. To use print statements in JavaScript, you would use the `console.log(" ");` command. Add a line to this document that prints out a relevant message (i.e., "Practicing using vi") in the file.
5. To exit, press **Esc** then type `:wq practice.js` to save the file under the filename README.md and exit. Congrats---you successfully exited vi! 🎉 To run the file in the terminal, use the following command:

```bash
node practice.js
```

---

##### **Reflection**
1. Open a new text file in the vi editor called `reflection.txt`. 

```bash
vi reflection.txt
```

2. Go into insert mode to add which development environments or IDEs you typically use for programming, and explain why.
3. Save the file and exit the vi editor. Use the following command to display the content of your file in the terminal.
```bash
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
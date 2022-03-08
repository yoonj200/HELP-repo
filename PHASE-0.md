# **PHASE 0**

## **CLI (Command Line Interface)**
------
`CLI` is a text-based conversation with the computer in which we type commands for:
- viewing, handling, and manipulating files on your computer
- launching software
- working with devices like printers or networks

`Terminal` programs emulate CLIs (Mac = Terminal, WSL = Ubuntu). `Shells` take input and ask CPUs to work (`bash` and `zsh` are `shell`s used by Unix systems (like Mac OSX and Linux)). 

Navigating through a directory on Unix systems 
``` bash
/parentdirectory/subdirectory/another/subdirectory
```
| Description                               | Terminal Command            |
| ----------------------------------------- |-----------------------------|
| Identify logged-in username               | `$ whoami`                  |
| Identify current working directory        | `$ pwd`                     |
| Navigate up one directory                 | `$ cd ..`                   |
| Navigate to home directory                | `$ cd ~`                    |
| Navigate up current directory             | `$ cd .`                    |
| Navigate to a directory                   | `$ cd [folder]`             |
| List all files in working directory       | `$ ls`                      |
| List all files in any directory           | `$ ls pathname`             |
| **List all files in more detail           | `$ ls -l pathname`          |
| Create a directory                        | `$ mkdir [name]`            |
| Move file from current dir to another dir | `$ mv filename ./dir1`      |
| Rename file or directory                  | `$ mv original_program.rb renamed_program.rb` |
| Move and rename file or dir               | `$ mv temp_download.gif ~/Desktop/cats_with_weapons/ninja_cat.gif` |     
| Create a copy of a file                   | `$ cp letter_to_mom.txt letter_to_mom-2019-02-15.txt1` |  
| Copy a directory and its file contents    | `$ cp -r february_cat_gifs ~/Desktop/vital_media_files` |
| Create an empty file                      | `$ touch hello_world.rb`    |
| Remove (delete) a file                    | `$ rm hello_world.rb`       |
| Remove (delete) a directory               | `$ rm -r ~/Desktop/pathname`|
| Print file contents                       | `$ cat filename.rb`         |
| Trigger  default action of file type      | `$ open filename.rb`        |
| Print a string in the terminal            | `$ echo "Hi world"`         |
| Redirect text into a file                 | `$ echo "I'm printing to the screen" >> my_file.txt` |
| ***Assign paths to `PATH` variable        | `$ echo $PATH`              |
| Show the program's version                | `$ cd /Users/kellyegreene/.rvm/rubies/ruby-2.7.4/bin` |
|                                           | `$ ./ruby -v`               |
| OR                                        | `$ /Users/kellyegreene/.rvm/rubies/ruby-2.7.4/bin/ruby -v` |
| Look up bash documentation (ex: on `ps`)  | `$ man ps`                  |

** Flags with commands are denoted by a `"-"`.
- `-l` = human readable format
- `-a` = all information (including hidden files) 

*** Directories whos names are listed in the `PATH` variable can have their programs run without having to `cd` to the directory (OR provide a long absolute path).

**NOTE**: Use Tab to auto-fill terminal commands.

## **Git**
------
**Version Control System (VCS)** describes a whole group of software (i.e. Git, Mercurial, Subversion, etc.)
  - Automatically creates a backup of your work
  - Provides easy way to undo mistakes and restore previous version(s) of work
  - Documents changes, including a **log** of what's changed with messages explaining why it was changed
  - Keep file names and hierarchies consistent and organized
  - Branch work off into multiple "sandboxes" that can be experimented with but won't impact each other
  - Collaborate with others without disturbing each other's or our own work

**Terminology**
  - **repository** (**repo**): directory of files tracked by Git
  - **track**: Git *tracks* files and notes any changes to those files
  - **diff**: all the changes that happened in it since the last commit
  - **commit**: committing a diff to the repo's history (`commit` command)
    - You are asked to write a "log" message that describes what happened in the diff
  - **log**: record of what happened in each commit
  - **log/remote**: the repo on our personal system is the local repo, which is cloned from a remote source
  - **default branch**: repo can support multiple branches ("sandboxes"); creating a Git repo automatically puts you on the default branch (`main` or `master`)
  - **branch**: combined history of all changes of all files in the repo

**How to Initialize a Git Repo**
1. Initialize the directory as a Git repository.
```bash
$ mkdir my-git-project
$ cd my-git-project
$ git init
```
**Check the Status of a Repository**
```bash
$ git status
```
**Create a `README.md` File**
```bash
$ touch README.md
```
**Track File Changes**
```bash
$ git add README.md
$ git status
On branch main

No commits yet

Changes to be committed:
(use "git rm --cached <file>..." to unstage)

  new file:   README.md
```
**Create a Commit and Apply a Commit Message**
```
$ git commit -m "Initial commit"
```

**Copy a Repository to Your Local Machine**
1. Navigate to the React repository
2. Click the green "Code" button and use `SSH` as the URL type
3. Copy to the clipboard and run the `git clone` command (right-click to paste into terminal)
```bash
$ git clone your-copied-github-url
```
**List Remotes**
1. `cd` into `react`
2. `remote` is the default name Git gives to the remote you cloned from
3. Prove that `origin` name has relationship to the address GitHub gave us 
```bash
$ git remote show origin
* remote origin
  Fetch URL: git@github.com:facebook/react.git
```
**Duplicate Other Organizations' Repos into Your Own via GitHub with the "Fork" Button**

**Create a Remote Repository on GitHub**
1. Go to [github.com/new](https://github.com/new) while logged into GitHub.
2. Enter Repository name.
3. Make sure the SSH option is selected before copying to clipboard.

**Connect a Local Repository to a Remote Repository**
1. Create a folder for our repo. In the terminal, navigate to the directory where you store your code and type `mkdir my_new_directory`.
2. Navigate into the folder and open in VS Code. 
3. Create a README.md file.
4. Type content into README.md via VS Code or use terminal (echo "This is my readme file"> README.md).
5. Initialize local repository.
6. Type `git add README.md` to stage the new README.md file so it will be tracked by git. 
7. Type `git commit -m "Initialize git"`. 

**Set the Destination of a Repo** 

The repo path is a long bunch of technical words; create a new remote with a short name of `origin` (the default remote short name is `origin`).

Paste the Git info copied from GitHub into the terminal: 
```
$ git remote add origin your-copied-remote-repository-url
```
Now you _**push the code**_.
``` bash
$ git remote -v
View existing remotes
origin git@github.com:OWNER/REPOSITORY.git (fetch)
origin  git@github.com:OWNER/REPOSITORY.git (push)
```
**Send Code to the Remote Repo with `git push`**

Send the latest work to the remote. You can find out what the default branch for your current repository is by running: 
```bash
$ git branch --show-current
```
These commands push code to GitHub depending on if your default branch name is `main` or `master`:
```bash
$ git push -u origin main
```
```bash
$ git push -u origin master
```
**An Aside and a Small Shortcut**

To add, commit and push work you've done locally, run these commands:
```bash
$ git add .
$ git commit -m "commit message"
$ git push
```
The following shortcut combines adding all tracked files and committing by using an additional option flag `-a` with the commit command: 
```bash
$ git commit -am "commit message"
$ git push
```

## **HTML**
------

## **CSS**
------

## **Programming as Conversation Part 1: Expressions**
------

## **Programming as Conversation Part 2: Statements**
------

## **Programming as Conversation Part 3: Bundling Expressions and Statements into Functions**
------

## **Working with Data Structures**
------
**`Data structures`** are a means for associating and organizing information. 

`String`s and `number`s are scalar data types (they can be put on a scale).
A `collection data type` holds multiple pieces of data and allows us to talk about the collection as an abstraction (**_not_** scalar).
### **Arrays**
`Array`: collection holding multiple pieces of data under a single name (ordered list)
``` javascript
const myArray = [
  "A string", // Array element (member)
  "Another string",
  7
];
```
- `Array index`: a number that identifies each element
- Some languages won't allow arrays to include elemnents of multiple types (i.e. C, C++, Java, Swift, etc.), while others do allow it (JavaScript, Python, Ruby, Lisp, etc.). 

Find the number of elements in an array using `.length` method.
```javascript
const myArray = ["This", "array", "has", 5, "elements"];

myArray.length;
//=> 5
```
### **Bracket Notation** 
**Accessing an element** uses bracket notation like this: `nameOfArray[index]`
```javascript
const winningNumbers = [32, 9, 14, 33, 48, 5];
// => undefined

winningNumbers[0];
// => 32

winningNumbers[3];
// => 33
```
**Accessing the last element**

Updating the Value of an Element

Nested arrays

**Array Methods**

**Mutability**


### **Objects**
`Object`: a collection data type holding multiple pieces of data under a collected name whose members can be read and updated by using a key instead of an index. 
```javascript
const englishBandsByCity = {
  liverpool: "The Beatles",
  manchester: "The Smiths",
  coventry: "Delia Derbyshire and the BBC Radiophonic Band",
  london: "Ziggy Stardust and the Spiders from Mars",
};
```
- `Object keys`: identifiers, usually a symbol or a string
- `Object values`: value returned from asking an object what a given key points to

**Colleciton Data Structures can be Nested in each other**
```javascript
const englishMusicByCity = {
  manchester: [
    {
      bandName: "The Smiths",
      memberNames: ["Morrissey", "Johnny", "Andy", "Mike"],
    },
    {
      bandName: "Joy Division",
      memberNames: ["Peter", "Stephen", "Bernard", "Ian"],
    },
  ],
};
```


## **DOM Manipulation**
------
**DOM (Document Object Model)** consists of using Javascript to:
1. Ask DOM to find or select HTML element(s) in rendered page
2. Remove and/or insert element(s)    
3. Adjust a property of selected element(s)

DOM is created when page loads from HTML/CSS/JavaScript that the web server provides to browser
1. (Google Chrome) Open a tab and navigate to any webpage
2. Add view-source: to front of URL to display all the source HTML of the page
3. The browser reads this HTML, along with CSS and JavaScript defined in `<script>` or `<link>` tags, to create the DOM inside the browser 
    -  At this point, nothing is displayed on the screen 
    - The time when nothing is displayed is very brief so our human eyes never really catch it
4. The browser uses the HTML to create a "middleman" that is then used to display the structured and styled content

`Ctrl + Shift + I` opens up Chrome DevTools for any webpage.

## **JavaScript Events**
------
JavaScript "listens" for events in the broswer.

**Mouse Click** 
-  JavaScript recognizes a single click on an element and changes its styling to highlight it
-  It recognizes a double-click on an element and opens a zoomed-in view of it

**Key Press**
- Currently, JavaScript includes `keydown` and `keyup` events (`keypress` has been deprecated)
- EX) A game program listens for `keydown` events and, if the space bar was pressed, makes the character jump 

**Form Submission**
- User submits a form, `submit` event is fired; HTML pages often use submit buttons to submit a form to a server

**Other Events**
- More complicated applications require you to handle and trigger work on more events, including but not limited to `scroll`, `mouseenter` and `mouseleave`, `focus`, `blur`, and `onchange`. 
- Not all JavaScript events are supported by all browsers!

## **Project Mode**
------
### **Hosting a Website on GitHub Pages**
Any repository on GitHub can be published as a website
- By default, it will take a repository's `README.md` file and convert it to an HTML page
- If there's an `index.html` file in the repository beside the `README.md`, the HTML file will be displayed isntead

#### 1. Create a Local Repository File

    - Navigate to a good location in the local repository and create a fold##er 
    ``` bash 
    $ mkdir example-repository
    $ cd example-repository
    ```
#### 2. Create a Remote GitHub Repository

    - Go to https://github.com/ and click the + icon
    - Choose `New repository`
#### 3. Add The New Remote to The Local Repository

- You can do it on the command line like this: 
    ``` bash
    echo "example-repository" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git branch -M main
    git remote add origin git@github.com:yourname/example-repository.git
    git push-u origin main
    ```  
1. `echo "# example-repository" >> README.md` creates a `README.md` file and adds some markdown.
2. `git init` initializes a local repository in the folder you're currently in on the command line
3. `git add README.md` stages newly created `README.md` file, getting it ready to be committed
4. `git commit -m "first commit"` creates repository's first commit, preserving newly created `README.md` file in repository's history
5. `git branch -M main` ensures default repository branch is set to main
6. `git remote add origin git@github...` associates remote GitHub repository with new local repository. This association is given the name origin.
7. `git push -u origin main` pushes the commit we just created to the remote repository.
#### 4. Build An `index.html` File with some Basic Content

In the terminal, create an `index.html` file
``` bash
$ touch index.html
```
In the text editor: 
``` html
<!DOCTYPE html> <!-- Indicates HTML -->
<html lang="en"> 
  <head>
    <title>My Website</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```
#### 5. Add, Commit and Push the New Content to the Remote
``` bash
$ git add index.html
$ git commit -m "create basic HTML file"
$ git push
``` 

#### 6. Enable GitHub Pages in the remote repository's settings

1. In the GitHub repository, click the **Settings** tab, then navigate to **GitHub Pages** section. 
2. Set the **Source** to the default branch (drop-down that says "None" -> `main`)
3. **Save**.

#### 7. Check out the published site

Navigate back to **GitHub Page** settings. Click on the URL `<your-username>.github.io`.

#### 8. Continue building out the HTML and add CSS and JavaScript files

##### Troubleshooting

- Double check GitHub Page settings and make sure `main` is set as source
- If settings are correct, review `index.html` file for typos or syntax errors
- Create a new repository again, but DON'T create an HTML file. Instead, only create a `README.md` file with some example text and use GitHub Pages to publish the repo. 
    - Once the Readme file is displaying as a GitHub Page, start going through the HTML file creation process again. 

##### Continuing To Build
GitHub Pages published websites will automatically update as you make changes to the repository files and push them to your remote
1. Create or modify a file
2. Add, commit, and push it to your remote
3. Wait a few minutes for GitHub to update your page
4. Visit your GitHub Page to see the newest changes
##### Add & Connect a CSS File
1. Create a CSS file alongside the `index.html` file.
``` bash
$ touch style.css
```
2. Create a basic style rule and save it before connecting to HTML. 
```
body {
    background: blue;
}
```
3. Connect the CSS file to the `index.html` by modifying the HTML `head` to include a `link` tag:
``` html
<head>
  <link rel="stylesheet" href="style.css" />
  <title>My Website</title>
</head>
```
4. Save the HTML file and open it locally (should be blue now).
5. Add both files before committing: 
``` bash
$ git add style.css
$ git add index.html
$ git commit -m "add style.css, connect to index.html"
$ git push
```

##### Add & Connect a JavaScript File
```
$ touch script.js
```
1. Add some basic code so you can see something once you've connected the JS file to the HTML file: 
``` javascript
const h2 = document.createElement("h2");
h2.textContent = "This content added by JavaScript";
```
2. The following code adds this `h2` element to the `body` element in the DOM:
```javascript
document.querySelector("body").appendChild(h2);
```
3. Save and switch to `index.html`. Connect `script.js` to HTML by adding a `script` tag inside `body`:
```html
<script src="script.js"></script>
```
4. The HTML file should look like this now:
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="stylesheet" href="style.css" />
    <title>My Website</title>
  </head>
  <body>
    <h1>Hello World!</h1>
    <script src="script.js"></script>
  </body>
</html>
```
5. Add, commit and push changes. Remember to add both files before committing. 
``` bash
$ git add script.js
$ git add index.html
$ git commit -m "add script.js, connect to index.html"
$ git push
```
### **Project: Build a Personal Website**

#### Recommended Workflow
1. Write some HTML, CSS or JavaScript
2. Refresh browser to see changes
3. Adjust code and repeat until satisfied
4. Move on to next task and repeat process

#### Professional Git Development Workflow

This is NOT what to do
- Commit 1: "Initialize Repository"
- Commit 2: "Finish website"

Here's what to do:
- Commit 1: "Initialize Repository"
- Commit 2: "Add basic HTML, CSS and JavaScript files"
- Commit 3: "Create initial HTML content"
- Commit 4: "Add CSS rules"
- Commit 5: "Fix syntax issue in HTML"
- Commit 6: "Finish bio/about section"
- Commit 7: "Add JS event listeners" 
- etc...
- Commit 22: "Adjust styling for new HTML layout"
- Commit 23: "Finish website"

Each commit addresses a small, often _`singular`_ task.

### **Looping vs Iteration**
**`Looping`**: executes a set of statements **_repeatedly until a condition is met_**. 
-  Great for when something needs to be done a specific number of times (`for` loop) or unlimited times until the condition is met (`while` or `do while` loop).

**`Iteration`**: executes a set of statements **_once for each element in a collection_**. We can accomplish this with a `for` loop:
```js
let myArray = ['a', 'b', 'c', 'd', 'e', 'f', 'g'];

for (let i = 0; i < myArray.length; i++) {
  console.log(myArray[i]);
}
```

or with a `while` loop:

```js
let myArray = ['a', 'b', 'c', 'd', 'e', 'f', 'g'];

let j = 0;

while (j < myArray.length) {
  console.log(myArray[j++]);
}
```

Neither is very pretty. The `for...of` statement gives us a better way.

### **`for...of`**

Using `for...of`, the code above becomes:

```js
const myArray = ['a', 'b', 'c', 'd', 'e', 'f', 'g'];

for (const element of myArray) {
  console.log(element);
}
```
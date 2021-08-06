# Contribution Guide  
I'm very glad that you are interested in contributing to the project!  
There are many ways to contribute to the project. Here are some examples:  
* Adding more commands to the terminal emulator  
* Adding documentation and guides to the Wiki or the helper window  
* Improving the codebase  
* Spreading the word around  
  
**Note:** In order to contribute to the Terminal or the Wiki, you need to have a [Github account](https://github.com/signup).  
## Overview   
1. Fork the [Project](https://github.com/taha-mcp/interactive-terminal)
2. Make your modifications (Don't know what to modify? Check the [Contribution Ideas](Contribution%20Ideas))
3. Make a [pull request](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) to have your modifications added to the repository.  

Full details are found below  
## Detailed contribution guide  
### Adding more commands
I tried to make this task as easy and hassle-free as possible so that you can easily add as many commands as you like!
After forking the repository, navigate to the `/assets/js` folder and open `main.js`. This file contains all the backend and logic code.  
At the top of `main.js` you see an array called `Command Array`. It should look something like this (hopefully with more commands):
```javascript
var CommandArary = [
    ["help", "HelpCommand", "Lists all available commands"],
    ["echo", "EchoCommand", "Echoes a word or sentence"],
    ["clear", "ClearCommand", "Clears all the text in the terminal window"],
    ["sudo", "SudoCommand", "Run a command with admin privileges"],
    ["apt", "AptCommand", "Application package manager"]
];
```
Adding a new command is as easy as adding a row to a table. As an example, we want to add the `ifconfig` command to return the user's public ip-address. Treat the command array as a 3 column spreadsheet. The first column is the actual command the user needs to enter. The second column is the backend function that is called when the respective command is entered. And the third column is a short description of the command which is displayed when the user enters the help command in the terminal.  
So with that said, let's call the command `ifconfig`, the backend function `IpCommand`, and the description `Display public ip-address`. Putting that into the array, it would look like this:
```javascript
["ifconfig", "IpCommand", "Display public ip-address"]
```
After adding it to the array, it should look like this:
```javascript
var CommandArary = [
    ["help", "HelpCommand", "Lists all available commands"],
    ["echo", "EchoCommand", "Echoes a word or sentence"],
    ["clear", "ClearCommand", "Clears all the text in the terminal window"],
    ["sudo", "SudoCommand", "Run a command with admin privileges"],
    ["apt", "AptCommand", "Application package manager"],
    ["ifconfig", "IpCommand", "Display public ip-address"]
];
```
**Note:** Keep in mind that the array file is comma seperated. There should be a comma between all the array elements.  
  
Now scroll to the bottom of the code and create a function with the name you defined earlier. 
```javascript
function IpCommand() {
    
}
```
The fucntion is currently empty. Now in order for something to happen, we need to code some stuff to get the user's IP address and display it. To get the user's public ip address, we could use a service like [ipinfo](https://ipinfo.io/). We just add the snippet to the terminal so at the end the function would look like this:
```javascript
function IpCommand() {
    // Snippet provided by Ipinfo
    $.get("http://ipinfo.io", function(response) {
        //Native method to print a text to the terminal
        WriteToTerminal(response.ip);
    }, "jsonp");
}
```
And we are done! Simple as that we added a new command to the terminal emulator! Now all you need to do is do a pull request to have your addition added to the main repository.  
As a matter of fact, this command shown in this example has not been implemented in the terminal emulator yet! You can be the first person to add it!

### Improving documentation
This process is even easier than adding a new command! The process is akin to Wikipedia. In this wiki, at the top of everypage, you will see the following buttons: **Add new | Edit | Delete | History | Source | Add new post** You can esaily click on each of these buttons to edit a page or add new content. It's very simple and easy. This wiki is made using Markdown and Github. Everything in this wiki has been written using Markdown. Chances are, you are already familar with markdown. Take a look at this [Markdown cheatsheat](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet). It is very useful! Don't forget to make a pull request after making a modification.
### Improving codebase
All of the backend code of the terminal emulator is contained in `assets/js/main.js`. Everything is written is raw Javascript but I am not against JQuery. I still prefer raw JavaScript over it but still JQuery 3.5.1 already exists in the main branch.  
The code could use a lot of improvements all across the board. Any help is greatly appreciated!
### Spreading the Word
Tell your firends, tell your family, tell your local news paper about it, show it to people who want to get into linux but do not have a technical background and are afraid of the infamous Linux Terminal. Or you could just use it to play around and test things out! Get in touch with us via the [forum](https://github.com/taha-mcp/interactive-terminal/discussions). We'd love to hear from you!

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
2. Make your modifications
3. Make a [pull request](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) to have your modifications added to the repository.  

Full details are found below  
## Detailed contribution guide  
### Adding more commands
I tried to make this task as easy and hassle-free as possible so that you can easily add as many commands as you like!
After forking the repository, navigate to the `/assets/js` folder and open `main.js`. This file contains all the backend code. All of the logic code can be seen in `main.js`.
At the begining of the code you see an array called `Command Array`. It should look something like this:
```javascript
var CommandArary = [
    ["help", "HelpCommand", "Lists all available commands"],
    ["echo", "EchoCommand", "Echoes a word or sentence"],
    ["clear", "ClearCommand", "Clears all the text in the terminal window"],
    ["sudo", "SudoCommand", "Run a command with admin privileges"],
    ["apt", "AptCommand", "Application package manager"]
];
```
Adding a new command is as easy as adding a line. As an example, we want to add the `ifconfig` command to return the user's public ip-address. Treat the command array as a 3 column spreadsheet. The first column is the actual command the user needs to enter. The second column is the backend function that is called when the respective command is entered. And the third column is a short description of the command which is displayed when the user enters the help command in the terminal.  
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
The fucntion is currently empty. Now in order for something to happen, we need to code some stuff to get the user's IP address and display it. To get the user's public ip address, we could use a service like [ipify](https://www.ipify.org/). We just add the snippet to the terminal so it would look like this:
```javascript
// Snippet provided by Ipify
<script type="application/javascript">
  $(function() {
    $.getJSON("https://api.ipify.org?format=jsonp&callback=?",
      function(json) {
        //This is the native method of priting a text to the terminal
        WriteToTerminal(json.ip);
      }
    );
  });
</script>
```
And we are done! Simple as that we added a new command to the terminal emulator! As a matter of fact, this command shown in this example has not been implemented in the terminal emulator yet! You can be the first person to add it!

### Improving documentation
### Improving codebase
### Spreading the Word

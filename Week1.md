Lab Report Week 1
<br> ''' cd ''' 
<br> This is a command that changes the working directory. 
<br>
![Image](cdnoarg.png)
<br>
When we have no arguments passed in, the working directory was changed to the home directory.
![Image](cd1arg.png)
<br>
With a directory argument, the new working directory was changed to the directory passed as an argument.
![Image](cd2arg.png)
<br>
When a file path was passed in as an arguemment, an error message was thrown saying that the file wasn't a directory. The cd command can only accept directory arguments as that's what's going to be the final directory.
<br> This is a command that lists out the items in a directory as a list.
<br>
![Image](lsnoarg.png)
<br>
When no arguments are passed in, it returns the items found in the current working directory.
<br>
![Image](ls1arg.png)
<br>
With a directory arguemnt, it returns list of items in that directory.
<br>
![Image](ls2arg.png)
<br>
With a file path argument, it returns the file path. 
<br> This is a command that lists out the items in a directory as a list.
<br>
![Image](catnoarg.png)
<br>
When no arguments are passed, it returns nothing.
<br>
![Image](cat1arg.png)
<br>
When a directory argument is passed in, it throws an error saying that the argument was a directory. This is because it cannot concatenate and print the items in a directory as it isn't a file.
<br>
![Image](cat2arg.png)
<br> 
When a file path is passed in, the contents of the file get printed out on the terminal.

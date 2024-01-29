Lab Report Week 1
`cd`  This is a command that changes the working directory. 

![Image](cdnoarg.png)

When we have no arguments passed in, the working directory was changed to the home directory. The two dots return back to one directory before the current directory. In this case, it went from:
<br> 
` \home\ lecture1 ` --> ` \home `
<br>
![Image](cd1arg.png)
<br>
With a directory argument, the new working directory was changed to the directory passed as an argument. In this case, it went from:
<br>
` \home ` --> ` \home\lecture1 `
<br>
![Image](cd2arg.png)
<br>
When a file path was passed in as an argument, an error message was thrown saying that the file wasn't a directory. The ` cd ` command can only accept directory arguments as that's what's going to be the final directory. Hence, the directories remained: 
<br>
`\home\lecture1 `
<br>
<br>
` ls ` 
<br> 
This is a command that lists out the items in a directory as a list.
<br>
![Image](lsnoarg.png)
<br>
When no arguments are passed in, it returns the items found in the current working directory.
<br>
![Image](ls1arg.png)
<br>
With a directory argument, it returns a list of items in that directory.
<br>
![Image](ls2arg.png)
<br>
With a file path argument, it returns the file path. 
<br>
<br>
` cat  ` 
<br> 
This is a command that prints out the contents of a single file. This is time-saving as one doesn't have to open the entire file in a large application and can read the contents still. 
<br>
![Image](catnoarg.png)
![Image](catnoarg1.png)
<br>
When no arguments are passed, it types the standard input back into the terminal. 
<br>
![Image](cat1arg.png)
<br>
When a directory argument is passed in, it throws an error saying that the argument was a directory. This is because it cannot concatenate and print the items in a directory as it isn't a file.
<br>
![Image](cat2arg.png)
<br> 
When a file path is passed in, the contents of the file get printed out on the terminal.

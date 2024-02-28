Step 4: Logging into ieng6   
`ssh ana012@ieng6.ucsd.edu`   
I pressed the relevant keys above to type up things.    
Since I wanted to organize my files, I created a `lab7report` folder to clone my fork into   
`mkdir` to create a  `lab7report` folder

--- 


Step 5: Cloning my fork   
`git clone git@github.com:anikaagarwal12/lab7.git`    
I pressed the relevant keys above to type up things.    
Since this clone made a lab7 folder, to access any files, I had to change my directories.    
`cd` lab7

--- 

Step 6: Running tests to show that they fail   
I ran the tests to show that there was an error in the files.     
`javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ListExamples.java ListExamplesTests.java`   
`java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests`   
   
This was the error message:   
```
JUnit version 4.13.2
..E
Time: 0.529
There was 1 failure:
1) testMerge2(ListExamplesTests)
org.junit.runners.model.TestTimedOutException: test timed out after 500 milliseconds
        at java.lang.System.arraycopy(Native Method)
        at java.util.Arrays.copyOf(Arrays.java:3213)
        at java.util.Arrays.copyOf(Arrays.java:3181)
        at java.util.ArrayList.grow(ArrayList.java:267)
        at java.util.ArrayList.ensureExplicitCapacity(ArrayList.java:241)
        at java.util.ArrayList.ensureCapacityInternal(ArrayList.java:233)
        at java.util.ArrayList.add(ArrayList.java:464)
        at ListExamples.merge(ListExamples.java:42)
        at ListExamplesTests.testMerge2(ListExamplesTests.java:19)

FAILURES!!!
Tests run: 2,  Failures: 1
```

--- 

Step 7: Editing code to fix the bug   
To fix the code found in the file found on ieng6, I cannot use a mouse to scroll through. Hence, I need to use vim to access that data.  
  
`vim ListExamples.java`  
These are the keys I pressed to navigate:   

To get to the line: 6 `<k>`   
To get to the character: 11 `<l>`   
Change mode to insert and replace: `i` and `<delete>` and `2`   
Exit out of insert mode: `<esc>`   
Save and Exit: `<:wq!>`   

--- 

Step 8: Rerunning the files to see success   
I compiled my files again and ran them to test.    
To access the compile commands and JUnit commands, I used the `<up>` arrow key to access my terminal history.

`<up><up><up><up><up><up><up><enter>` My history was 3 commands up, so I pressed the `<up>` 3 times.    
`[ana012@ieng6-201]:lab7:182$ javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ListExamplesTests.java ListExamples.java`


`<up><up><up><up><up><up><enter>` My history was 3 commands up, so I pressed the `<up>` 3 times.   
`[ana012@ieng6-201]:lab7:183$ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests`   
   
This was the output to show our success:   
```
JUnit version 4.13.2
..
Time: 0.014

OK (2 tests)
```

--- 

Step 9: Commit and push  
After we have made the changes, we should also make changes to my github repo.   
Adding changes to the staging area:   
Input: `[ana012@ieng6-201]:lab7:184$ git add --all`

Finalizing changes:   
Input: `[ana012@ieng6-201]:lab7:185$ git commit -m "lab7report changes`  

Output:   
``` 
[main 4eff394] lab7report changes
 Committer: Anika Agarwal <ana012@ieng6-201.ucsd.edu>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 1 insertion(+), 1 deletion(-)
```
Pushing changes to github:    
Input: `[ana012@ieng6-201]:lab7:184$ git push`   

Output:    
```
numerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 294 bytes | 294.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:anikaagarwal12/lab7.git
   5e6617f..95c7350  main -> main
```



Lab Report 5 

Part 1: 
---
Post on Edstem
```
Hello,

My name is Anika Agarwal and I am having this issue in my code somewhere in this project.
Here is what I see on my end when I try to run `bash test.sh`.
![image](https://github.com/anikaagarwal12/cse15l-lab-reports/assets/147211541/84975310-ac28-4bef-9888-350ddb703a3d)

Here is my code that I have written.
![image](https://github.com/anikaagarwal12/cse15l-lab-reports/assets/147211541/aaf3d8d5-6882-4f29-9132-97b00302cde1)

These are the test cases that we were given to test:
![image](https://github.com/anikaagarwal12/cse15l-lab-reports/assets/147211541/aa53a44b-d668-4736-b0e6-2f6d1bff7081)


I think the error is related my to the length of my arraylist. Each time I call merge(), I create a new arraylist. It seems like I am adding more elements to the arrayList than there is space for which is why I am getting an IndexOutOfBoundsException. Should I throw an exception in my method to limit the number of elements that I can add?


Thank you so much for your help!

Best Regards,
Anika Agarwal
```
---
Reply from TA
```
I see that the problem is definitely with your ArrayList. Did you try to check your while loop conditions. When you are trying to merge two different lists, what is the condition that must be true for you to make additions to your result arraylist?

Are both lists always going to be of the same size and what if they aren't the same size?
What in-built methods are you calling on both lists that won't work if you run out of elements from one list? 
```
---
Respond back to the TA
```
Thank you so much for your response! I have a better idea of potential bugs and I will look into them.

Thanks a lot for your help!
```
---
The issue was that I was comparing elements in the smaller list that didn't exist with the other elements in the other list that did exist. This was causing IndexOutOfBoundsException because that index element just didn't exist in the list. 

Here is the fixed version of the code: 
![image](https://github.com/anikaagarwal12/cse15l-lab-reports/assets/147211541/e039783e-f90c-4ff3-8b2d-d14548687a99)
To avoid the error, I replaced the condition of either list 1 or list 2 having elements with both of them having elements for the while loop to run so that `.compareTo()` works properly and doesn't throw IndexOutOfBounds errors. 

Here is the screenshot of the tests passing: 
![image](https://github.com/anikaagarwal12/cse15l-lab-reports/assets/147211541/f4b6c7d9-ac97-48cd-a023-ca110ad5e959)


Conclusion: 
The set-up of this debugging exercise was as follows     
File Structure: 
![image](https://github.com/anikaagarwal12/cse15l-lab-reports/assets/147211541/583a54d4-bbfc-4458-b64e-436d3da8be56)
Contents of `ListExamples` before fixing the bug: 
![image](https://github.com/anikaagarwal12/cse15l-lab-reports/assets/147211541/39d7a29c-0f47-414a-8a07-5cf8bee912e0)

Contents of `ListExamplesTests` before fixing the bug: 
![image](https://github.com/anikaagarwal12/cse15l-lab-reports/assets/147211541/03206f8b-0a90-4b02-b5c1-93b2ce1d23ea)

Contents of `bash test.sh` before fixing the bug: 
![image](https://github.com/anikaagarwal12/cse15l-lab-reports/assets/147211541/2808f300-10dc-4954-9bdb-a14099b8da33)

Lines I ran to trigger the bug: 
`bash test.sh` 
Description of what to edit to fix the bug: 
To fix the bug, I edited the following while condition:

Before: ` while(index1 < list1.size() || index2 < list2.size())`

After: `while(index1 < list1.size() && index2 < list2.size())`

Now, as soon as either list1 or list2 runs out of elements, the while loop stops running and the elements aren't compared. 
---
---
Part 2: 
One thing that I learned in the second half of the quarter was how to use vim to edit files remotely without using a text editor. We can use vim to access files that may not be on our computer and just using the terminal, we can access it, run it and edit it. I learned the different short cut keys to use vim. 

I also learned how to use a jdb debugger. It doesn't actually debug things but just tells us where the bug is happening. We as programmers still have to think and figure out where the errors are happening. 

I also learned how to write test cases to test things. 

I learned how to write bash scripts that make things easier when it comes to running a set of commands that need to be run frequently. 


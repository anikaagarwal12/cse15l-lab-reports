Lab Report 3

Part 1 - Bugs
---
The following are the tests that failed.

Input 1:
``` 
@Test
  public void testAverageWithoutLowestMultiple() {
    double[] input1 = {1,0, 1.0, 2.0, 3.0};
    assertEquals(2.5, ArrayExamples.averageWithoutLowest(input1), 0.0001);
  }
```
Input 2:
```
@Test
  public void testAverageWithoutLowestMultiple() {
    double[] input2 = {1.0, 3.0, 1.0, 2.0};
    assertEquals(2.5, ArrayExamplesFail.averageWithoutLowest(input2), 0.0001);
  }
```
The output of this test failing was a symptom that demonstrated a bug in the code.  It failed because the expected ```averageWithoutLowest()``` was 2.5, but it came out to be 1.75. 
Input 1 Fail:
```
1) testAverageWithoutLowestMultiple(ArrayTests)
java.lang.AssertionError: expected:<2.5> but was:<1.75>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:555)
        at org.junit.Assert.assertEquals(Assert.java:685)
        at ArrayTests.testAverageWithoutLowestMultiple(ArrayTests.java:60)
```
The output of this test failing was a symptom that demonstrated a bug in the code.  It failed because the expected ```averageWithoutLowest()``` was 2.5, but it came out to be 1.66. 
Input 2 Fail:
```
1) testAverageWithoutLowestMultiple(ArrayTests)
java.lang.AssertionError: expected:<2.5> but was:<1.6666666666666667>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:555)
        at org.junit.Assert.assertEquals(Assert.java:685)
        at ArrayTests.testAverageWithoutLowestMultiple(ArrayTests.java:62)

FAILURES!!!
```
Original version:
```
// Averages the numbers in the array (takes the mean), but leaves out the
  // lowest number when calculating. Returns 0 if there are no elements or just
  // 1 element in the array
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```

Since 1.0 is the lowest value and it is present 2 times in the array, it should be removed two times. Hence, the remaining elements should be 2.0 and 3.0 whose average will be 2.5. 
Here is the correct version of the code that passes all the tests. The bug was not accounting for multiple lowest value elements. It would only remove 1 from the new size ```(arr.length-1)```. It didn't account for when the elements were the same and lowest. 

Changed Version:
```
 static double averageWithoutLowest(double[] arr) {
    if (arr.length < 2) {
      return 0.0;
  }

  double lowest = arr[0];
  int lowestCount = 1; // Initialize count to 1 for the first occurrence of the lowest value

  // Find the lowest value and count its occurrences
  for (int i = 1; i < arr.length; i++) {
      if (arr[i] < lowest) {
          lowest = arr[i];
         lowestCount++;// Reset count for new distinct lowest value
      } else if (arr[i] == lowest) {
          lowestCount++; // Increment count for each occurrence of the current lowest value
      }
  }

  double sum = 0;
  // Calculate sum excluding the lowest value(s)
  for (double num : arr) {
      sum += num;
  }
  sum -= (lowest * lowestCount); // Subtract the sum of lowest value(s) from total sum
 
  return sum / (arr.length - lowestCount); // Calculate average
}
```
PS: I utilized ChatGPT for the best way to implement the changes in this code including the counter for the lowest values in an array. 
This was my input to "Debug this" and after a lot of on and off ChatGPT gave me a code that subtracted the number of times lowest value occurred. However, the code that it provided was still faulty and I had to debug a little more after it did its job. 


Here is the correct ouput: 
Input 1 Pass:
```
JUnit version 4.13.2
........
Time: 0.024

OK (8 tests)
```
Input 2 Pass:
```
JUnit version 4.13.2
........
Time: 0.031

OK (8 tests)
```

---
The following is a test that doesn't induce a failure.
```
 @Test
  public void testAverageWithoutLowest1Elem() {
    double[] input1 = {1.0};
    assertEquals(0.0, ArrayExamples.averageWithoutLowest(input1), 0.0001);
  }
```
This is because it doesn't test the other part of the code that caused an error in the other tests. 

---
Part 2 - Research Commands  
All of the commands that I found below are suggested by ChatGPT. 
The input that I gave ChatGPT is "command line options for find" and I received a bunch of options with details on how to use them. 

``` find ```

---
 ``` -name ```
 
 Example 1:
 ```
 Anika@LAPTOP-G52370DB MINGW64 ~/Anika/UCSD/UCSDWINTER2024/CSE15L/docsearch (main)
$ ls technical/
911report/  biomed/  government/  plos/

Anika@LAPTOP-G52370DB MINGW64 ~/Anika/UCSD/UCSDWINTER2024/CSE15L/docsearch (main)
$ find technical/911report/ -name "*.txt"
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
...
technical/911report/chapter-9.txt
technical/911report/preface.txt
```

 Example 2:
 ```
Anika@LAPTOP-G52370DB MINGW64 ~/Anika/UCSD/UCSDWINTER2024/CSE15L/docsearch (main)
$ find technical/government/About_LSC/ -name "*.txt"
technical/government/About_LSC/Comments_on_semiannual.txt
technical/government/About_LSC/commission_report.txt
...
technical/government/About_LSC/State_Planning_Special_Report.txt
technical/government/About_LSC/Strategic_report.txt
```
---
 ``` -type ```  
 Example 1:
```
Anika@LAPTOP-G52370DB MINGW64 ~/Anika/UCSD/UCSDWINTER2024/CSE15L/docsearch (main)
$ find technical/ -type d 
technical/
technical/911report
technical/biomed
...
technical/government/Post_Rate_Comm
technical/plos
```

 Example 2:
 ```
Anika@LAPTOP-G52370DB MINGW64 ~/Anika/UCSD/UCSDWINTER2024/CSE15L/docsearch (main)
$ find technical/government/ -type f
technical/government/About_LSC/Comments_on_semiannual.txt
technical/government/About_LSC/commission_report.txt
technical/government/About_LSC/conference_highlights.txt
 ...
technical/government/Post_Rate_Comm/ReportToCongress2002WEB.txt
technical/government/Post_Rate_Comm/WolakSpeech_usps.txt
```
---
```-mtime ```
 
 Example 1:
 ```
 $ find technical/government/ -mtime -24
technical/government/
 ...
 technical/government/Post_Rate_Comm/Redacted_Study.txt
technical/government/Post_Rate_Comm/ReportToCongress2002WEB.txt
technical/government/Post_Rate_Comm/WolakSpeech_usps.txt
```

 Example 2:
```
Anika@LAPTOP-G52370DB MINGW64 ~/Anika/UCSD/UCSDWINTER2024/CSE15L/docsearch (main)
$ find technical/911report/ -mtime +1
technical/911report/
...
technical/911report/chapter-9.txt
technical/911report/preface.txt
```
---

 `size` 

 Example 1 
 ```
Anika@LAPTOP-G52370DB MINGW64 ~/Anika/UCSD/UCSDWINTER2024/CSE15L/docsearch (main)
$ find technical/government/ -size +1b
technical/government/About_LSC/Comments_on_semiannual.txt
technical/government/About_LSC/commission_report.txt
...
technical/government/Post_Rate_Comm/WolakSpeech_usps.txt
```

 Example 2 
```
Anika@LAPTOP-G52370DB MINGW64 ~/Anika/UCSD/UCSDWINTER2024/CSE15L/docsearch (main)
$ find technical/government/Media/ -size +1k
technical/government/Media/5_Legal_Groups.txt
technical/government/Media/Abuse_penalties.txt
technical/government/Media/Advocate_for_Poor.txt
...
technical/government/Media/Workers_aid_center.txt
technical/government/Media/Working_for_Free.tx
```

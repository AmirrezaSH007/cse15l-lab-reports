
**Student Question:**


I'm having trouble with my Sorter.java program. I expect it to sort an array of integers, but it seems to be giving me incorrect results. 
I think the issue might be with my sorting logic or how I'm handling array indices.

![Image](buggy-code.png)

Here is a screenshot of my terminal output:

![Image](Buggy-output.png)

In this example, I tried to sort the array `[3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]`, but the output is not sorted correctly.
Can you help me find the error or the bug?



**TA Response:**

It looks like there might be an issue with your sorting logic. Let's try to narrow down the problem.
You can add some debug `print` statements inside your sorting method to see how the array changes after each iteration.

**Student Response:**

Thanks for the suggestion! I added the debug print statement as you suggested.

![Image](Debug-code.png)
 Here is the updated output:
It looks like the array is partially sorted, but some elements are still out of place after each pass.

![Image](Debugging-output.png)
From the debug output, I noticed that elements are not being compared correctly.

.
.
.
.
.
.


* **The directory of the code which was used to create the above story:**

![Image](Directory.png)

* **The setup for `run_sorter.sh`**
  
![Image](run-sorter.png)

* **The Fixed code after debugging and finding the error:**
  
![Image](Fixed-code.png)

* **The correct output after fixing the code and using `bash` to run:**
  
![Image](Fixed-output.png)

**Reflection:**
This class showed me that terminal itself, is a whole different story. For us who started learning to write codes, all we think, or used to think, was to write the perfect code. This class showed me there are many different things can be done through terminal and it can make our lives as programers much much easier. One of the other interesting things I learned was connecting to the UCSD servers. During the lab, when we worked on something difficult as a group, different oppinions, in most of the times, was the key for us to be success in that lab. This is the other thing I learned. I learned to hear, analize and test what the people around me have to say.


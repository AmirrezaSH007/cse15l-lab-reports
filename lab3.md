**PART 1)**
* #1) A failure-inducing input
  **`ArrayTests.java`**
  ```import org.junit.Test;
     import static org.junit.Assert.*;

     public class ArrayTests {
       @Test //This test checks if the method correctly reverses an array of four elements. If there is a bug to improper swapping, this test will likely fail.
       public void testReverseInPlaceFailure() {
         int[] input = {1, 2, 3, 4};
         ArrayExamples.reverseInPlace(input);
         assertArrayEquals(new int[]{4, 3, 2, 1}, input);
       }
     }
  ``` 

* #2) An input that doesn't induce a failure
  ```@Test 
       public void testReverseInPlaceNonFailure() {
          int[] input = { 3 };
          ArrayExamples.reverseInPlace(input);
          assertArrayEquals(new int[]{ 3 }, input); // This test should pass as reversing a single element doesn't change the array.
       }
  ```
* #3) 
![Image](symptom.png)
* #4)
  ``` public class ArrayExamples {
        public static void reverseInPlace(int[] array) {
          for (int i = 0; i < array.length; i++) {
            int temp = array[i];
            array[i] = array[array.length - i]; 
            array[array.length - i] = temp;     
       }
     }
  }
  
 **Next**

  ```public class ArrayExamples {
       public static void reverseInPlace(int[] array) {
         for (int i = 0; i < array.length / 2; i++) {
            int temp = array[i];
            array[i] = array[array.length - 1 - i]; 
            array[array.length - 1 - i] = temp;     
        }
     }
  }
```
* #5)
The fix addresses the issue by correctly using `array.length - 1 - i` for indexing, which correctly accesses the elements from the end of the array to swap with those at the beginning, without exceeding the array bounds. The loop only goes up to the middle of the array (`array.length / 2`), it makes sure that each element is swapped once, which reverses the array. This change ensures that the method behaves correctly for all valid input sizes and types, including arrays with an even number of elements, which was where the original method failed.

**PART 2)**
I used `man grep` on my terminal and every usable command poped up and these are the ones I chose which I think are both interesting and useful:
![Image](r.png)
This command searches for the word "function" in all files within the ./technical directory and all its subdirectories. It's useful for finding occurrences of "function" in multiple files without having to specify each file.

`grep -r "function" ./technical/`
```
./technical//biomed/1471-2202-2-6.txt:        assemble to form a functional channel. Both homomultimeres
./technical//biomed/1471-2202-2-6.txt:        this function, since it is the only IP 
./technical//biomed/1471-2202-2-6.txt:        expressed in taste cells [ 26], also functions to decrease
./technical//biomed/1475-2867-2-15.txt:        usage [ 2 ] . Both the RARs and RXRs contain functional
./technical//biomed/1475-2867-2-15.txt:        promoters. RARs and RXRs function as heterodimers that bind
./technical//biomed/1475-2867-2-15.txt:        of serine 77 enhanced the transactivation function of RARα.
./technical//biomed/1475-2867-2-15.txt:        the proper functioning of RARs.
./technical//biomed/1475-2867-2-15.txt:        to inhibit the basal activation function of the receptor [
.
.
.
. many more
```

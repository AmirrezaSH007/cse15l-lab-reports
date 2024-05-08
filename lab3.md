* Part 1) A failure-inducing input
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
     }``` 

* Part 2) An input that doesn't induce a failure
    ```@Test 
       public void testReverseInPlaceNonFailure() {
          int[] input = { 3 };
          ArrayExamples.reverseInPlace(input);
          assertArrayEquals(new int[]{ 3 }, input); // This test should pass as reversing a single element doesn't change the array.
       }```
Part 3) 
![Image](symptom.png)

**PART 1)**
* #1) A failure-inducing input
  **`ArrayTests.java`**

  ```
  import org.junit.Test;
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
  ```
  @Test 
       public void testReverseInPlaceNonFailure() {
          int[] input = { 3 };
          ArrayExamples.reverseInPlace(input);
          assertArrayEquals(new int[]{ 3 }, input); // This test should pass as reversing a single element doesn't change the array.
       }
  ```
* #3) 
![Image](symptom.png)
* #4)
```
  public class ArrayExamples {
        public static void reverseInPlace(int[] array) {
          for (int i = 0; i < array.length; i++) {
            int temp = array[i];
            array[i] = array[array.length - i]; 
            array[array.length - i] = temp;     
       }
     }
  }
```  
 
 **Next**

```
public class ArrayExamples {
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

* **`grep -r "function" ./technical/`**

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
* **`grep -r "^import" ./technical/`**
  Again, This command does the same as above, but searches for lines that start with "import" in all files under the ./technical directory recursively.

```
./technical//government/About_LSC/Strategic_report.txt:important to the creation of a world-class delivery system as state
./technical//government/About_LSC/Strategic_report.txt:important consulting and facilitative assistance with configuration
./technical//government/About_LSC/CONFIG_STANDARDS.txt:importance of creating enduring capacities at the state level to
./technical//government/About_LSC/commission_report.txt:important agricultural states, such as Arkansas, Kentucky, New
./technical//government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt:important mechanism to bring people together to find-and
./technical//government/About_LSC/diversity_priorities.txt:importance of a diverse workplace and the commitment of board and
.
.
.
.many more
```
**NEXT**

![Image](i.png)
* **`grep -i "MODel" ./technical/biomed/rr73.txt`** This searches for the word "model" in rr73.txt under the ./technical/biomed directory, ignoring case. It's useful when we're unsure of the casing.

  ```in vitro model of 
  remodeling. It seems unlikely that tissue remodeling is
  ```
  
 * **`grep -i "STudY" ./technical/biomed/rr196.txt`** Again does the same but for the word "study" and in a different file.

```
   control muscle in that study [ 11 ] .
        out to study changes in MHC-determined fiber types and MHC
          An apparatus for the study 
          After study, the strip was removed from the apparatus,
          cross-sectional area. Study of two of the control rat
        demonstrated [ 10 ] , and in that study histochemical
        from IIb fibers. Furthermore, no study in emphysematous
        more in line with Kanbara's findings. In that study, the
        fibers [ 10 ] . Another study has shown increased
        animal model of emphysema, this study is the first to
```

**NEXT**

  ![Image](n.png)
* **`grep -n "study" ./technical/biomed/rr73.txt`** This command searches for "study" in the ./technical/rr73.txt, displaying line numbers with matches. It's particularly useful when editing files as it tells you exactly where to find the terms.

```
16:        Results in the linked study [ 5] demonstrated that 3D
20:        the current study, an extension of this linked study, was
148:        In the linked study [ 5], extended co-cultures of
152:        degradation of collagen. The current study suggests that
163:        21]. The current study suggests the possibility that NE can
182:        however, develop emphysema [ 14]. The current study
186:        According to results from this study, several proteases
189:        play a role beyond those evaluated in the current study. In
222:        This study demonstrates that monocytes and fibroblasts
```
* **`grep -n "model" ./technical/biomed/rr196.txt`** Again, does the same but in a different file and finds the word "model" with the matched lines.

```
7:        studied animal model for human emphysema. Several
9:        been demonstrated in this model. Among these are diaphragm
46:        which is similar to that seen in the animal model.
74:        expected that such findings might identify the rat model of
75:        elastase-induced emphysema as a model in which the
119:          servomotor system (motor model 6450, electronics model
432:        animal model of emphysema. These changes are qualitatively
438:        The most studied animal model for the adaptation of
440:        elastase-induced emphysema. The hamster model has probably
510:        diaphragm in animal models of emphysema, fiber type has
533:        MHC shifts in rodent models of emphysema than in humans
538:        disease in comparison with the animal models that have yet
553:        Other studies of MHC adaptation in animal models of
586:        animal model of emphysema, this study is the first to
652:        animal models of emphysema without the demonstration of
660:        animal model the shift occurs at the faster end of the
```

**NEXT**

![Image](exclude.png)
* **`grep -r --exclude-dir=biomed "cache" ./technical/`** This command searches recursively for "cache" in all files within ./technical, excluding any directory named `biomed`. It helps in avoiding redundant searches in `biomed` directory.

```
./technical//government/Media/Retirement_Has_Its_Appeal.txt:"He has the cachet of being a long-standing family court judge,
./technical//911report/chapter-13.4.txt:                cachets. CIA analytic report, Al Qaeda travel issues, Jan. 2004, p. 1.
./technical//911report/chapter-13.4.txt:                1999. Another possible source of suspicion is his passport, which contains a cachet
./technical//911report/chapter-5.txt:                and adding travel cachets, were also taught. Manuals demonstrating the technique for
./technical//911report/chapter-12.txt:                recorded in passports with entry-exit stamps called cachets, which al Qaeda has
```
* **`grep -r --exclude-dir={government,biomed} "session" ./technical/`** Again does the same, but this times, we used the command so that we exclude both `government` and `biomed` to find the word session in the other.
  
```
./technical//plos/pmed.0020060.txt:        Museum of French Art in New York, auctioned, and finally ending up in the possession of a
./technical//plos/pmed.0020060.txt:        tapes of hundreds of hours of therapy sessions given to her by Sexton's therapist Dr.
./technical//plos/journal.pbio.0030136.txt:        obsession reveal about neural processing? Why does repeated fine-grain structure wreak such
./technical//plos/pmed.0020016.txt:        preparation for that session, Schwartländer et al. published an estimate of the resource
./technical//plos/journal.pbio.0020116.txt:        opinion that research into prolonging healthy life may result in a lifetime obsession with
./technical//plos/pmed.0020034.txt:        current obsession of the medical profession with the pharmaceutical management of asthma
./technical//plos/journal.pbio.0020306.txt:        these was in October 2002, a massive brainstorming session at which we all dug around in
./technical//911report/chapter-13.4.txt:                Jarrah had in his possession, but released him after he pointed out that he had
.
.
.
. more
```

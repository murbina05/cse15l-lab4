# In this lab report we will be working with vim 


## Part 2

The first thing I type is command-v and <Enter> this will copy the command for cloning the repo that was provided and then I click enter in order to run the command and clone the repository
```
[maurbina@ieng6-201]:~:58$ git clone https://github.com/ucsd-cse15l-s23/lab7
Cloning into 'lab7'...
remote: Enumerating objects: 58, done.
remote: Counting objects: 100% (24/24), done.
remote: Compressing objects: 100% (12/12), done.
remote: Total 58 (delta 15), reused 12 (delta 12), pack-reused 34
Receiving objects: 100% (58/58), 376.37 KiB | 1.18 MiB/s, done.
Resolving deltas: 100% (21/21), done.
```

After that I type ls to see what files were cloned which gives the following output

```
[maurbina@ieng6-201]:~:59$ ls
Desktop    Downloads  Pictures  Templates  lab7   wavelet
Documents  Music      Public    Videos     perl5

```

The next thing I type is cd lab7/ which will change the working directory to the new directory where all the files are located 
```
[maurbina@ieng6-201]:~:60$ cd lab7/
```

Next I type ls again to see what files were cloned and see the following files 
```
[maurbina@ieng6-201]:lab7:61$ ls
ListExamples.java  ListExamplesTests.java  lib  test.sh
```

From here I run the test script using bash test.sh which will run the script and you can see the output below 
```
[maurbina@ieng6-201]:lab7:62$ bash test.sh
JUnit version 4.13.2
..E
Time: 0.534
There was 1 failure:
1) testMerge2(ListExamplesTests)
org.junit.runners.model.TestTimedOutException: test timed out after 500 milliseconds
	at java.util.Arrays.copyOf(Arrays.java:3210)
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

Next I type vim ListExamplesTests.java which will allow me to check the test in order to fix the error
```
[maurbina@ieng6-201]:lab7:63$ vim ListExamplesTests.java

```

The code bellow is the ListExamplesTests.java that I will edit. I do this by typing in <down><down><down><down><down><down><down><down><down><down><down><down><down><down><down><down><down><down><down><down> 19 times to go to the assertArrayEquals of testMerge2 method. From here I will type i in order to enter insert mode. Next I hold <left> till I get to the parameters taht we pass to the merge function. Here I will <delete> 1 and type in 2 and <delete> 2 and type in 1
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
        @Test(timeout = 500)
        public void testMerge1() {
                List<String> l1 = new ArrayList<String>(Arrays.asList("x", "y"));
                List<String> l2 = new ArrayList<String>(Arrays.asList("a", "b"));
                assertArrayEquals(new String[]{ "a", "b", "x", "y"}, ListExamples.merge(l1, l2).toArray());
        }

	@Test(timeout = 500)
        public void testMerge2() {
                List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
                List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
                assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
        }

}
```

This will make the file look like the code below. Keep in mind that the only thing that I changed was the parameters that I pass to merge
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
        @Test(timeout = 500)
        public void testMerge1() {
                List<String> l1 = new ArrayList<String>(Arrays.asList("x", "y"));
                List<String> l2 = new ArrayList<String>(Arrays.asList("a", "b"));
                assertArrayEquals(new String[]{ "a", "b", "x", "y"}, ListExamples.merge(l1, l2).toArray());
        }

	@Test(timeout = 500)
        public void testMerge2() {
                List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
                List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
                assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l2, l1).toArray());
        }

}

```

The next thing I type in is bash test.sh again to run the test scrip again and as you can see it now passes
```
[maurbina@ieng6-201]:lab7:64$ bash test.sh
JUnit version 4.13.2
..
Time: 0.013

OK (2 tests)

```

The last thing I do is push to github I do this first by typing the git add ListExamplesTests.java which will add the file 
```
[maurbina@ieng6-201]:lab7:70$ git add ListExamplesTests.java 
```
I then type in git commit -m "Fixed test methods" this will add the git messages when I push to the repo 

```
[maurbina@ieng6-201]:lab7:70$ git commit -m "Fixed test methods"
```
Lastly I will finally push to the actual github repo by typing git push https://github.com/murbina05/cse15l-lab4.git you can see the example below

```
[maurbina@ieng6-201]:lab7:70$ git push https://github.com/murbina05/cse15l-lab4.git 
```

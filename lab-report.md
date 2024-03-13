# In this lab report we will be working with vim 


## Part 1

The first thing I type is type s, s, h, `<space>`, m, a, u, r, b, i, n, a, @, i, e, n, g, 6, -, 2, 0, 1, ., u, c, s, d, ., e, d, u, `<enter>` to ssh into the server 

```
murbina@Max:~$ ssh maurbina@ieng6-201.ucsd.edu
```

Next I type g,i,t, `<space>`, c,l,o,n,e, `<command-v>` and `<Enter>` this will copy the command for cloning the repo that was provided and then I click enter in order to run the command and clone the repository
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

After that I type l, s `<enter>` to see what files were cloned which gives the following output

```
[maurbina@ieng6-201]:~:59$ ls
Desktop    Downloads  Pictures  Templates  lab7   wavelet
Documents  Music      Public    Videos     perl5

```

The next thing I type is c, d, `<space>`, l, a, b, 7, `<enter>` which will change the working directory to the new directory where all the files are located 
```
[maurbina@ieng6-201]:~:60$ cd lab7/
```

Next I type l, s, `<enter>` again to see what files were cloned and see the following files 
```
[maurbina@ieng6-201]:lab7:61$ ls
ListExamples.java  ListExamplesTests.java  lib  test.sh
```

From here I run the test script using b, a, s, h, `<space>`, t, e, s, t, ., s, h, `<enter>` which will run the script and you can see the output below 
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

Next I type v, i, m, `<space>` ListExmaples.java, `<enter>`  which will allow me to check file in order to fix the error
```
[maurbina@ieng6-201]:lab7:63$ vim ListExamples.java

```

The code bellow is the ListExamples.java that I will edit. I do this by holding `<down>` untile I get to the line that updates index1 and change it to index2 by typing i, `<left>` until i get to 1, `<delete>`, 2, `<escape>`, `<shift z>`, `<shift z>` to save the changes. You can see how the file looked before and after the changes below.  
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }


}
```

This will make the file look like the code below. Keep in mind that the only thing that I changed what index was updated so that it keeps track of elements properly 
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }
    return result;
  }


}
```

The next thing I type in is b,a,s,h, `<space>`, t, e, s, t, ., s, h, `<enter>` again to run the test scrip again and as you can see it now passes
```
[maurbina@ieng6-201]:lab7:64$ bash test.sh
JUnit version 4.13.2
..
Time: 0.013

OK (2 tests)

```

The last thing I do is push to github I do this first by typing the g, i, t, `<space>`, a, d, d, `<.>`, `<enter>`  which will add the file 
```
[maurbina@ieng6-201]:lab7:70$ git add ListExamplesTests.java 
```
I then type in g,i,t, `<space>`, c, o, m, m, i, t, `<space>`, -,m, `<space>`, ",F i ,x ,e ,d , `<space>`, t, e, s, t, `<space>`, m, e, t, h, o, d, s, ", `<enter>` this will add the git messages when I push to the repo 

```
[maurbina@ieng6-201]:lab7:70$ git commit -m "Fixed test methods"
```
Lastly I will finally push to the actual github repo by typing g,i,t, `<space>`, p,u,s,h,`<space>` h,t,t,p,s,:,/,/,g,i,t,h,u,b,.,c,o,m,/,m,u,r,b,i,n,a,0,5,/,c,s,e,1,5,l,-,l,a,b,4,.,g,i,t `<enter>` you can see the example below

```
[maurbina@ieng6-201]:lab7:70$ git push https://github.com/murbina05/cse15l-lab4.git 
```


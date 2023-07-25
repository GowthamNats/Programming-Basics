# Java Programs

## Q. Write a function to find out duplicate words in a given string?

**Approach:**

1. Define a string.
1. Convert the string into lowercase to make the comparison insensitive.
1. Split the string into words.
1. Two loops will be used to find duplicate words. Outer loop will select a word and Initialize variable count to 1. Inner loop will compare the word selected by outer loop with rest of the words.
1. If a match found, then increment the count by 1 and set the duplicates of word to '0' to avoid counting it again.
1. After the inner loop, if count of a word is greater than 1 which signifies that the word has duplicates in the string.

```java
public class DuplicateWord {  

    public static void main(String[] args) {  
    
        String string = "Big black bug bit a big black dog on his big black nose";  
        int count;  
          
        //Converts the string into lowercase  
        string = string.toLowerCase();  
          
        //Split the string into words using built-in function  
        String words[] = string.split(" ");  
          
        System.out.println("Duplicate words in a given string : ");   
        for(int i = 0; i < words.length; i++) {  
            count = 1;  
            for(int j = i+1; j < words.length; j++) {  
                if(words[i].equals(words[j])) {  
                    count++;  
                    //Set words[j] to 0 to avoid printing visited word  
                    words[j] = "0";  
                }  
            }  
              
            //Displays the duplicate word if count is greater than 1  
            if(count > 1 && words[i] != "0")  
                System.out.println(words[i]);  
        }  
    }  
}  
```

Output

```java
Duplicate words in a given string : 
big
black
```

## Q. Find the missing number in an array?

**Approach:**

1. Calculate `A = n (n+1)/2` where n is largest number in series 1…N.
1. Calculate B = Sum of all numbers in given series
1. Missing number = A – B

```java
// Java program to find missing Number 

public class Test {  
    
	public static void main(String[] args) {

		int total;
		int[] numbers = new int[]{1, 2, 3, 4, 6, 7};
		total = 7;
		int expected_sum = total * ((total + 1) / 2);
		int num_sum = 0;
		
		for (int i: numbers) {
		 num_sum += i;
		}
		
		System.out.print( expected_sum - num_sum );
	}
}   
```
Output
```
5
```
<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. Write a program to generate random numbers between the given range?

**Approach**
1. Get the Min and Max which are the specified range.
1. Call the nextInt() method of ThreadLocalRandom class (java.util.concurrent.ThreadLocalRandom) and specify the Min and Max value as the parameter as
`ThreadLocalRandom.current().nextInt(min, max + 1);`
1. Return the received random value

```java
// Java program to generate a random integer
// within this specific range

import java.util.concurrent.ThreadLocalRandom;

class GFG {

	public static int getRandomValue(int Min, int Max)
	{

		// Get and return the random integer
		// within Min and Max
		return ThreadLocalRandom
			.current()
			.nextInt(Min, Max + 1);
	}

	// Driver code
	public static void main(String[] args)
	{

		int Min = 1, Max = 100;

		System.out.println("Random value between "
						+ Min + " and " + Max + ": "
						+ getRandomValue(Min, Max));
	}
}

```

**Input**
```
Input: Min = 1, Max = 10
```

**Output**
```
Random value between 1 and 100: 35
```

## Q. Write a java program to swap two string variables without using temp variable?
**Approach**  

1. Append second string to first string and store in first string:
   a = a + b

2. call the method substring(int beginindex, int endindex)
   by passing beginindex as 0 and endindex as,
      a.length() - b.length():
   b = substring(0,a.length()-b.length());

3. call the method substring(int beginindex) by passing 
   b.length() as argument to store the value of initial 
   b string in a
   a = substring(b.length());

```java
/**
* Java program to swap two strings without using a temporary 
* variable.
**/ 
import java.util.*; 

class Swap 
{	 
	public static void main(String args[]) {

		// Declare two strings 
		String a = "Hello"; 
		String b = "World"; 
		
		// Print String before swapping 
		System.out.println("Strings before swap: a = " + a + " and b = "+b); 
		
		// append 2nd string to 1st 
		a = a + b; 
		
		// store intial string a in string b 
		b = a.substring(0, a.length() - b.length()); 
		
		// store initial string b in string a 
		a = a.substring(b.length()); 
		
		// print String after swapping 
		System.out.println("Strings after swap: a = " + a + " and b = " + b);		 
	}	 
} 
```
Output
```
Strings before swap: a = Hello and b = World
Strings after swap: a = World and b = Hello
```

## Q. Write a java program to Move all zeroes to end of array?
```
Input:  arr[] = {1, 2, 0, 4, 3, 0, 5, 0};
Output: arr[] = {1, 2, 4, 3, 5, 0, 0, 0};
```
```java

public class Test 
{  
   	static void pushZerosToEnd(int arr[], int n) {
		
        int count = 0;  // Count of non-zero elements 
  
        // Traverse the array. If element encountered is 
        // non-zero, then replace the element at index 'count' 
        // with this element 
        for (int i = 0; i < n; i++) 
            if (arr[i] != 0) 
                arr[count++] = arr[i]; 
  
        // Now all non-zero elements have been shifted to 
        // front and 'count' is set as index of first 0. 
        // Make all elements 0 from count to end. 
        while (count < n) 
            arr[count++] = 0; 
    } 
  
   
    public static void main (String[] args) { 
    	
        int arr[] = {1, 9, 8, 4, 0, 0, 2, 7, 0, 6, 0, 9}; 
        int n = arr.length; 
        pushZerosToEnd(arr, n); 
        System.out.println("Array after pushing zeros to the back: "); 
        for (int i=0; i<n; i++) 
            System.out.print(arr[i]+" "); 
    } 	 
}  
```
Output
```
Array after pushing all zeros to end of array:
1 9 8 4 2 7 6 9 0 0 0 0
```
<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. Write a multi-threading program to print odd number using one thread and even number using other?
```java
class TaskEvenOdd implements Runnable {

    private int max;
    private Printer print;
    private boolean isEvenNumber;

    TaskEvenOdd(Printer print, int max, boolean isEvenNumber) {
        this.print = print;
        this.max = max;
        this.isEvenNumber = isEvenNumber;
    }

    @Override
    public void run() {
   
        int number = isEvenNumber == true ? 2 : 1;
        while (number <= max) {

            if (isEvenNumber) {
                //System.out.println("Thread Even: "+ Thread.currentThread().getName());
                print.printEven(number);
            } else {
                //System.out.println("Thread Odd: "+ Thread.currentThread().getName());
                print.printOdd(number);
            }
            number += 2;
        }
    }
}

class Printer {

    boolean isOdd = false;

    synchronized void printEven(int number) {

        while (isOdd == false) {
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println("Thread Even: " + number);
        isOdd = false;
        notifyAll();
    }

    synchronized void printOdd(int number) {
        while (isOdd == true) {
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println("Thread Odd: " + number);
        isOdd = true;
        notifyAll();
    }
}

public class Test 
{  
	static int MAX = 5;
	public static void main(String... args) {
        Printer print = new Printer();
        Thread t1 = new Thread(new TaskEvenOdd(print, MAX, false));
        Thread t2 = new Thread(new TaskEvenOdd(print, MAX, true));
        t1.start();
        t2.start();
    }	 
} 
```
Output
```
Thread Odd: 1
Thread Even: 2
Thread Odd: 3
Thread Even: 4
Thread Odd: 5
```
## Q. How to print all permutations of a String in Java?
**Approach**  

1. Define a string.
1. Fix a character and swap the rest of the characters.
1. Call the generatePermutation() for rest of the characters.
1. Backtrack and swap the characters again.

**Recursive Approach**  


![Recursive Approach](https://github.com/learning-zone/java-interview-questions/blob/master/assets/recursive.png)

```java
public class PermuteString 
{  
    // Function for swapping the characters   
    public static String swapString(String a, int i, int j) {  
        char[] b =a.toCharArray();  
        char ch;  
        ch = b[i];  
        b[i] = b[j];  
        b[j] = ch;  
        return String.valueOf(b);  
    }  

    // Function for generating different permutations of the string  
    public static void generatePermutation(String str, int start, int end) {

        //Prints the permutations  
        if (start == end-1)  
            System.out.println(str);  
        else {  

            for (int i = start; i < end; i++) {

                //Swapping the string by fixing a character  
                str = swapString(str,start,i);  
                //Recursively calling function generatePermutation() for rest of the characters   
                generatePermutation(str,start+1,end);  
                //Backtracking and swapping the characters again.  
                str = swapString(str,start,i);  
            }  
        }  
    }

    public static void main(String[] args) {

        String str = "ABC";  
        int len = str.length();  
        System.out.println("All the permutations of the string are: ");  
        generatePermutation(str, 0, len);  
    }   
}  
```
Output
```
All the permutations of the string are: 

ABC
ACB
BAC
BCA
CBA
CAB
```
## Q. Reverse the string with preserving the position of spaces
**Approach**  

1. Create a string to store result. Mark the space position of the given string in this string.
1. Insert the character from input string into the result string in reverse order.
1. While inserting the character check if the result string already contains a space at index ‘j’ or not. If it contains, we copy the character to the next position.

```java
// Java program to reverse a string 
// preserving spaces. 
public class ReverseStringPreserveSpace 
{ 
	static void reverses(String str) { 
			
	  char[] inputArray = str.toCharArray(); 
	  char[] result = new char[inputArray.length]; 
	  // Mark spaces in result 
	  for (int i = 0; i < inputArray.length; i++) { 
	    if (inputArray[i] == ' ') { 
	    	result[i] = ' '; 
	    } 
	  } 		
	  // Traverse input string from beginning 
	  // and put characters in result from end 
	  int j = result.length - 1; 
	  for (int i = 0; i < inputArray.length; i++) { 	
	    // Ignore spaces in input string 
	    if (inputArray[i] != ' ') { 			
	      // ignore spaces in result. 
	      if (result[j] == ' ') { 
	      	j--; 
	      }	 
	      result[j] = inputArray[i]; 
	      j--; 
	    } 
	  } 
	  System.out.println(String.valueOf(result)); 
	} 
	public static void main(String[] args) {
		reverses("India Is my country"); 
	} 
} 
```
Output
```
India Is my country --> yrtnu oc ym sIaidnI
```
## Q. How do you find longest substring without repeating characters in a string?
**Approach**  

1. Start traversing the string from left to right and maintain track
2. Check the non-repeating characters in current substring with the help of a start and end index

```java
public class Test 
{  
	public static String getUniqueCharacterSubstring(String input) {

	    Map<Character, Integer> visited = new HashMap<>();
	    String output = "";
	    for (int start = 0, end = 0; end < input.length(); end++) {
	        char currChar = input.charAt(end);
	        if (visited.containsKey(currChar)) {
	            start = Math.max(visited.get(currChar) + 1, start);
	        }
	        if (output.length() < end - start + 1) {
	            output = input.substring(start, end + 1);
	        }
	        visited.put(currChar, end);
	    }
	    return output;
	}

	public static void main(String[] args) {
		
	    String input = "LongestSubstringFindOut";
	    System.out.println(getUniqueCharacterSubstring(input));
	} 
} 
```
Output
```
LongestSubstringFindOut --> LongestSub
```
## Q. A Program to check if strings are rotations of each other or not?
**Approach**

1. Create a temp string and store concatenation of str1 to str1 in temp.
        temp = str1.str1
2. If str2 is a substring of temp then str1 and str2 are rotations of each other.

Example:                 
        str1 = "ABACD"
        str2 = "CDABA"

        temp = str1.str1 = "ABACDABACD"
Since str2 is a substring of temp, str1 and str2 are rotations of each other.

```java
class StringRotation 
{

	static boolean areRotations(String str1, String str2) { 
		// There lengths must be same and str2 must be 
		// a substring of str1 concatenated with str1. 
		return (str1.length() == str2.length()) && ((str1 + str1).indexOf(str2) != -1); 
	} 
	
	public static void main (String[] args) { 
		String str1 = "AACD"; 
		String str2 = "ACDA"; 

		if (areRotations(str1, str2)) 
			System.out.println("Strings are rotations of each other"); 
		else
			System.out.printf("Strings are not rotations of each other"); 
	} 
} 
```
Output
```
Strings are rotations of each other
```
## Q. Can you write a regular expression to check if String is a number?
```java
public class StringTest 
{
	public static void main (String[] args) { 
		String regex = "[0-9]+";
		// String regex = "\\d+";
		String data = "23343453";
		System.out.println("Is Number: "+ data.matches(regex));
	} 
} 
```
Output
```
Is Number: true
```
## Q. Write a program to find top two maximum numbers in a array?
```java
public class TwoMaxNumbers {
 
    public void printTwoMaxNumbers(int[] nums) {
        int maxOne = 0;
        int maxTwo = 0;
        for(int n:nums) {
            if(maxOne < n) {
                maxTwo = maxOne;
                maxOne = n;
            } else if(maxTwo < n) {
                maxTwo = n;
            }
        }
        System.out.println("First Max Number: "+maxOne);
        System.out.println("Second Max Number: "+maxTwo);
    }
     
    public static void main(String a[]) {
        int num[] = {5,34,78,2,45,1,99,23};
        TwoMaxNumbers tmn = new TwoMaxNumbers();
        tmn.printTwoMaxNumbers(num);
    }
}
```
Output
```
First Max Number: 99
Second Max Number: 78
```
## Q. How to find all the leaders in an integer array in java?
An element is leader if it is greater than all the elements to its right side. And the rightmost element is always a leader. For example int the array {16, 17, 4, 3, 5, 2}, leaders are 17, 5 and 2.

```java
public class Test 
{
    void printLeaders(int arr[], int size) { 
        for (int i = 0; i < size; i++) { 
            int j; 
            for (j = i + 1; j < size; j++) { 
                if (arr[i] <= arr[j]) 
                    break; 
            } 
            if (j == size) // the loop didn't break 
                System.out.print(arr[i] + " "); 
        } 
    } 

    public static void main(String[] args) { 
    	Test lead = new Test(); 
        int arr[] = new int[]{25, 10, 2, 4, 1, 3}; 
        int n = arr.length; 
        lead.printLeaders(arr, n); 
    } 
} 
```
Output
```
25 10 4 3 
```
## Q. Write a java program to find number of characters, number of words and number of lines in a text file?
```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class CharacterCount 
{
	public static void main(String[] args) {

        int charCount = 0;
        int wordCount = 0;
        int lineCount = 0;
         
        try (
        	BufferedReader reader = new BufferedReader(new FileReader("C:\\file.txt"));
        ) {    
            // Reading the first line into currentLine
            String currentLine = reader.readLine();
             
            while (currentLine != null) {
                // Updating the lineCount
                lineCount++;
                 
                // Getting number of words in currentLine
                String[] words = currentLine.split(" ");
                 
                // Updating the wordCount
                wordCount = wordCount + words.length;

                for (String word : words) {
                    charCount = charCount + word.length();
                }
                 
                // Reading next line into currentLine
                currentLine = reader.readLine();
            }
 
            System.out.println("Number Of Chars In A File : "+charCount);
            System.out.println("Number Of Words In A File : "+wordCount);
            System.out.println("Number Of Lines In A File : "+lineCount);
        } 
        catch (IOException e) {
            e.printStackTrace();
        }
    }   
} 
```
## Q. Find all pairs of elements whose sum is equal to given number?
```java
public class FindPairs 
{  	
	// Prints number of pairs in arr[0..n-1] with sum equal 
    // to 'sum' 
    public static void getPairsCount(int[] arr, int sum) {
        // Consider all possible pairs and check their sums 
        for (int i = 0; i < arr.length; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                if ((arr[i] + arr[j]) == sum) {
                	System.out.printf("(%d, %d) %n", arr[i], arr[j]); 
                }
            }
        }
    }
	public static void main(String args[]) { 
        int[] arr = { 1, 5, 7, -1, 5 }; 
        int sum = 12; 
        getPairsCount(arr, sum); 
    }
} 
```
Output
```
(5, 7) 
(7, 5)
```
## Q. Program to convert lower to upper case without using toUppercase()?
```java
public class LowerToUpperCase 
{  	
    public static void toLowerCase(String a) {
        for (int i = 0; i< a.length(); i++) {
            char character = a.charAt(i);
            if (65 <= character && character <= 90) {
            	character = (char)( (character + 32) ); 
            }
            System.out.print(character);
         }
     }
    public static void main(String[] args) {
		String str = "HELLO WORLD";
        toLowerCase(str);
    }
} 
```
Output
```
HELLO WORLD --> hello world
```
## Q. Write a program to create deadlock between two threads?
```java
public class DeadlockExample  
{  	
	// Creating Object Locks
    static Object ObjectLock1 = new Object();
    static Object ObjectLock2 = new Object();
   
    private static class ThreadName1 extends Thread {
      public void run() {
         synchronized (ObjectLock1) {
            System.out.println("Thread 1: Has  ObjectLock1");
            /* Adding sleep() method so that
               Thread 2 can lock ObjectLock2 */
            try { 
                Thread.sleep(100);
            }
            catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("Thread 1: Waiting for ObjectLock 2");
            /*Thread 1 has ObjectLock1 
              but waiting for ObjectLock2*/
            synchronized (ObjectLock2) {
               System.out.println("Thread 1: No DeadLock");
            }
         }
      }
   }
   private static class ThreadName2 extends Thread {
      public void run() {
         synchronized (ObjectLock2) {
            System.out.println("Thread 2: Has  ObjectLock2");
            /* Adding sleep() method so that
               Thread 1 can lock ObjectLock1 */
            try { 
                Thread.sleep(100);
            }
            catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("Thread 2: Waiting for ObjectLock 1");
            /*Thread 2 has ObjectLock2 
              but waiting for ObjectLock1*/
            synchronized (ObjectLock1) {
               System.out.println("Thread 2: No DeadLock");
            }
         }
      }
   }
   
   public static void main(String args[]) {
      ThreadName1 thread1 = new ThreadName1();
      ThreadName2 thread2 = new ThreadName2();
      thread1.start();
      thread2.start();
   }
} 
```
Output
```
Thread 1: Has  ObjectLock1
Thread 2: Has  ObjectLock2
Thread 2: Waiting for ObjectLock 1
Thread 1: Waiting for ObjectLock 2
```
**To get the Deadlocak details**  
```
To get the Thread PID
cmd > jps   // 9004 Test
cmd > jcmd 9004 Thread.print


9004:
2019-12-30 20:39:13
Full thread dump Java HotSpot(TM) 64-Bit Server VM (25.121-b13 mixed mode):

"DestroyJavaVM" #12 prio=5 os_prio=0 tid=0x000000000261d800 nid=0x25a8 waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"Thread-1" #11 prio=5 os_prio=0 tid=0x000000001d746000 nid=0xe78 waiting for monitor entry [0x000000001de9e000]
   java.lang.Thread.State: BLOCKED (on object monitor)
        at Test$ThreadName2.run(Test.java:45)
        - waiting to lock <0x000000076b3eae68> (a java.lang.Object)
        - locked <0x000000076b3eae78> (a java.lang.Object)

"Thread-0" #10 prio=5 os_prio=0 tid=0x000000001d745000 nid=0x468c waiting for monitor entry [0x000000001dd9e000]
   java.lang.Thread.State: BLOCKED (on object monitor)
        at Test$ThreadName1.run(Test.java:24)
        - waiting to lock <0x000000076b3eae78> (a java.lang.Object)
        - locked <0x000000076b3eae68> (a java.lang.Object)

"Service Thread" #9 daemon prio=9 os_prio=0 tid=0x000000001d6c1000 nid=0x2c08 runnable [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"C1 CompilerThread2" #8 daemon prio=9 os_prio=2 tid=0x000000001bd6c000 nid=0x265c waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"C2 CompilerThread1" #7 daemon prio=9 os_prio=2 tid=0x000000001bd46000 nid=0x461c waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"C2 CompilerThread0" #6 daemon prio=9 os_prio=2 tid=0x000000001bd3c800 nid=0x2bb8 waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"Attach Listener" #5 daemon prio=5 os_prio=2 tid=0x000000001bd3b000 nid=0x2b2c waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"Signal Dispatcher" #4 daemon prio=9 os_prio=2 tid=0x000000001bd39800 nid=0x55e4 runnable [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"Finalizer" #3 daemon prio=8 os_prio=1 tid=0x000000001bd29000 nid=0x32fc in Object.wait() [0x000000001d09f000]
   java.lang.Thread.State: WAITING (on object monitor)
        at java.lang.Object.wait(Native Method)
        - waiting on <0x000000076b388ec8> (a java.lang.ref.ReferenceQueue$Lock)
        at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:143)
        - locked <0x000000076b388ec8> (a java.lang.ref.ReferenceQueue$Lock)
        at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:164)
        at java.lang.ref.Finalizer$FinalizerThread.run(Finalizer.java:209)

"Reference Handler" #2 daemon prio=10 os_prio=2 tid=0x0000000002751000 nid=0x39e4 in Object.wait() [0x000000001cf9f000]
   java.lang.Thread.State: WAITING (on object monitor)
        at java.lang.Object.wait(Native Method)
        - waiting on <0x000000076b386b68> (a java.lang.ref.Reference$Lock)
        at java.lang.Object.wait(Object.java:502)
        at java.lang.ref.Reference.tryHandlePending(Reference.java:191)
        - locked <0x000000076b386b68> (a java.lang.ref.Reference$Lock)
        at java.lang.ref.Reference$ReferenceHandler.run(Reference.java:153)

"VM Thread" os_prio=2 tid=0x000000001bd06800 nid=0x5990 runnable

"GC task thread#0 (ParallelGC)" os_prio=0 tid=0x0000000002676800 nid=0x51d8 runnable

"GC task thread#1 (ParallelGC)" os_prio=0 tid=0x0000000002678000 nid=0x489c runnable

"GC task thread#2 (ParallelGC)" os_prio=0 tid=0x000000000267a000 nid=0x2e5c runnable

"GC task thread#3 (ParallelGC)" os_prio=0 tid=0x000000000267b800 nid=0x52ec runnable

"VM Periodic Task Thread" os_prio=2 tid=0x000000001d6cb000 nid=0x45ec waiting on condition

JNI global references: 5


Found one Java-level deadlock:
=============================
"Thread-1":
  waiting to lock monitor 0x00000000027572b8 (object 0x000000076b3eae68, a java.lang.Object),
  which is held by "Thread-0"
"Thread-0":
  waiting to lock monitor 0x0000000002759d58 (object 0x000000076b3eae78, a java.lang.Object),
  which is held by "Thread-1"

Java stack information for the threads listed above:
===================================================
"Thread-1":
        at Test$ThreadName2.run(Test.java:45)
        - waiting to lock <0x000000076b3eae68> (a java.lang.Object)
        - locked <0x000000076b3eae78> (a java.lang.Object)
"Thread-0":
        at Test$ThreadName1.run(Test.java:24)
        - waiting to lock <0x000000076b3eae78> (a java.lang.Object)
        - locked <0x000000076b3eae68> (a java.lang.Object)

Found 1 deadlock.
```
## Q. How to find the word with the highest frequency from a file in Java?
```java
public class MostRepeatedWord  
{  	
	public static void main(String[] args) {	
		
		int count = 0;
		String mostRepeatedWord = null;
		
		// Creating wordCountMap which holds words as keys and their occurrences as values
		HashMap<String, Integer> wordCountMap = new HashMap<String, Integer>();
	
		try (
			BufferedReader	reader = new BufferedReader(new FileReader("C:\\file.txt"));
		) {
			// Reading the first line into currentLine
			String currentLine = reader.readLine();
			
			while (currentLine != null) {	
				// splitting the currentLine into words
				String[] words = currentLine.toLowerCase().split(" ");
				
				for (String word : words) {
					// If word is already present in wordCountMap, updating its count
					if(wordCountMap.containsKey(word)) {	
						wordCountMap.put(word, wordCountMap.get(word)+1);
					} else {
						wordCountMap.put(word, 1);
					}
				}
				// Reading next line into currentLine
				currentLine = reader.readLine();
			}
			
			// Getting the most repeated word and its occurrence
			Set<Entry<String, Integer>> entrySet = wordCountMap.entrySet();
			
			for (Entry<String, Integer> entry : entrySet) {
				if(entry.getValue() > count) {
					mostRepeatedWord = entry.getKey();
					count = entry.getValue();
				}
			}
			
			System.out.println("The most repeated word in input file is: "+mostRepeatedWord);
			System.out.println("Number Of Occurrences: "+count);
		} 
		catch (IOException e) {
			e.printStackTrace();
		}
	}
} 
```
Output
```
The most repeated word in input file is: java
Number Of Occurrences: 5
```
## Q. How to sort a text file in java?
```java
public class SortTextFile 
{  	
	public static void main(String[] args) {
		
		//Create an ArrayList object to hold the lines of input file
		ArrayList<String> lines = new ArrayList<String>();
		
		try (
			BufferedReader	reader = new BufferedReader(new FileReader("C:\\file.txt"));
			BufferedWriter	writer = new BufferedWriter(new FileWriter("C:\\output.txt"));
		)
		{
			//Reading all the lines of input file one by one and adding them into ArrayList
			String currentLine = reader.readLine();
			
			while (currentLine != null) {
				lines.add(currentLine);	
				currentLine = reader.readLine();
			}
			
			//Sorting the ArrayList
			Collections.sort(lines);
			
			//Writing sorted lines into output file
			for (String line : lines) {
				writer.write(line);
				writer.newLine();
			}
		} 
		catch (IOException e) {
			e.printStackTrace();
		}
	}	
} 
```
Output
```
20
50
Enterprise JavaBeans (EJB)
J2EE Connector Architecture (J2EE-CA, or JCA)
Java Database Connectivity (JDBC)
Java Message Service (JMS)
Java Naming and Directory Interface (JNDI)
Java Servlets
Java Transaction API (JTA)
Java Transaction Service (JTS)
JavaMail
JavaServer Pages (JSP)
```
## Q. Find middle index of array where both ends sum is equal?
```java
public class FindMiddleIndex 
{
    public static int findMiddleIndex(int[] array) throws Exception {

        int endIndex = array.length - 1;
        int startIndex = 0;
        int leftSum = 0;
        int rightSum = 0;
        while (true) {
            if (leftSum > rightSum) {
                rightSum += array[endIndex--];
            } else {
                leftSum += array[startIndex++];
            }
            if (startIndex > endIndex) {
                if (leftSum == rightSum) {
                    break;
                } else {
                    throw new Exception("No such combination found in the array.");
                }
            }
        }
        return endIndex;
    }

    public static void main(String[] args) {
        int[] array = {1, 7, 5, 2, 8, 3};
        try {
            int index = findMiddleIndex(array);
            System.out.println("Sum preceding the index " + index + " is equal to sum succeeding the index " + index);
        } catch (Exception ex) {
            System.out.println(ex.getMessage());
        }
    }
}
```
Output
```
Sum preceding the index 2 is equal to sum succeeding the index 2
```
## Q. What do the expression 1.0 / 0.0 will return? will it throw Exception? any compile time error? 
* Output: Infinity, No Exception
## Q. How do you check the equality of two arrays in java?
* Arrays.equals() 
## Q. How to remove duplicate elements from ArrayList in java?
**Using Java 8 Stream.distinct()**  

**Approach**  

1. Get the ArrayList with duplicate values.
1. Create a new List from this ArrayList.
1. Using Stream().distinct() method which return distinct object stream.
1. convert this object stream into List

```java
/**
* Java program to remove duplicates from ArrayList
*
**/ 
import java.util.ArrayList; 
import java.util.Arrays; 
import java.util.List; 
import java.util.stream.Collectors; 

class ArrayListExample 
{ 
	public static void main(String[] args) { 
		// input list with duplicates 
		List<Integer> list = new ArrayList<>(Arrays.asList(1, 10, 1, 2, 2, 3, 10, 3, 3, 4, 5, 5)); 
			
		System.out.println("ArrayList with duplicates: "+ list); 

		// Construct a new list from the set constucted from elements 
		// of the original list 
		List<Integer> newList = list.stream().distinct().collect(Collectors.toList()); 

		System.out.println("ArrayList with duplicates removed: "+ newList); 
	} 
} 
```
Output
```
ArrayList with duplicates: [1, 10, 1, 2, 2, 3, 10, 3, 3, 4, 5, 5]
ArrayList with duplicates removed: [1, 10, 2, 3, 4, 5]
```
## Q. Write a java program to append text to a file?
```java
public class Test 
{  	
	public static void main(String[] args) {
        String path = "C:\\file.txt";
        String text = "Append new text";
        try (
        	FileWriter fw = new FileWriter(path, true);
        ) {
            fw.write(text);
        }
        catch(IOException e) {
        	e.printStackTrace();
        }
    }
} 
```
## Q. Write a program to sort a map by value?
```java
public class SortMapExample 
{
	public static Map<String, String> sortMap(Map<String, String> map) {

        List<Map.Entry<String, String>> capitalList = new LinkedList<>(map.entrySet());
        Collections.sort(capitalList, (o1, o2) -> o1.getValue().compareTo(o2.getValue()));
        LinkedHashMap<String, String> result = new LinkedHashMap<>();
        
        for (Map.Entry<String, String> entry : capitalList) {
            result.put(entry.getKey(), entry.getValue());
        }
        return result;
    }
    public static void main(String[] args) {

    	LinkedHashMap<String, String> capitals = new LinkedHashMap<>();
        capitals.put("Nepal", "Kathmandu");
        capitals.put("India", "New Delhi");
        capitals.put("United States", "Washington");
        capitals.put("England", "London");
        capitals.put("Australia", "Canberra");
        
        Map<String, String> result = sortMap(capitals);
        
        for (Map.Entry<String, String> entry : result.entrySet()) {
            System.out.print("Key: " + entry.getKey());
            System.out.println(", Value: " + entry.getValue());
        }
    } 
}
```
Output
```
Key: Australia,     Value: Canberra
Key: Nepal,         Value: Kathmandu
Key: England,       Value: London
Key: India,         Value: New Delhi
Key: United States, Value: Washington
```
## Q. How to find duplicate number on Integer array in Java?
```java
public class DuplicatesInArray 
{
	public static void main(String[] args) {
		
        int[] array = {4, 2, 4, 5, 2, 3, 1};  
        Set<Integer> set = new HashSet<>();
         
        for(int i = 0; i < array.length ; i++) {
            //If same integer is already present then add method will return FALSE 
            if(set.add(array[i]) == false) {
                System.out.println("Duplicate Element Found: " + array[i]);
            }
        }
    } 
}
```
Output
```
Duplicate Element: 4
Duplicate Element: 2
```
## Q. How to find largest and smallest number in unsorted array?
```java
public class FindBiggestSmallestNumber  
{
	public static void main(String[] args) {
		
        int numbers[] = {85, 91, 7, 98, 71, 57, 20, 38, 97, 6};
        int smallest = numbers[0];
        int biggest = numbers[0];
       
        for(int i = 1; i < numbers.length; i++) {
                if(numbers[i] > biggest)
                        biggest = numbers[i];
                else if (numbers[i] < smallest)
                        smallest = numbers[i];      
        }
        System.out.println("Smallest Number is : " + smallest);
        System.out.println("Largest Number is : " + biggest);
    }
}
```
Output
```
Smallest Number is: 6
Largest Number is: 98
```
## Q. FizzBuzz problem:- Write a program which return "fizz" if the number is a multiplier of 3, return "buzz" if its multiplier of 5 and return "fizzbuzz" if the number is divisible by both 3 and 5. If the number is not divisible by either 3 or 5 then it should just return the number itself?
```java
public class FizzBuzzExample 
{
	public static String fizzBuzz(int number) {
        if (number % 3 == 0) {
            if (number % 5 == 0) {
                return "fizzbuzz";
            } else {
                return "fizz";
            }
        } else if (number % 5 == 0) {
            return "buzz";
        }
        return String.valueOf(number);
    }
	public static void main(String[] args) {
		System.out.println(fizzBuzz(15));
	}
}
```
Output
```
3   ---> fizz
15  ---> fizzbuzz
23  ---> 23 
```
## Q. Write a Comparator in Java to compare two employees based upon their name, departments and age?
**Name Sorter**
```java
import java.util.Comparator;
 
public class NameSorter implements Comparator<Employee>{
 
    @Override
    public int compare(Employee o1, Employee o2) {
        return o1.getName().compareTo(o2.getName());
    }
}
```
**Department Sorter**
```java
import java.util.Comparator;
 
public class DepartmentSorter implements Comparator<Employee> {

    @Override
    public int compare(Employee o1, Employee o2) {
        return o1.getDepartment().compareTo(o2.getDepartment());
    }
}
```
**Age Sorter**
```java
import java.util.Comparator;
 
public class AgeSorter implements Comparator<Employee> {
    @Override
    public int compare(Employee o1, Employee o2) {
        return o1.getAge() - o2.getAge();
    }
}
```
**compare with Comparator**  
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
 
public class TestSorting 
{
    public static void main(String[] args) {

        Employee e1 = new Employee(1, "aTestName", "dLastName", 34);
        Employee e2 = new Employee(2, "nTestName", "pLastName", 30);
        Employee e3 = new Employee(3, "kTestName", "sLastName", 31);
        Employee e4 = new Employee(4, "dTestName", "zLastName", 25);
 
        List<Employee> employees = new ArrayList<Employee>();
        employees.add(e2);
        employees.add(e3);
        employees.add(e1);
        employees.add(e4);
 
        // UnSorted List
        System.out.println(employees);
 
        Collections.sort(employees);
 
        // Default Sorting by employee id
        System.out.println(employees);
 
        Collections.sort(employees, new NameSorter());
 
        // Sorted by Employee Name
        System.out.println(employees);
 
        Collections.sort(employees, new DepartmentSorter());
 
        // Sorted by Department Name
        System.out.println(employees);
 
        Collections.sort(employees, new AgeSorter());
 
        // Sorted by Employee Age
        System.out.println(employees);
    }
}
```
Output:
```
//Unsorted
 
[Employee : 2 - nTestName - pLastName - 30
, Employee : 3 - kTestName - sLastName - 31
, Employee : 1 - aTestName - dLastName - 34
, Employee : 4 - dTestName - zLastName - 25]
 
//Default sorting based on employee id
 
[Employee : 1 - aTestName - dLastName - 34
, Employee : 2 - nTestName - pLastName - 30
, Employee : 3 - kTestName - sLastName - 31
, Employee : 4 - dTestName - zLastName - 25]

```
## Q. Write a program to convert Decimal To Binary, Decimal To Octal and Decimal to HexaDecimal in Java?
```java
public class DecimalToBinary 
{
	public static void main(String[] args) {
		
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter the Decimal Number: ");
        int inputNumber = sc.nextInt();
        
        int copyOfInputNumber = inputNumber;
        String binary = "";
        int rem = 0;
                  
        while (inputNumber > 0) {
            rem = inputNumber % 2;
            binary =  rem + binary;
            inputNumber = inputNumber/2;
        }
        System.out.println("Binary Equivalent of "+copyOfInputNumber+" is "+binary);
    }
}
```
Output
```
Enter the Decimal Number: 5

Binary Equivalent of 5 is 101
```
```java
public class DecimalToOctal 
{
	public static void main(String[] args) {
		
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter The Decimal Number: ");
         
        int inputNumber = sc.nextInt();
        int copyOfInputNumber = inputNumber;
        String octal = "";
        int rem = 0;
        
        while (inputNumber > 0) {
            rem = inputNumber % 8;
            octal =  rem + octal;
            inputNumber = inputNumber / 8;
        } 
        System.out.println("Octal Equivalent of "+copyOfInputNumber+" is "+octal);
    }
}
```
Output
```
Enter The Decimal Number: 8

Octal Equivalent of 8 is 10
```
```java
public class DecimalToHexaDecimal 
{
	public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);     
        System.out.println("Enter The Decimal Number: ");
         
        int inputNumber = sc.nextInt();   
        int copyOfInputNumber = inputNumber;
        String hexa = "";
         
        //Digits in HexaDecimal Number System
        char hexaDecimals[] = {'0','1','2','3','4','5','6','7','8','9','A','B','C','D','E','F'};         
        int rem = 0;
        
        while (inputNumber > 0) {
            rem = inputNumber % 16;
            hexa =  hexaDecimals[rem] + hexa;
            inputNumber = inputNumber / 16;
        }
        System.out.println("HexaDecimal Equivalent of "+copyOfInputNumber+" is "+hexa);
    }
}
```
Output
```
Enter The Decimal Number: 100

HexaDecimal Equivalent of 100 is 64
```
## Q. How to rearrange array in alternating positive and negative number?
**Objective**: Given an array arrA[] which has negative and positive elements, rearrange the array in such a manner that positive and negative elements occupy the alternate positions and if there are extra positive or negative elements are left then append it to the end.

Example:
```
int[] arrA = { 1, 2, -3, -4, -5, 6, -7, -8, 9, 10, -11, -12, -13, 14 };
Output: -13 9 -3 10 -5 6 -7 2 -12 1 -11 14 -4 -8
```
**Quick Sort Technique**

* Take the pivot element as 0 and do the first round of Quick Sort.
* After above step you will have all the negative elements on left and all the positive elements on the right.
* Then just the every alternate element in the left half (negative elements) with the elements in the right (positive elements)

```java
public class RearragePostiveNegativeAlternatively 
{
	public void rerrange(int[] arrA) {
		int pivot = 0;
		int left = 0;
		int right = arrA.length - 1;
		while (right > left) {
			while (arrA[left] < 0 && left < right)
				left++;
			while (arrA[right] > 0 && left < right)
				right--;
			if (left < right) {

				int temp = arrA[left];
				arrA[left] = arrA[right];
				arrA[right] = temp;
				left++;
				right--;
			}
		}
		// At the point all the negative elements on the left half and
		// positive elements on the right half of the array
		// swap the every alternate element in the left half (negative
		// elements) with the elements in the right (positive elements)
		left = 1;
		int high = 0;
		while (arrA[high] < 0)
			high++;
		right = high;
		while (arrA[left] < 0 && right < arrA.length) {
			int temp = arrA[left];
			arrA[left] = arrA[right];
			arrA[right] = temp;
			left = left + 2;
			right++;
		}
		for (int i = 0; i < arrA.length; i++) {
			System.out.print("  " + arrA[i]);
		}
	}

	public static void main(String[] args) throws java.lang.Exception {
		int[] arrA = { 1, 2, -3, -4, -5, 6, -7, -8, 9, 10, -11, -12, -13, 14 };
		RearragePostiveNegativeAlternatively i = new RearragePostiveNegativeAlternatively();
		i.rerrange(arrA);
	}
}
```
Output
```
-13 9 -3 10 -5 6 -7 2 -12 1 -11 14 -4 -8
```
## Q. How Convert lower to upper case without using toUppercase() in java?

```java
/**
* Java program to Convert lower to upper case
* 
**/
public class toLowerCase {

    public static void main(String[] args) {
        toLowerCase(args[0]);
    }

    public static void toLowerCase(String a) {

        for (int i = 0; i< a.length(); i++) {
            char aChar = a.charAt(i);
            if (65 <= aChar && aChar<=90) {
                aChar = (char)( (aChar + 32) ); 
            }
            System.out.print(aChar);
         }
     }
}    
```
<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. Explain deadlock condition in-between two threads with example?

```java
public class DeadLockSimulator {
     
    public static Object Lock1 = new Object();
    public static Object Lock2 = new Object();

    private static class FirstThread extends Thread {
        public void run() {
            synchronized (Lock1) {
            System.out.println("Thread 1: Holding lock 1...");
            try { Thread.sleep(10); } catch (Exception e) {}
            System.out.println("Thread 1: Waiting for lock 2...");
            synchronized (Lock2) {
                System.out.println("Thread 1: Holding lock 1 & 2...");
            }
            }
        }
    }
    
    private static class SecondThread extends Thread {
        public void run() {
            synchronized (Lock2) {
            System.out.println("Thread 2: Holding lock 2...");
            try { Thread.sleep(10); } catch (Exception e) {}
            System.out.println("Thread 2: Waiting for lock 1...");
            synchronized (Lock1) {
                System.out.println("Thread 2: Holding lock 1 & 2...");
            }
            }
        }
    }
     
    public static void main(String args[]) {
         
        new FirstThread().start();
        new SecondThread().start();
    }
}
```
Output:
```java
"Thread-1" prio=6 tid=0x0000000007319000 nid=0x7cd3c waiting for monitor entry [0x0000000008a3f000]
   java.lang.Thread.State: BLOCKED (on object monitor)
    at com.tier1app.DeadLockSimulator$SecondThread.run(DeadLockSimulator.java:29)
    - waiting to lock 0x00000007ac3b1970 (a java.lang.Object)
    - locked 0x00000007ac3b1980 (a java.lang.Object)
 
   Locked ownable synchronizers:
    - None
 
"Thread-0" prio=6 tid=0x0000000007318800 nid=0x7da14 waiting for monitor entry [0x000000000883f000]
   java.lang.Thread.State: BLOCKED (on object monitor)
    at com.tier1app.DeadLockSimulator$FirstThread.run(DeadLockSimulator.java:16)
    - waiting to lock 0x00000007ac3b1980 (a java.lang.Object)
    - locked 0x00000007ac3b1970 (a java.lang.Object)
 
   Locked ownable synchronizers:
    - None
```
## Q. How do you sort out items in ArrayList in reverse direction?
Reverse order of all elements of Java ArrayList
```java
import java.util.ArrayList;
import java.util.Collections;

public class MainClass {
  public static void main(String[] args) {
    ArrayList<String> arrayList = new ArrayList<String>();

    arrayList.add("A");
    arrayList.add("B");
    arrayList.add("C");
    arrayList.add("D");
    arrayList.add("E");

    System.out.println(arrayList);
    Collections.reverse(arrayList);
    System.out.println(arrayList);
  }
}
```
<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. Find the shortest-path weights d(s, v) from given source s for all vertices v present in the graph.

![Dijkstras Algorithm](https://github.com/learning-zone/java-interview-questions/blob/master/assets/shorted-path-dijkstras.png)

For Example:


Path from vertex A to vertex B has min cost of 4 & the route is [ A -> E -> B ]

Path from vertex A to vertex C has min cost of 6 & the route is [ A -> E -> B -> C ]

Path from vertex A to vertex D has min cost of 5 & the route is [ A -> E -> D ]

Path from vertex A to vertex E has min cost of 3 & the route is [ A -> E ]



Dijkstra’s Algorithm is an algorithm for finding the shortest paths between nodes in a graph. For a given source node in the graph, the algorithm finds the shortest path between that node and every other node. It can also be used for finding the shortest paths from a single node to a single destination node by stopping the algorithm once the shortest path to the destination node has been determined.

Dijkstra’s Algorithm is based on the principle of relaxation, in which an approximation to the correct distance is gradually replaced by more accurate values until shortest distance is reached. The approximate distance to each vertex is always an overestimate of the true distance, and is replaced by the minimum of its old value with the length of a newly found path. It uses a priority queue to greedily select the closest vertex that has not yet been processed and performs this relaxation process on all of its outgoing edges.

```java
import java.util.*;

// Data structure to store graph edges
class Edge
{
	int source, dest, weight;

	public Edge(int source, int dest, int weight) {
		this.source = source;
		this.dest = dest;
		this.weight = weight;
	}
};

// data structure to store heap nodes
class Node {
	int vertex, weight;

	public Node(int vertex, int weight) {
		this.vertex = vertex;
		this.weight = weight;
	}
};

// class to represent a graph object
class Graph
{
	// A List of Lists to represent an adjacency list
	List<List<Edge>> adjList = null;

	// Constructor
	Graph(List<Edge> edges, int N) {

		adjList = new ArrayList<>(N);

		for (int i = 0; i < N; i++) {
			adjList.add(i, new ArrayList<>());
		}

		// add edges to the undirected graph
		for (Edge edge: edges) {
			adjList.get(edge.source).add(edge);
		}
	}
}

class Main
{
	private static void printRoute(int prev[], int i) {
		if (i < 0)
			return;

		printRoute(prev, prev[i]);
		System.out.print(i + " ");
	}

	// Run Dijkstra's algorithm on given graph
	public static void shortestPath(Graph graph, int source, int N) {

		// create min heap and push source node having distance 0
		PriorityQueue<Node> minHeap = new PriorityQueue<>((lhs, rhs) -> lhs.weight - rhs.weight);
		minHeap.add(new Node(source, 0));

		// set infinite distance from source to v initially
		List<Integer> dist = new ArrayList<>(Collections.nCopies(N, Integer.MAX_VALUE));

		// distance from source to itself is zero
		dist.set(source, 0);

		// boolean array to track vertices for which minimum
		// cost is already found
		boolean[] done = new boolean[N];
		done[0] = true;

		// stores predecessor of a vertex (to print path)
		int prev[] = new int[N];
		prev[0] = -1;

		// run till minHeap is not empty
		while (!minHeap.isEmpty()) {

			// Remove and return best vertex
			Node node = minHeap.poll();

			// get vertex number
			int u = node.vertex;

			// do for each neighbor v of u
			for (Edge edge: graph.adjList.get(u)) {

				int v = edge.dest;
				int weight = edge.weight;

				// Relaxation step
				if (!done[v] && (dist.get(u) + weight) < dist.get(v)) {
					dist.set(v, dist.get(u) + weight);
					prev[v] = u;
					minHeap.add(new Node(v, dist.get(v)));
				}
			}

			// marked vertex u as done so it will not get picked up again
			done[u] = true;
		}

		for (int i = 1; i < N; ++i) {
			System.out.print("Path from vertex 0 to vertex " + i + " has minimum cost of "
								+ dist.get(i) + " and the route is [ ");
			printRoute(prev, i);
			System.out.println("]");
		}
	}

	public static void main(String[] args) {
        
		// initialize edges as per above diagram
		// (u, v, w) triplet represent undirected edge from
		// vertex u to vertex v having weight w
		List<Edge> edges = Arrays.asList(
				new Edge(0, 1, 10), new Edge(0, 4, 3),
				new Edge(1, 2, 2), new Edge(1, 4, 4),
				new Edge(2, 3, 9), new Edge(3, 2, 7),
				new Edge(4, 1, 1), new Edge(4, 2, 8),
				new Edge(4, 3, 2)
		);

		// Set number of vertices in the graph
		final int N = 5;

		// construct graph
		Graph graph = new Graph(edges, N);

		shortestPath(graph, 0, N);
	}
}
```
Output
```
Path from vertex 0 to vertex 1 has minimum cost of 4 and the route is [ 0 4 1 ]
Path from vertex 0 to vertex 2 has minimum cost of 6 and the route is [ 0 4 1 2 ]
Path from vertex 0 to vertex 3 has minimum cost of 5 and the route is [ 0 4 3 ]
Path from vertex 0 to vertex 4 has minimum cost of 3 and the route is [ 0 4 ]
```
<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to display 10 random numbers using forEach()?

```java
( new  Random ())
    .ints ()
    .limit ( 10 )
    .forEach ( System . out :: println);
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How can I display unique squares of numbers using the method map()?

```java
Stream 
    .of ( 1 , 2 , 3 , 2 , 1 )
    .map (s -> s * s)
    .distinct ()
    .collect ( Collectors . toList ())
    .forEach ( System . out :: println);
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to display the number of empty lines using the method filter()?

```java
System.out.println (
     Stream 
        .of ( " Hello " , " " , " , " , " world " , " ! " )
        .filter ( String :: isEmpty)
        .count ());
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to display 10 random numbers in ascending order?

```java
( new  Random ())
    .ints ()
    .limit ( 10 )
    .sorted ()
    .forEach ( System . out :: println);
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to find the maximum number in a set?

```java
Stream 
    .of ( 5 , 3 , 4 , 55 , 2 )
    .mapToInt (a -> a)
    .max ()
    .getAsInt (); // 55
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to find the minimum number in a set?

```java
Stream 
    .of ( 5 , 3 , 4 , 55 , 2 )
    .mapToInt (a -> a)
    .min ()
    .getAsInt (); // 2
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to get the sum of all numbers in a set?

```java
Stream 
    .of( 5 , 3 , 4 , 55 , 2 )
    .mapToInt()
    .sum(); // 69
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to get the average of all numbers?

```java
Stream 
    .of ( 5 , 3 , 4 , 55 , 2 )
    .mapToInt (a -> a)
    .average ()
    .getAsDouble (); // 13.8
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
## Q. How to get current date using Date Time API from Java 8?

```java
LocalDate as.now();
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to add 1 week, 1 month, 1 year, 10 years to the current date using the Date Time API?

```java
LocalDate as.now ().plusWeeks ( 1 );
LocalDate as.now ().plusMonths ( 1 );
LocalDate as.now ().plusYears ( 1 );
LocalDate as.now ().plus ( 1 , ChronoUnit.DECADES );
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to get the next Tuesday using the Date Time API?

```java
LocalDate as.now().with( TemporalAdjusters.next ( DayOfWeek.TUESDAY ));
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to get the current time accurate to milliseconds using the Date Time API?

```java
new  Date ().toInstant ();
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to get the second Saturday of the current month using the Date Time API?

```java
LocalDate 
    .of ( LocalDate.Now ().GetYear (), LocalDate.Now ().GetMonth (), 1 )
    .with ( TemporalAdjusters.nextOrSame ( DayOfWeek.SATURDAY ))
    .with ( TemporalAdjusters.next ( DayOfWeek.SATURDAY ));
```
<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to get the current time in local time accurate to milliseconds using the Date Time API?

```java
LocalDateTime.ofInstant ( new  Date().toInstant(), ZoneId.systemDefault());
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. How to sort a list of strings using a lambda expression?

```java
public  static  List < String > sort ( List < String > list) {
    Collections.sort(list, (a, b) -> a.compareTo(b));
    return list;
}
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find if there is a sub array with sum equal to zero?

```java
import java.util.HashMap;

public class SubarraySumZero {

    public static boolean hasSubarrayWithSumZero(int[] nums) {
        HashMap<Integer, Integer> sumMap = new HashMap<>();
        sumMap.put(0, -1); // Initialize the hashmap with sum = 0 at index -1 (before the array starts)
        int cumulativeSum = 0;

        for (int i = 0; i < nums.length; i++) {
            cumulativeSum += nums[i];

            if (sumMap.containsKey(cumulativeSum)) {
                // Subarray with sum 0 found from index (sumMap.get(cumulativeSum) + 1) to i
                return true;
            } else {
                sumMap.put(cumulativeSum, i);
            }
        }

        return false; // No subarray with sum 0 found
    }

    public static void main(String[] args) {
        int[] nums = {4, 2, -3, 1, 6};
        boolean result = hasSubarrayWithSumZero(nums);
        System.out.println("Subarray with sum 0 exists: " + result); // Output: Subarray with sum 0 exists: true
    }
}
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to remove a given element from array in Java?

To remove a given element from an array in Java, you need to perform the following steps:

1. Find the index of the element you want to remove in the array.
2. If the element is found, remove it by shifting all the elements after it one position to the left.

Here's a Java method that demonstrates this process:

```java
import java.util.Arrays;

public class ArrayUtils {

    public static int[] removeElementFromArray(int[] array, int elementToRemove) {
        // Find the index of the element to remove
        int indexToRemove = -1;
        for (int i = 0; i < array.length; i++) {
            if (array[i] == elementToRemove) {
                indexToRemove = i;
                break;
            }
        }

        // If the element is not found, return the original array
        if (indexToRemove == -1) {
            return array;
        }

        // Create a new array with size reduced by 1
        int[] newArray = new int[array.length - 1];

        // Copy the elements before the element to remove
        System.arraycopy(array, 0, newArray, 0, indexToRemove);

        // Copy the elements after the element to remove
        System.arraycopy(array, indexToRemove + 1, newArray, indexToRemove, array.length - indexToRemove - 1);

        return newArray;
    }

    public static void main(String[] args) {
        int[] originalArray = {1, 2, 3, 4, 5};
        int elementToRemove = 3;

        int[] newArray = removeElementFromArray(originalArray, elementToRemove);

        System.out.println("Original Array: " + Arrays.toString(originalArray));
        System.out.println("Element to Remove: " + elementToRemove);
        System.out.println("New Array: " + Arrays.toString(newArray));
    }
}
```

In this example, the method `removeElementFromArray` takes an integer array `array` and an `elementToRemove`. It first finds the index of the element to remove, and then it creates a new array with size reduced by 1. It then copies the elements before the element to remove and the elements after the element to remove into the new array using `System.arraycopy`. The result is the new array with the specified element removed.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find trigonometric values of an angle in Java?

To find trigonometric values (sine, cosine, and tangent) of an angle in Java, you can use the `Math` class provided by the Java standard library. The `Math` class contains various static methods for common mathematical operations, including trigonometric functions.

Here's how you can find the trigonometric values of an angle in Java:

```java
import java.lang.Math;

public class TrigonometricValues {

    public static void main(String[] args) {
        double angleInDegrees = 30.0; // The angle in degrees

        // Convert the angle from degrees to radians since Java trigonometric functions work with radians
        double angleInRadians = Math.toRadians(angleInDegrees);

        // Calculate trigonometric values
        double sineValue = Math.sin(angleInRadians);
        double cosineValue = Math.cos(angleInRadians);
        double tangentValue = Math.tan(angleInRadians);

        // Print the results
        System.out.println("Angle in degrees: " + angleInDegrees);
        System.out.println("Angle in radians: " + angleInRadians);
        System.out.println("Sine value: " + sineValue);
        System.out.println("Cosine value: " + cosineValue);
        System.out.println("Tangent value: " + tangentValue);
    }
}
```

In this example, we use the `Math.toRadians()` method to convert the angle from degrees to radians because the trigonometric functions (`Math.sin()`, `Math.cos()`, and `Math.tan()`) in Java work with radians. Then, we calculate the trigonometric values of the angle and print the results.

Note that trigonometric functions expect the angle to be in radians, so make sure to convert the angle from degrees to radians before using them. The `Math.toRadians()` method makes this conversion easy.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Reverse and add until you get a palindrome

To reverse and add until you get a palindrome in Java, you can create a function that takes an integer as input, reverses it, adds it to the original number, and then checks if the result is a palindrome. If the result is not a palindrome, repeat the process until you obtain one.

Here's a Java function that implements this logic:

```java
public class PalindromeReverseAndAdd {

    public static void main(String[] args) {
        int number = 123; // Replace this with your desired number

        int palindrome = findPalindrome(number);
        System.out.println("Palindrome: " + palindrome);
    }

    public static int findPalindrome(int number) {
        int reverse = 0;
        int originalNumber = number;

        while (true) {
            // Reverse the number
            reverse = reverseNumber(number);

            // Add the reversed number to the original number
            number += reverse;

            // Check if the result is a palindrome
            if (isPalindrome(number)) {
                return number;
            }
        }
    }

    public static int reverseNumber(int number) {
        int reverse = 0;

        while (number != 0) {
            int digit = number % 10;
            reverse = reverse * 10 + digit;
            number /= 10;
        }

        return reverse;
    }

    public static boolean isPalindrome(int number) {
        int originalNumber = number;
        int reverse = 0;

        while (number != 0) {
            int digit = number % 10;
            reverse = reverse * 10 + digit;
            number /= 10;
        }

        return originalNumber == reverse;
    }
}
```

In this example, the `findPalindrome` function takes an integer `number` as input. It repeatedly reverses the number and adds the reversed number to the original number. Then, it checks if the result is a palindrome using the `isPalindrome` function. If not, it continues the process until a palindrome is found. The final palindrome is returned as the result.

The `reverseNumber` function is used to reverse the digits of an integer, and the `isPalindrome` function checks if a given number is a palindrome (reads the same forwards and backwards).

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Selection sort in Java

Selection sort is a simple sorting algorithm that repeatedly finds the minimum (or maximum, depending on the sorting order) element from the unsorted part of the array and swaps it with the first unsorted element. It continues this process until the entire array is sorted.

Here's the implementation of the selection sort algorithm in Java:

```java
public class SelectionSort {

    public static void main(String[] args) {
        int[] arr = {64, 25, 12, 22, 11};

        System.out.println("Original array:");
        printArray(arr);

        selectionSort(arr);

        System.out.println("Sorted array:");
        printArray(arr);
    }

    public static void selectionSort(int[] arr) {
        int n = arr.length;

        // One by one move the boundary of the unsorted subarray
        for (int i = 0; i < n - 1; i++) {
            // Find the minimum element in the unsorted array
            int minIndex = i;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[minIndex]) {
                    minIndex = j;
                }
            }

            // Swap the found minimum element with the first element
            int temp = arr[minIndex];
            arr[minIndex] = arr[i];
            arr[i] = temp;
        }
    }

    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

In this example, we use the `selectionSort` function to sort an integer array `arr`. The outer loop runs from the first element to the second-to-last element, defining the boundary of the unsorted subarray. The inner loop searches for the minimum element in the unsorted part of the array. Once the minimum element is found, it is swapped with the first element in the unsorted subarray. The process continues until the entire array is sorted.

The `printArray` function is a utility function used to print the elements of an array for demonstration purposes.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a singleton class in Java?

A singleton class is a class that allows only one instance of itself to be created and provides a global point of access to that instance. To create a singleton class in Java, you need to follow a few steps to ensure that only one instance is created and that it is accessible from anywhere in your code.

Here's an example of a singleton class in Java:

```java
public class Singleton {

    // Private static instance variable to hold the single instance of the class
    private static Singleton instance;

    // Private constructor to prevent direct instantiation from outside the class
    private Singleton() {
        // Initialization code (if needed)
    }

    // Public static method to access the single instance of the class
    public static Singleton getInstance() {
        // Lazy initialization: create the instance only when it's requested for the first time
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }

    // Other methods and attributes of the singleton class can be added here
}
```

In this example:

1. We have a private static variable `instance`, which holds the single instance of the class.
2. The constructor is made private to prevent direct instantiation from outside the class.
3. We provide a public static method `getInstance()` that returns the single instance of the class. This method follows the lazy initialization approach, meaning the instance is created only when it is first requested. Subsequent calls to `getInstance()` return the already created instance.
4. Other methods and attributes can be added to the singleton class as needed.

Usage of the singleton class:

```java
public class Main {
    public static void main(String[] args) {
        // Get the single instance of the Singleton class
        Singleton singleton1 = Singleton.getInstance();
        Singleton singleton2 = Singleton.getInstance();

        // Both instances refer to the same object
        System.out.println(singleton1 == singleton2); // Output: true
    }
}
```

In this usage example, `singleton1` and `singleton2` refer to the same instance of the `Singleton` class because it's a singleton, and there can only be one instance of the class throughout the program's execution.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to calculate complexity of algorithm?

Calculating the complexity of an algorithm involves analyzing the performance of the algorithm as the input size grows. The most common way to express algorithm complexity is through Big O notation, which gives an upper bound on the growth rate of the algorithm. Here's how you can calculate the complexity of an algorithm in Java:

1. Identify the operations: Analyze the algorithm and identify the basic operations that are executed repeatedly. These operations could be comparisons, assignments, arithmetic operations, etc.

2. Count the number of operations: Determine how many times each identified operation is executed based on the size of the input (usually denoted by 'n').

3. Express the complexity in Big O notation: Find the term that grows the fastest with the input size 'n' and remove the constants and lower-order terms. This will give you the Big O notation of the algorithm.

Let's take a simple example of calculating the sum of the first 'n' natural numbers as an illustration:

```java
public class AlgorithmComplexity {

    public static int sumOfNaturalNumbers(int n) {
        int sum = 0;
        for (int i = 1; i <= n; i++) {
            sum += i;
        }
        return sum;
    }

    public static void main(String[] args) {
        int n = 1000; // Input size

        int result = sumOfNaturalNumbers(n);

        System.out.println("Sum of the first " + n + " natural numbers: " + result);
    }
}
```

In this example, the `sumOfNaturalNumbers` method calculates the sum of the first 'n' natural numbers using a simple for loop. Let's analyze the complexity:

1. Identify the operations: The basic operation here is the addition operation (sum += i) inside the loop.

2. Count the number of operations: The loop runs 'n' times, and within each iteration, there is one addition operation.

3. Express the complexity in Big O notation: The loop runs 'n' times, and for each iteration, there's one addition operation. So, the total number of addition operations is proportional to 'n'. Therefore, the complexity of this algorithm is O(n).

In this case, the algorithm has a linear time complexity, denoted by O(n), because the number of operations is directly proportional to the size of the input 'n'.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Implement Producer Consumer design Pattern in Java using wait, notify and notifyAll method in Java?

The Producer-Consumer design pattern is used to solve the synchronization problem between producers (threads that produce data) and consumers (threads that consume data) when sharing a common buffer or queue. The pattern ensures that producers and consumers do not interfere with each other and operate correctly.

In Java, the `wait`, `notify`, and `notifyAll` methods are used to implement this pattern. Here's a simple implementation of the Producer-Consumer pattern using these methods:

```java
import java.util.LinkedList;
import java.util.Queue;

public class ProducerConsumer {
    private static final int CAPACITY = 5;
    private final Queue<Integer> buffer = new LinkedList<>();

    public static void main(String[] args) {
        ProducerConsumer pc = new ProducerConsumer();
        Thread producerThread = new Thread(() -> {
            try {
                pc.produce();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        });

        Thread consumerThread = new Thread(() -> {
            try {
                pc.consume();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        });

        producerThread.start();
        consumerThread.start();
    }

    public void produce() throws InterruptedException {
        int value = 0;
        while (true) {
            synchronized (this) {
                while (buffer.size() == CAPACITY) {
                    wait();
                }

                System.out.println("Producing: " + value);
                buffer.add(value++);

                // Notify the consumer that new data is available
                notifyAll();

                // Introduce some delay to simulate production time
                Thread.sleep(1000);
            }
        }
    }

    public void consume() throws InterruptedException {
        while (true) {
            synchronized (this) {
                while (buffer.isEmpty()) {
                    wait();
                }

                int value = buffer.poll();
                System.out.println("Consuming: " + value);

                // Notify the producer that the buffer has space available
                notifyAll();

                // Introduce some delay to simulate consumption time
                Thread.sleep(1000);
            }
        }
    }
}
```

In this example:

1. The `ProducerConsumer` class has a buffer of integers (a `Queue`) with a capacity of 5.
2. The `produce()` method is responsible for producing data and adding it to the buffer. It is executed by the producer thread. If the buffer is full, it waits until the consumer consumes some data and creates space in the buffer. After adding data, it notifies the consumer that new data is available.
3. The `consume()` method is responsible for consuming data from the buffer. It is executed by the consumer thread. If the buffer is empty, it waits until the producer produces some data. After consuming data, it notifies the producer that there is space available in the buffer for more data.

The producer and consumer threads execute concurrently, and the synchronization using `wait`, `notify`, and `notifyAll` ensures that they work together correctly without any data interference or deadlock.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Find Minimum numbers of platforms required for railway station in Java

To find the minimum number of platforms required for a railway station, you can use the Greedy Algorithm approach. The idea is to keep track of the trains arriving and departing at the station while maintaining the minimum number of platforms needed at any given time.

Here's a Java method that calculates the minimum number of platforms required:

```java
import java.util.Arrays;

public class MinimumPlatforms {

    public static void main(String[] args) {
        int[] arrival = {900, 940, 950, 1100, 1500, 1800};
        int[] departure = {910, 1200, 1120, 1130, 1900, 2000};

        int minPlatforms = findMinPlatforms(arrival, departure);
        System.out.println("Minimum number of platforms required: " + minPlatforms);
    }

    public static int findMinPlatforms(int[] arrival, int[] departure) {
        // Sort the arrival and departure arrays in ascending order
        Arrays.sort(arrival);
        Arrays.sort(departure);

        int minPlatforms = 1; // Minimum number of platforms required (initially one platform for the first train)
        int platformsNeeded = 1; // Tracks the number of platforms needed at any given time

        int i = 1; // Pointer for the arrival array
        int j = 0; // Pointer for the departure array

        while (i < arrival.length && j < departure.length) {
            if (arrival[i] <= departure[j]) {
                platformsNeeded++; // A new train arrives before the previous one departs, so a new platform is needed
                i++;
            } else {
                platformsNeeded--; // A train departs before a new one arrives, so one platform is freed up
                j++;
            }

            minPlatforms = Math.max(minPlatforms, platformsNeeded); // Update the minimum platforms needed
        }

        return minPlatforms;
    }
}
```

In this example, we have two arrays: `arrival` and `departure`, which represent the arrival and departure times of trains, respectively. We first sort both arrays in ascending order. Then, we use two pointers, `i` for the `arrival` array and `j` for the `departure` array, to traverse through the arrays.

As we traverse the arrays, we keep track of the number of platforms needed at any given time using the `platformsNeeded` variable. If a new train arrives before the previous one departs, we increment the `platformsNeeded` to account for the need for an additional platform. If a train departs before a new one arrives, we decrement the `platformsNeeded` as one platform becomes available.

The `minPlatforms` variable keeps track of the maximum number of platforms needed at any time during the traversal, and it represents the minimum number of platforms required for the entire schedule.

Finally, we return the `minPlatforms`, which represents the minimum number of platforms required for the given schedule of trains at the railway station.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to check whether given number is binary or not?

To check whether a given number is binary or not in Java, you can follow these steps:

1. Convert the number to a string representation.
2. Check if the string contains only '0' and '1' characters.

Here's a Java method to perform the above steps:

```java
public class BinaryChecker {

    public static void main(String[] args) {
        int number = 101010; // Replace this with your desired number

        boolean isBinary = isBinaryNumber(number);

        if (isBinary) {
            System.out.println(number + " is a binary number.");
        } else {
            System.out.println(number + " is not a binary number.");
        }
    }

    public static boolean isBinaryNumber(int number) {
        // Convert the number to a string
        String numberString = String.valueOf(number);

        // Check if the string contains only '0' and '1' characters
        return numberString.matches("[01]+");
    }
}
```

In this example, the `isBinaryNumber` method takes an integer `number` as input. It first converts the number to its string representation using `String.valueOf(number)`. Then, it uses a regular expression (`[01]+`) to check if the string contains only '0' and '1' characters. The `matches` method returns `true` if the string matches the regular expression (i.e., contains only '0' and '1' characters), indicating that the number is binary. Otherwise, it returns `false`, indicating that the number is not binary.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Armstrong number program in Java

An Armstrong number (also known as a narcissistic number, pluperfect digital invariant, or pluperfect digital number) is a number that is equal to the sum of its own digits each raised to the power of the number of digits.

Here's a Java program to check if a given number is an Armstrong number or not:

```java
public class ArmstrongNumber {

    public static void main(String[] args) {
        int number = 153; // Replace this with your desired number

        if (isArmstrongNumber(number)) {
            System.out.println(number + " is an Armstrong number.");
        } else {
            System.out.println(number + " is not an Armstrong number.");
        }
    }

    public static boolean isArmstrongNumber(int number) {
        int originalNumber = number;
        int numDigits = String.valueOf(number).length();
        int sum = 0;

        while (number > 0) {
            int digit = number % 10;
            sum += Math.pow(digit, numDigits);
            number /= 10;
        }

        return originalNumber == sum;
    }
}
```

In this example, the `isArmstrongNumber` method takes an integer `number` as input. It first calculates the number of digits in the number using `String.valueOf(number).length()`. Then, it iterates through the digits of the number using a while loop and calculates the sum of each digit raised to the power of the number of digits.

Finally, it compares the original number with the sum. If they are equal, the method returns `true`, indicating that the number is an Armstrong number. Otherwise, it returns `false`, indicating that the number is not an Armstrong number.

For example, the number 153 is an Armstrong number because `1^3 + 5^3 + 3^3 = 153`.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find sum of all digits of a number in Java?

To find the sum of all the digits of a number in Java, you can use a simple loop to extract each digit from the number and add them together. Here's a Java method that calculates the sum of all digits of a number:

```java
public class SumOfDigits {

    public static void main(String[] args) {
        int number = 12345; // Replace this with your desired number

        int sum = sumOfDigits(number);

        System.out.println("Sum of digits of " + number + " is: " + sum);
    }

    public static int sumOfDigits(int number) {
        int sum = 0;

        // Use a while loop to extract each digit and add it to the sum
        while (number > 0) {
            int digit = number % 10; // Get the last digit of the number
            sum += digit; // Add the digit to the sum
            number /= 10; // Remove the last digit from the number
        }

        return sum;
    }
}
```

In this example, the `sumOfDigits` method takes an integer `number` as input. It initializes a variable `sum` to store the sum of the digits. The method then uses a while loop to extract each digit of the number from right to left.

In each iteration of the loop:
1. The last digit of the number is obtained by calculating `number % 10`.
2. The extracted digit is added to the `sum`.
3. The last digit is removed from the number by dividing it by 10 (`number /= 10`).

The loop continues until all the digits are processed (i.e., the number becomes 0). Finally, the method returns the sum of all the digits. For example, for the number 12345, the sum of its digits would be 1 + 2 + 3 + 4 + 5 = 15.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find largest number less than a given number and without a given digit?

To find the largest number less than a given number and without a given digit, you can perform the following steps:

1. Convert the given number to a string to make it easier to manipulate its digits.
2. Starting from the given number minus one, decrement the number in a loop until you find a number that does not contain the given digit.
3. Check each number within the loop to ensure it does not contain the given digit.

Here's a Java method that implements this logic:

```java
public class LargestNumberWithoutGivenDigit {

    public static void main(String[] args) {
        int givenNumber = 54321;
        int givenDigit = 3;

        int largestNumberWithoutDigit = findLargestNumberWithoutDigit(givenNumber, givenDigit);
        System.out.println("Largest number less than " + givenNumber + " without digit " + givenDigit + " is: " + largestNumberWithoutDigit);
    }

    public static int findLargestNumberWithoutDigit(int givenNumber, int givenDigit) {
        for (int number = givenNumber - 1; number > 0; number--) {
            if (!containsDigit(number, givenDigit)) {
                return number;
            }
        }
        return -1; // If no number found without the given digit, return -1 or handle it as needed.
    }

    public static boolean containsDigit(int number, int digit) {
        String numberString = Integer.toString(number);
        String digitString = Integer.toString(digit);
        return numberString.contains(digitString);
    }
}
```

In this example, we have the `findLargestNumberWithoutDigit` method, which takes the given number and the given digit as input. It starts from the given number minus one and decrements it in a loop until it finds a number that does not contain the given digit. The method uses the `containsDigit` method to check if a number contains the given digit by converting both the number and the digit to strings and using the `contains` method.

The `containsDigit` method takes an integer `number` and an integer `digit` as input and returns `true` if the number contains the digit, and `false` otherwise.

Note: If no number is found without the given digit, the `findLargestNumberWithoutDigit` method returns -1 or you can handle it in a way that is appropriate for your use case.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Roman equivalent of a decimal number

To convert a decimal number to its Roman numeral equivalent in Java, you can use a simple algorithm that involves dividing the decimal number by specific Roman numeral values and appending the corresponding Roman numerals to a result string.

Here's a Java method that performs the conversion:

```java
import java.util.LinkedHashMap;
import java.util.Map;

public class DecimalToRoman {

    public static void main(String[] args) {
        int decimalNumber = 1987; // Replace this with your desired decimal number

        String romanNumeral = decimalToRoman(decimalNumber);

        System.out.println("Roman numeral equivalent of " + decimalNumber + " is: " + romanNumeral);
    }

    public static String decimalToRoman(int num) {
        if (num <= 0 || num > 3999) {
            throw new IllegalArgumentException("Invalid input. Please enter a number between 1 and 3999.");
        }

        // Create a mapping of decimal values to Roman numerals in descending order
        Map<Integer, String> romanNumerals = new LinkedHashMap<>();
        romanNumerals.put(1000, "M");
        romanNumerals.put(900, "CM");
        romanNumerals.put(500, "D");
        romanNumerals.put(400, "CD");
        romanNumerals.put(100, "C");
        romanNumerals.put(90, "XC");
        romanNumerals.put(50, "L");
        romanNumerals.put(40, "XL");
        romanNumerals.put(10, "X");
        romanNumerals.put(9, "IX");
        romanNumerals.put(5, "V");
        romanNumerals.put(4, "IV");
        romanNumerals.put(1, "I");

        StringBuilder result = new StringBuilder();

        // Iterate through the mapping and build the Roman numeral string
        for (Map.Entry<Integer, String> entry : romanNumerals.entrySet()) {
            int decimalValue = entry.getKey();
            String romanSymbol = entry.getValue();

            while (num >= decimalValue) {
                result.append(romanSymbol);
                num -= decimalValue;
            }
        }

        return result.toString();
    }
}
```

In this example, the `decimalToRoman` method takes an integer `num` as input and returns the Roman numeral equivalent as a string.

The method uses a LinkedHashMap to map decimal values to Roman numerals in descending order. It iterates through the mapping and repeatedly appends the Roman numeral symbols to the result string while the decimal value is less than or equal to the input `num`. The method subtracts the corresponding decimal value from `num` after appending the corresponding Roman numeral.

For example, if you call `decimalToRoman(1987)`, it will return "MCMLXXXVII," which is the Roman numeral equivalent of 1987.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to check whether user input is number or not in Java?

To check whether user input is a number or not in Java, you can use various methods based on the requirements of your application. Here are three common approaches to check if user input is a number:

1. Using `Scanner` class and `hasNextInt()` or `hasNextDouble()` method:

```java
import java.util.Scanner;

public class NumberCheck {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        if (scanner.hasNextInt()) {
            int number = scanner.nextInt();
            System.out.println(number + " is an integer.");
        } else if (scanner.hasNextDouble()) {
            double number = scanner.nextDouble();
            System.out.println(number + " is a double.");
        } else {
            String input = scanner.next();
            System.out.println(input + " is not a number.");
        }

        scanner.close();
    }
}
```

2. Using `Integer.parseInt()` or `Double.parseDouble()` with exception handling:

```java
import java.util.Scanner;

public class NumberCheck {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        String input = scanner.next();

        try {
            int number = Integer.parseInt(input);
            System.out.println(number + " is an integer.");
        } catch (NumberFormatException e1) {
            try {
                double number = Double.parseDouble(input);
                System.out.println(number + " is a double.");
            } catch (NumberFormatException e2) {
                System.out.println(input + " is not a number.");
            }
        }

        scanner.close();
    }
}
```

3. Using regular expressions to check for valid numbers:

```java
import java.util.Scanner;

public class NumberCheck {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        String input = scanner.next();

        if (input.matches("-?\\d+(\\.\\d+)?")) {
            System.out.println(input + " is a number.");
        } else {
            System.out.println(input + " is not a number.");
        }

        scanner.close();
    }
}
```

All three methods will check the user input and determine whether it is a number or not. The choice of the method depends on the specific requirements and use case of your application. The first method using `Scanner` is the simplest and handles both integer and double inputs, but it requires additional checks. The second method using `parseInt()` and `parseDouble()` is more specific and handles conversion exceptions. The third method using regular expressions provides a more flexible approach to handle different number formats, but it requires understanding regular expressions. Choose the method that suits your needs best.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to convert decimal number to binary format.

To convert a decimal number to binary format in Java, you can use a simple algorithm that involves dividing the decimal number by 2 repeatedly and keeping track of the remainders to form the binary representation.

Here's a Java program that converts a decimal number to binary format:

```java
import java.util.Scanner;

public class DecimalToBinary {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a decimal number: ");
        int decimalNumber = scanner.nextInt();

        String binaryNumber = decimalToBinary(decimalNumber);
        System.out.println("Binary representation of " + decimalNumber + " is: " + binaryNumber);

        scanner.close();
    }

    public static String decimalToBinary(int decimalNumber) {
        if (decimalNumber == 0) {
            return "0";
        }

        StringBuilder binaryBuilder = new StringBuilder();

        while (decimalNumber > 0) {
            int remainder = decimalNumber % 2;
            binaryBuilder.insert(0, remainder); // Insert the remainder at the beginning of the binary string
            decimalNumber /= 2;
        }

        return binaryBuilder.toString();
    }
}
```

In this example, the `decimalToBinary` method takes an integer `decimalNumber` as input and returns its binary representation as a string.

The method uses a `StringBuilder` to build the binary representation by repeatedly dividing the `decimalNumber` by 2 and keeping track of the remainders. The method uses a while loop that continues until the `decimalNumber` becomes 0. In each iteration of the loop:

1. The remainder of the division (`decimalNumber % 2`) is calculated.
2. The remainder is inserted at the beginning of the `binaryBuilder` using `binaryBuilder.insert(0, remainder)`.
3. The `decimalNumber` is updated to `decimalNumber / 2` to continue the division.

Finally, the method returns the binary representation as a string. For example, if you input 14, the program will output "1110" as the binary representation.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to find perfect number or not.

A perfect number is a positive integer that is equal to the sum of its proper divisors (excluding itself). To determine whether a given number is a perfect number or not, you can write a Java program using a loop to find all its divisors and calculate their sum.

Here's a Java program that checks if a number is a perfect number or not:

```java
import java.util.Scanner;

public class PerfectNumber {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a positive integer: ");
        int number = scanner.nextInt();

        if (isPerfectNumber(number)) {
            System.out.println(number + " is a perfect number.");
        } else {
            System.out.println(number + " is not a perfect number.");
        }

        scanner.close();
    }

    public static boolean isPerfectNumber(int number) {
        if (number <= 0) {
            return false;
        }

        int sumOfDivisors = 0;

        // Find divisors and calculate their sum
        for (int i = 1; i <= number / 2; i++) {
            if (number % i == 0) {
                sumOfDivisors += i;
            }
        }

        return sumOfDivisors == number;
    }
}
```

In this example, the `isPerfectNumber` method takes an integer `number` as input and returns `true` if it is a perfect number, and `false` otherwise.

The method first checks if the `number` is positive and greater than 0. If not, it immediately returns `false`.

Then, the method uses a loop to find all the divisors of the number (excluding itself) and calculates their sum in the variable `sumOfDivisors`.

Finally, the method returns `true` if `sumOfDivisors` is equal to the `number`, indicating that the number is a perfect number.

For example, if you input 28, the program will output "28 is a perfect number," as 28 is equal to the sum of its proper divisors (1 + 2 + 4 + 7 + 14 = 28).

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to find sum of each digit in the given number using recursion.

To find the sum of each digit in a given number using recursion in Java, you can define a recursive method that breaks down the number into individual digits and calculates their sum. Here's a Java program to achieve this:

```java
import java.util.Scanner;

public class SumOfDigitsRecursion {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a positive integer: ");
        int number = scanner.nextInt();

        int sum = sumOfDigits(number);

        System.out.println("Sum of digits in " + number + " is: " + sum);

        scanner.close();
    }

    public static int sumOfDigits(int number) {
        // Base case: If the number is less than 10, it is a single-digit number, and the sum is the number itself.
        if (number < 10) {
            return number;
        }

        // Recursive case: Get the last digit of the number and call the method with the rest of the digits.
        int lastDigit = number % 10;
        int remainingDigits = number / 10;
        return lastDigit + sumOfDigits(remainingDigits);
    }
}
```

In this example, the `sumOfDigits` method is a recursive function that takes an integer `number` as input and returns the sum of its individual digits.

The method uses a base case to handle single-digit numbers (numbers less than 10), in which the sum of digits is simply the number itself.

In the recursive case, the method extracts the last digit of the number using `number % 10` and calls the `sumOfDigits` method again with the remaining digits obtained using `number / 10`. The result of the recursive call is then added to the last digit and returned as the final sum.

For example, if you input 12345, the program will output "Sum of digits in 12345 is: 15" (1 + 2 + 3 + 4 + 5 = 15).

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to check the given number is a prime number or not?

To check if a given number is a prime number or not in Java, you can write a program that checks for divisibility of the number by all numbers from 2 up to the square root of the number. If the number is only divisible by 1 and itself, it is a prime number.

Here's a Java program to determine if a given number is a prime number:

```java
import java.util.Scanner;

public class PrimeNumberCheck {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a positive integer: ");
        int number = scanner.nextInt();

        if (isPrime(number)) {
            System.out.println(number + " is a prime number.");
        } else {
            System.out.println(number + " is not a prime number.");
        }

        scanner.close();
    }

    public static boolean isPrime(int number) {
        // Check if the number is less than 2 (0 and 1 are not prime numbers)
        if (number < 2) {
            return false;
        }

        // Check for divisibility of the number by all numbers from 2 to the square root of the number
        for (int i = 2; i <= Math.sqrt(number); i++) {
            if (number % i == 0) {
                return false; // If the number is divisible by any other number, it is not prime
            }
        }

        return true; // If the loop completes without finding any divisors, the number is prime
    }
}
```

In this example, the `isPrime` method takes an integer `number` as input and returns `true` if it is a prime number, and `false` otherwise.

The method first checks if the `number` is less than 2, as 0 and 1 are not prime numbers, and it immediately returns `false` in such cases.

Next, the method uses a for loop to check for divisibility of the number by all numbers from 2 to the square root of the number (`Math.sqrt(number)`). If the number is divisible by any other number, it is not a prime number, and the method returns `false`. If the loop completes without finding any divisors, the number is prime, and the method returns `true`.

For example, if you input 17, the program will output "17 is a prime number," as 17 is only divisible by 1 and itself, making it a prime number.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to check the given number is binary number or not?

To check if a given number is a binary number or not in Java, you can write a program that checks each digit of the number to ensure it contains only '0' and '1' characters.

Here's a Java program to determine if a given number is a binary number:

```java
import java.util.Scanner;

public class BinaryNumberCheck {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        String input = scanner.next();

        if (isBinaryNumber(input)) {
            System.out.println(input + " is a binary number.");
        } else {
            System.out.println(input + " is not a binary number.");
        }

        scanner.close();
    }

    public static boolean isBinaryNumber(String input) {
        // Check if the string contains only '0' and '1' characters
        return input.matches("[01]+");
    }
}
```

In this example, the `isBinaryNumber` method takes a string `input` as input and returns `true` if it is a binary number (contains only '0' and '1' characters), and `false` otherwise.

The method uses a regular expression `[01]+` to check if the string contains only '0' and '1' characters. The `matches` method returns `true` if the string matches the regular expression (i.e., contains only '0' and '1' characters), indicating that the number is binary. If the string contains any other characters, the method returns `false`, indicating that the number is not binary.

For example, if you input "101010", the program will output "101010 is a binary number," as it contains only '0' and '1' characters. If you input "12345", the program will output "12345 is not a binary number," as it contains other characters besides '0' and '1'.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Find prime factors of number in Java

To find the prime factors of a number in Java, you can write a program that iterates through all numbers from 2 up to the square root of the given number. If a number is a factor of the given number and is also a prime number, it is a prime factor.

Here's a Java program to find the prime factors of a given number:

```java
import java.util.Scanner;

public class PrimeFactors {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a positive integer: ");
        int number = scanner.nextInt();

        System.out.println("Prime factors of " + number + " are:");
        findPrimeFactors(number);

        scanner.close();
    }

    public static void findPrimeFactors(int number) {
        if (number <= 1) {
            System.out.println("No prime factors for " + number);
            return;
        }

        // Print all 2's that divide the number
        while (number % 2 == 0) {
            System.out.print("2 ");
            number /= 2;
        }

        // At this point, 'number' is odd
        for (int i = 3; i <= Math.sqrt(number); i += 2) {
            // While i divides 'number', print i and divide 'number'
            while (number % i == 0) {
                System.out.print(i + " ");
                number /= i;
            }
        }

        // If the remaining number is greater than 2, it must be a prime factor
        if (number > 2) {
            System.out.print(number);
        }

        System.out.println();
    }
}
```

In this example, the `findPrimeFactors` method takes an integer `number` as input and prints its prime factors.

The method first checks if the `number` is less than or equal to 1. If so, it prints that there are no prime factors for such numbers and returns.

Next, the method handles all the factors of 2 by dividing the number repeatedly by 2 and printing 2 as a prime factor until the number becomes odd.

Afterwards, it uses a for loop to iterate through odd numbers starting from 3 up to the square root of the remaining number. For each odd number, it checks if it is a factor of the remaining number and if it is a prime number. If it is, it divides the number by the prime factor and prints the prime factor.

Finally, if the remaining number after the loop is greater than 2, it must be a prime factor itself, so it is printed.

For example, if you input 60, the program will output "Prime factors of 60 are: 2 2 3 5".

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write code to avoid deadlock in Java where N threads are accessing N shared resources?

To avoid deadlock in Java where N threads are accessing N shared resources, you can use a technique called "Resource Allocation Graph" and implement a "Safe State" algorithm. The Safe State algorithm checks whether a particular thread should wait for a resource or not to avoid deadlock.

Here's a Java implementation using the Safe State algorithm:

```java
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

public class AvoidDeadlock {

    private static int numResources = 3; // Number of shared resources (N in this example)
    private static Lock[] locks = new Lock[numResources];

    public static void main(String[] args) {
        for (int i = 0; i < numResources; i++) {
            locks[i] = new ReentrantLock();
        }

        int numThreads = numResources; // Number of threads (N in this example)
        Thread[] threads = new Thread[numThreads];

        for (int i = 0; i < numThreads; i++) {
            final int threadId = i;
            threads[i] = new Thread(() -> accessResources(threadId));
            threads[i].start();
        }

        // Wait for all threads to finish
        for (int i = 0; i < numThreads; i++) {
            try {
                threads[i].join();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }

        System.out.println("All threads finished execution.");
    }

    private static void accessResources(int threadId) {
        int resource1 = threadId;
        int resource2 = (threadId + 1) % numResources;

        // Acquire locks in a predefined order to avoid circular wait
        if (resource1 > resource2) {
            int temp = resource1;
            resource1 = resource2;
            resource2 = temp;
        }

        // Try to acquire the locks in the defined order
        locks[resource1].lock();
        locks[resource2].lock();

        // Simulate some work with the resources
        System.out.println("Thread " + threadId + " is accessing resources " + resource1 + " and " + resource2);

        // Release the locks in reverse order
        locks[resource2].unlock();
        locks[resource1].unlock();
    }
}
```

In this example, we have `numResources` shared resources (N in this example). We use an array of `Lock` objects to represent each shared resource. The `accessResources` method represents the logic for a thread to access the shared resources.

To avoid deadlock, we use a predefined order to acquire the locks. In this example, we use the thread ID as the resource ID. The thread with the smaller ID will try to acquire the locks in ascending order, and the thread with the larger ID will try to acquire the locks in descending order. This way, we prevent circular wait, which is one of the conditions for deadlock to occur.

In the `main` method, we create `numThreads` threads (N in this example) and start them. Each thread will execute the `accessResources` method.

By using the Safe State algorithm and carefully managing the order of acquiring and releasing the locks, we can avoid the possibility of a deadlock occurring when N threads access N shared resources.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to sort an array in place using QuickSort algorithm?

To sort an array in place using the QuickSort algorithm in Java, you can implement a recursive QuickSort method that partitions the array and sorts its sub-arrays. The QuickSort algorithm has an average time complexity of O(n log n).

Here's a Java implementation of the QuickSort algorithm:

```java
public class QuickSort {

    public static void main(String[] args) {
        int[] arr = { 10, 7, 8, 9, 1, 5 };
        quickSort(arr, 0, arr.length - 1);

        System.out.println("Sorted array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }

    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pivotIndex = partition(arr, low, high);

            // Recursively sort the sub-arrays before and after the pivot
            quickSort(arr, low, pivotIndex - 1);
            quickSort(arr, pivotIndex + 1, high);
        }
    }

    public static int partition(int[] arr, int low, int high) {
        // Choose the last element as the pivot
        int pivot = arr[high];
        int i = low - 1;

        for (int j = low; j < high; j++) {
            // If the current element is smaller than or equal to the pivot,
            // swap it with the element at index i and move i to the next position.
            if (arr[j] <= pivot) {
                i++;
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }

        // Finally, swap the pivot with the element at index i+1
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        // Return the index of the pivot in the sorted array
        return i + 1;
    }
}
```

In this example, we have a `quickSort` method that takes an array `arr`, a starting index `low`, and an ending index `high`. The method recursively sorts the array by partitioning it and sorting its sub-arrays. The partitioning is done using the `partition` method.

The `partition` method takes the same array, starting index `low`, and ending index `high`. It chooses the last element as the pivot and rearranges the elements such that all elements smaller than or equal to the pivot are on the left side, and all elements greater than the pivot are on the right side. The method returns the index of the pivot in the sorted array.

The `quickSort` method continues recursively sorting the sub-arrays before and after the pivot until the entire array is sorted.

For example, if you input the array `{10, 7, 8, 9, 1, 5}`, the program will output the sorted array: `1 5 7 8 9 10`.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to find intersection of two sorted arrays in Java?

To find the intersection of two sorted arrays in Java, you can use a simple algorithm that iterates through both arrays simultaneously, comparing elements and identifying the common elements.

Here's a Java program to find the intersection of two sorted arrays:

```java
import java.util.ArrayList;
import java.util.List;

public class IntersectionOfSortedArrays {

    public static void main(String[] args) {
        int[] arr1 = {1, 3, 4, 6, 8};
        int[] arr2 = {2, 3, 5, 6, 7, 8};

        List<Integer> intersection = findIntersection(arr1, arr2);

        System.out.println("Intersection of the two arrays:");
        for (int num : intersection) {
            System.out.print(num + " ");
        }
    }

    public static List<Integer> findIntersection(int[] arr1, int[] arr2) {
        List<Integer> intersection = new ArrayList<>();
        int i = 0, j = 0;

        while (i < arr1.length && j < arr2.length) {
            if (arr1[i] == arr2[j]) {
                intersection.add(arr1[i]);
                i++;
                j++;
            } else if (arr1[i] < arr2[j]) {
                i++;
            } else {
                j++;
            }
        }

        return intersection;
    }
}
```

In this example, we have two sorted arrays `arr1` and `arr2`. The `findIntersection` method takes these two arrays as input and returns a list containing their intersection.

The method uses two pointers, `i` and `j`, to iterate through both arrays simultaneously. If the elements at the current positions of both arrays are the same, it means there is an intersection, and the element is added to the `intersection` list. If the element in `arr1` is smaller, we move the pointer `i` to the next position. If the element in `arr2` is smaller, we move the pointer `j` to the next position.

The method continues this process until one of the arrays is fully traversed, and then it returns the `intersection` list.

For example, if you have two arrays `arr1 = {1, 3, 4, 6, 8}` and `arr2 = {2, 3, 5, 6, 7, 8}`, the program will output the intersection: `3 6 8`. These are the common elements present in both arrays.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How find the first repeating element in an array of integers?

To find the first repeating element in an array of integers in Java, you can use a HashSet to keep track of elements seen so far. As you traverse the array, check if the element is already present in the HashSet. If it is, then it is the first repeating element, and you can return it.

Here's a Java program to find the first repeating element in an array:

```java
import java.util.HashSet;

public class FirstRepeatingElement {

    public static void main(String[] args) {
        int[] arr = {4, 2, 6, 8, 3, 2, 7, 4};
        int firstRepeating = findFirstRepeatingElement(arr);

        if (firstRepeating != -1) {
            System.out.println("The first repeating element is: " + firstRepeating);
        } else {
            System.out.println("No repeating elements found in the array.");
        }
    }

    public static int findFirstRepeatingElement(int[] arr) {
        HashSet<Integer> seenElements = new HashSet<>();

        for (int num : arr) {
            if (seenElements.contains(num)) {
                return num; // Found the first repeating element
            }
            seenElements.add(num);
        }

        return -1; // No repeating element found
    }
}
```

In this example, we have an array of integers `arr`. The `findFirstRepeatingElement` method takes this array as input and returns the first repeating element.

The method uses a HashSet called `seenElements` to keep track of the elements seen so far. It traverses the array, and for each element, it checks if it is already present in the HashSet using `contains` method. If the element is already present, it means it is the first repeating element, and the method returns it. If the element is not present, it adds it to the HashSet and continues the iteration.

If no repeating element is found in the array, the method returns -1.

For example, in the input array `{4, 2, 6, 8, 3, 2, 7, 4}`, the first repeating element is `2`, so the program will output "The first repeating element is: 2".

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find first non-repeating element in array of integers?

To find the first non-repeating element in an array of integers in Java, you can use a LinkedHashMap to keep track of the count of each element in the array while preserving the order of insertion. After counting the occurrences of each element, you can iterate through the LinkedHashMap to find the first element with a count of 1.

Here's a Java program to find the first non-repeating element in an array:

```java
import java.util.LinkedHashMap;

public class FirstNonRepeatingElement {

    public static void main(String[] args) {
        int[] arr = {4, 2, 6, 8, 3, 2, 7, 4};
        int firstNonRepeating = findFirstNonRepeatingElement(arr);

        if (firstNonRepeating != -1) {
            System.out.println("The first non-repeating element is: " + firstNonRepeating);
        } else {
            System.out.println("No non-repeating element found in the array.");
        }
    }

    public static int findFirstNonRepeatingElement(int[] arr) {
        LinkedHashMap<Integer, Integer> elementCount = new LinkedHashMap<>();

        // Count the occurrences of each element in the array
        for (int num : arr) {
            elementCount.put(num, elementCount.getOrDefault(num, 0) + 1);
        }

        // Find the first element with a count of 1
        for (int num : arr) {
            if (elementCount.get(num) == 1) {
                return num; // Found the first non-repeating element
            }
        }

        return -1; // No non-repeating element found
    }
}
```

In this example, we have an array of integers `arr`. The `findFirstNonRepeatingElement` method takes this array as input and returns the first non-repeating element.

The method uses a LinkedHashMap called `elementCount` to store the count of occurrences of each element in the array. It traverses the array and counts the occurrences of each element using the `put` method of the LinkedHashMap. Since LinkedHashMap preserves the order of insertion, the elements will be stored in the order they appear in the array.

After counting the occurrences, the method iterates through the array again and checks the count of each element in the LinkedHashMap. If the count of an element is equal to 1, it means it is the first non-repeating element, and the method returns it.

If no non-repeating element is found in the array, the method returns -1.

For example, in the input array `{4, 2, 6, 8, 3, 2, 7, 4}`, the first non-repeating element is `6`, so the program will output "The first non-repeating element is: 6".

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find top two numbers from an integer array?

To find the top two numbers from an integer array in Java, you can use a simple algorithm that keeps track of the two largest numbers while iterating through the array.

Here's a Java program to find the top two numbers from an integer array:

```java
public class TopTwoNumbers {

    public static void main(String[] args) {
        int[] arr = {10, 5, 8, 15, 7, 20, 12};

        int[] topTwo = findTopTwoNumbers(arr);

        System.out.println("Top two numbers:");
        System.out.println("1st: " + topTwo[0]);
        System.out.println("2nd: " + topTwo[1]);
    }

    public static int[] findTopTwoNumbers(int[] arr) {
        if (arr == null || arr.length < 2) {
            throw new IllegalArgumentException("Array should have at least two elements.");
        }

        int firstMax = Integer.MIN_VALUE;
        int secondMax = Integer.MIN_VALUE;

        for (int num : arr) {
            if (num > firstMax) {
                secondMax = firstMax;
                firstMax = num;
            } else if (num > secondMax && num != firstMax) {
                secondMax = num;
            }
        }

        return new int[]{firstMax, secondMax};
    }
}
```

In this example, we have an integer array `arr`. The `findTopTwoNumbers` method takes this array as input and returns the top two numbers as an array.

The method initializes two variables, `firstMax` and `secondMax`, to `Integer.MIN_VALUE`, which represents the smallest possible integer value. It then iterates through the array, comparing each element with `firstMax` and `secondMax`. If the current element is greater than `firstMax`, it updates `firstMax` and moves the old value of `firstMax` to `secondMax`. If the current element is greater than `secondMax` and not equal to `firstMax`, it updates `secondMax`.

After the iteration, the method returns an array containing `firstMax` and `secondMax`, which are the top two numbers from the original array.

For example, in the input array `{10, 5, 8, 15, 7, 20, 12}`, the top two numbers are `20` and `15`, so the program will output:

```yaml
Top two numbers:
1st: 20
2nd: 15
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find the smallest positive integer value that cannot be represented as sum of any subset of a given array?

To find the smallest positive integer value that cannot be represented as the sum of any subset of a given array in Java, you can use a greedy approach. The idea is to sort the array in ascending order and then iterate through the sorted array to find the smallest positive integer that cannot be formed as a sum of any previous elements.

Here's a Java program to find the smallest positive integer value:

```java
import java.util.Arrays;

public class SmallestPositiveInteger {

    public static void main(String[] args) {
        int[] arr = {1, 3, 6, 10, 11, 15};
        int smallestPositive = findSmallestPositiveInteger(arr);

        System.out.println("The smallest positive integer that cannot be represented as a sum of any subset: " + smallestPositive);
    }

    public static int findSmallestPositiveInteger(int[] arr) {
        Arrays.sort(arr);

        int smallestPositive = 1;

        for (int num : arr) {
            if (num <= smallestPositive) {
                smallestPositive += num;
            } else {
                break;
            }
        }

        return smallestPositive;
    }
}
```

In this example, we have an integer array `arr`. The `findSmallestPositiveInteger` method takes this array as input and returns the smallest positive integer that cannot be represented as a sum of any subset.

The method first sorts the array in ascending order using `Arrays.sort(arr)`.

It then initializes `smallestPositive` to 1 and iterates through the sorted array. For each element, if the element is less than or equal to `smallestPositive`, it means we can form `smallestPositive + num` using the current subset, so we update `smallestPositive` to `smallestPositive + num`. If the element is greater than `smallestPositive`, it means we cannot form the `smallestPositive` using the current subset, and we break out of the loop.

After the loop, the `smallestPositive` will be the smallest positive integer that cannot be formed as a sum of any subset of the given array, and the method returns it.

For example, in the input array `{1, 3, 6, 10, 11, 15}`, the smallest positive integer that cannot be represented as a sum of any subset is `2`, so the program will output:

```python
The smallest positive integer that cannot be represented as a sum of any subset: 2
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to merge sorted array?

To merge two sorted arrays into a single sorted array in Java, you can use a simple merging algorithm similar to the merge step of the MergeSort algorithm. Since both input arrays are already sorted, you can efficiently merge them into a new sorted array by comparing elements from both arrays and inserting them in the correct order.

Here's a Java program to merge two sorted arrays:

```java
public class MergeSortedArrays {

    public static void main(String[] args) {
        int[] arr1 = {1, 3, 5, 7};
        int[] arr2 = {2, 4, 6, 8, 10};

        int[] mergedArray = mergeArrays(arr1, arr2);

        System.out.println("Merged sorted array:");
        for (int num : mergedArray) {
            System.out.print(num + " ");
        }
    }

    public static int[] mergeArrays(int[] arr1, int[] arr2) {
        int length1 = arr1.length;
        int length2 = arr2.length;
        int[] mergedArray = new int[length1 + length2];

        int i = 0, j = 0, k = 0;

        // Compare elements from both arrays and insert them in the merged array
        while (i < length1 && j < length2) {
            if (arr1[i] <= arr2[j]) {
                mergedArray[k++] = arr1[i++];
            } else {
                mergedArray[k++] = arr2[j++];
            }
        }

        // Insert any remaining elements from the first array
        while (i < length1) {
            mergedArray[k++] = arr1[i++];
        }

        // Insert any remaining elements from the second array
        while (j < length2) {
            mergedArray[k++] = arr2[j++];
        }

        return mergedArray;
    }
}
```

In this example, we have two sorted integer arrays `arr1` and `arr2`. The `mergeArrays` method takes these two arrays as input and returns a new merged array containing all elements from both arrays in sorted order.

The method uses three pointers, `i`, `j`, and `k`, to keep track of the current position in each array and the merged array, respectively. It compares elements from both arrays, starting from the first element, and inserts the smaller element into the merged array. It then moves the corresponding pointer to the next element in that array. This process continues until all elements from both arrays are merged into the new sorted array.

Finally, any remaining elements from either array are inserted into the merged array, and the merged array is returned.

For example, if you have two sorted arrays `arr1 = {1, 3, 5, 7}` and `arr2 = {2, 4, 6, 8, 10}`, the merged sorted array will be `{1, 2, 3, 4, 5, 6, 7, 8, 10}`. The program will output:

```c
Merged sorted array:
1 2 3 4 5 6 7 8 10
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find sub array with maximum sum in an array of positive and negative number?

To find the subarray with the maximum sum in an array containing both positive and negative numbers, you can use the Kadane's algorithm. This algorithm efficiently finds the maximum sum subarray by keeping track of the maximum sum ending at each position in the array.

Here's a Java program to find the subarray with the maximum sum:

```java
public class MaximumSubarraySum {

    public static void main(String[] args) {
        int[] arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        int[] maxSubarray = findMaximumSubarraySum(arr);

        System.out.println("Maximum subarray sum: " + maxSubarray[0]);
        System.out.println("Subarray elements:");

        for (int i = maxSubarray[1]; i <= maxSubarray[2]; i++) {
            System.out.print(arr[i] + " ");
        }
    }

    public static int[] findMaximumSubarraySum(int[] arr) {
        int n = arr.length;
        int maxEndingHere = arr[0];
        int maxSoFar = arr[0];
        int start = 0;
        int end = 0;
        int tempStart = 0;

        for (int i = 1; i < n; i++) {
            // Calculate the maximum sum ending at the current position
            maxEndingHere = Math.max(arr[i], maxEndingHere + arr[i]);

            // If the current element is greater than the maximum sum so far,
            // update the start and end indices of the subarray
            if (arr[i] > maxEndingHere) {
                tempStart = i;
            }

            if (maxEndingHere > maxSoFar) {
                maxSoFar = maxEndingHere;
                start = tempStart;
                end = i;
            }
        }

        return new int[]{maxSoFar, start, end};
    }
}
```

In this example, we have an integer array `arr` containing both positive and negative numbers. The `findMaximumSubarraySum` method takes this array as input and returns an array containing the maximum subarray sum, as well as the start and end indices of the subarray.

The method uses two variables, `maxEndingHere` and `maxSoFar`, to keep track of the maximum sum ending at the current position and the overall maximum sum found so far, respectively. It also uses `start` and `end` variables to store the indices of the maximum subarray.

The algorithm iterates through the array starting from the second element. For each element, it calculates the maximum sum ending at that position (`maxEndingHere`) by taking the maximum of the current element and the sum of the current element and the maximum sum ending at the previous position.

If the current element is greater than the maximum sum ending at that position, it means starting a new subarray from that position will give a larger sum. In that case, it updates the `tempStart` variable to store the index of the potential new start of the subarray.

If the `maxEndingHere` is greater than `maxSoFar`, it means a new maximum subarray is found. In that case, it updates `maxSoFar`, `start`, and `end` to store the new maximum sum, as well as the start and end indices of the subarray.

After the iteration, the `maxSoFar`, `start`, and `end` values represent the maximum subarray sum and its corresponding subarray in the given array, and the method returns an array containing these values.

For example, in the input array `{-2, 1, -3, 4, -1, 2, 1, -5, 4}`, the maximum subarray sum is `6`, and the subarray with the maximum sum is `{4, -1, 2, 1}`. The program will output:

```yaml
Maximum subarray sum: 6
Subarray elements:
4 -1 2 1
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find sub array with largest product in array of both positive and negative number?

To find the subarray with the largest product in an array containing both positive and negative numbers, you can use a dynamic programming approach. Since the presence of negative numbers complicates the product calculation, you need to keep track of both the maximum and minimum products ending at each position in the array.

Here's a Java program to find the subarray with the largest product:

```java
public class MaximumSubarrayProduct {

    public static void main(String[] args) {
        int[] arr = {2, 3, -2, 4, -1};
        int maxProduct = findMaximumSubarrayProduct(arr);

        System.out.println("Maximum subarray product: " + maxProduct);
    }

    public static int findMaximumSubarrayProduct(int[] arr) {
        int n = arr.length;
        int maxEndingHere = arr[0];
        int minEndingHere = arr[0];
        int maxSoFar = arr[0];

        for (int i = 1; i < n; i++) {
            // Save the maxEndingHere value as it will be used later to calculate the minEndingHere
            int temp = maxEndingHere;

            // Calculate the maximum and minimum products ending at the current position
            maxEndingHere = Math.max(arr[i], Math.max(arr[i] * maxEndingHere, arr[i] * minEndingHere));
            minEndingHere = Math.min(arr[i], Math.min(arr[i] * temp, arr[i] * minEndingHere));

            // Update the overall maximum product found so far
            maxSoFar = Math.max(maxSoFar, maxEndingHere);
        }

        return maxSoFar;
    }
}
```

In this example, we have an integer array `arr` containing both positive and negative numbers. The `findMaximumSubarrayProduct` method takes this array as input and returns the maximum subarray product.

The method uses three variables, `maxEndingHere`, `minEndingHere`, and `maxSoFar`, to keep track of the maximum product ending at the current position, the minimum product ending at the current position, and the overall maximum product found so far, respectively.

The algorithm iterates through the array starting from the second element. For each element, it calculates the maximum and minimum products ending at that position (`maxEndingHere` and `minEndingHere`) using dynamic programming. It compares the current element, the product of the current element and the maximum product ending at the previous position, and the product of the current element and the minimum product ending at the previous position, and updates `maxEndingHere` and `minEndingHere` accordingly.

The algorithm also updates `maxSoFar` to store the maximum of all `maxEndingHere` values, which represents the maximum product found so far.

After the iteration, the `maxSoFar` value represents the maximum subarray product in the given array, and the method returns it.

For example, in the input array `{2, 3, -2, 4, -1}`, the maximum subarray product is `48`, which is obtained from the subarray `{2, 3, -2, 4}`. The program will output:

```yaml
Maximum subarray product: 48
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to find length of longest consecutive sequence in array of integers?

To find the length of the longest consecutive sequence in an array of integers, you can use a HashSet to efficiently check for the presence of consecutive numbers while traversing the array.

Here's a Java program to find the length of the longest consecutive sequence:

```java
import java.util.HashSet;

public class LongestConsecutiveSequence {

    public static void main(String[] args) {
        int[] arr = {100, 4, 200, 1, 3, 2, 5};

        int longestConsecutiveLength = findLongestConsecutiveSequence(arr);

        System.out.println("Length of the longest consecutive sequence: " + longestConsecutiveLength);
    }

    public static int findLongestConsecutiveSequence(int[] arr) {
        HashSet<Integer> numSet = new HashSet<>();
        int longestConsecutiveLength = 0;

        // Add all elements to the HashSet
        for (int num : arr) {
            numSet.add(num);
        }

        // Check for consecutive sequences starting from each element
        for (int num : arr) {
            // Check for the start of the consecutive sequence (the element before 'num' is not present in the set)
            if (!numSet.contains(num - 1)) {
                int currentNum = num;
                int currentLength = 1;

                // Find the length of the consecutive sequence
                while (numSet.contains(currentNum + 1)) {
                    currentNum++;
                    currentLength++;
                }

                longestConsecutiveLength = Math.max(longestConsecutiveLength, currentLength);
            }
        }

        return longestConsecutiveLength;
    }
}
```

In this example, we have an integer array `arr`. The `findLongestConsecutiveSequence` method takes this array as input and returns the length of the longest consecutive sequence.

The method uses a HashSet called `numSet` to store all elements from the array, which allows for efficient lookup.

It then iterates through the array and for each element `num`, it checks if `num - 1` is not present in the HashSet. If `num - 1` is not in the set, it means `num` is the start of a consecutive sequence. The method then searches for the length of the consecutive sequence by incrementing `num` while `num + 1` is present in the HashSet.

The algorithm keeps track of the longest consecutive sequence length found so far and updates it whenever a longer consecutive sequence is encountered.

After the iteration, the `longestConsecutiveLength` value represents the length of the longest consecutive sequence in the given array, and the method returns it.

For example, in the input array `{100, 4, 200, 1, 3, 2, 5}`, the longest consecutive sequence is `{1, 2, 3, 4, 5}`, and its length is `5`. The program will output:

```mathematica
Length of the longest consecutive sequence: 5
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find minimum value in a rotated sorted array?

To find the minimum value in a rotated sorted array, you can use a modified binary search algorithm. Since the array is sorted but rotated, the minimum value will be the first element that is smaller than its previous element. This is true even if the array is rotated multiple times.

Here's a Java program to find the minimum value in a rotated sorted array:

```java
public class MinimumInRotatedSortedArray {

    public static void main(String[] args) {
        int[] arr = {4, 5, 6, 7, 0, 1, 2};
        int minValue = findMinimumInRotatedSortedArray(arr);

        System.out.println("Minimum value in the rotated sorted array: " + minValue);
    }

    public static int findMinimumInRotatedSortedArray(int[] arr) {
        int left = 0;
        int right = arr.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] > arr[right]) {
                // The minimum value is in the right half
                left = mid + 1;
            } else {
                // The minimum value is in the left half or at the current position
                right = mid;
            }
        }

        return arr[left];
    }
}
```

In this example, we have an integer array `arr`, which is a rotated sorted array. The `findMinimumInRotatedSortedArray` method takes this array as input and returns the minimum value.

The method uses a modified binary search to find the minimum value. It initializes two pointers, `left` and `right`, to the start and end indices of the array, respectively.

The algorithm repeatedly checks the middle element of the current subarray (calculated as `mid = left + (right - left) / 2`) and compares it with the element at the `right` pointer. If the middle element is greater than the element at the `right` pointer, it means the minimum value is in the right half of the array (including the middle element), so the `left` pointer is moved to `mid + 1`. Otherwise, the minimum value is in the left half of the array or could be the current middle element, so the `right` pointer is moved to `mid`.

The binary search continues until the `left` and `right` pointers converge, and the loop terminates when `left == right`.

At this point, the `left` pointer is pointing to the minimum value in the rotated sorted array, and the method returns the value at `arr[left]`.

For example, in the input array `{4, 5, 6, 7, 0, 1, 2}`, the minimum value is `0`, and the program will output:

```c
Minimum value in the rotated sorted array: 0
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Given an array of of size n and a number k, find all elements that appear more than n/k times?

To find all elements in an array that appear more than n/k times, where n is the size of the array and k is a positive integer, you can use a HashMap to keep track of the frequency of each element in the array. Then, you can iterate through the HashMap and collect all elements that have a frequency greater than n/k.

Here's a Java program to find such elements:

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class ElementsMoreThanNKTimes {

    public static void main(String[] args) {
        int[] arr = {3, 1, 2, 2, 1, 2, 3, 3};
        int k = 4;

        List<Integer> elementsMoreThanNKTimes = findElementsMoreThanNKTimes(arr, k);

        System.out.println("Elements appearing more than n/k times:");
        for (int element : elementsMoreThanNKTimes) {
            System.out.print(element + " ");
        }
    }

    public static List<Integer> findElementsMoreThanNKTimes(int[] arr, int k) {
        List<Integer> result = new ArrayList<>();
        int n = arr.length;
        int targetFrequency = n / k;

        // Use a HashMap to count the frequency of each element in the array
        Map<Integer, Integer> frequencyMap = new HashMap<>();
        for (int num : arr) {
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
        }

        // Collect elements that have a frequency greater than n/k
        for (Map.Entry<Integer, Integer> entry : frequencyMap.entrySet()) {
            if (entry.getValue() > targetFrequency) {
                result.add(entry.getKey());
            }
        }

        return result;
    }
}
```

In this example, we have an integer array `arr` and a positive integer `k`. The `findElementsMoreThanNKTimes` method takes these two inputs and returns a list containing all elements that appear more than n/k times in the array.

The method first calculates the `targetFrequency` as n/k, which is the minimum frequency that an element should have to be considered as appearing more than n/k times.

Then, it uses a HashMap called `frequencyMap` to count the frequency of each element in the array. The key of the HashMap represents the element, and the value represents its frequency.

Next, the method iterates through the HashMap and collects all elements that have a frequency greater than `targetFrequency`. These elements are added to the `result` list.

Finally, the method returns the `result` list containing the elements that appear more than n/k times in the array.

For example, in the input array `{3, 1, 2, 2, 1, 2, 3, 3}` and `k = 4`, the elements that appear more than n/k times are `2` and `3`, so the program will output:

```bash
Elements appearing more than n/k times:
2 3
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Returns the largest sum of contiguous integers in the array

To find the largest sum of contiguous integers (also known as the maximum subarray sum) in an array, you can use Kadane's algorithm. This algorithm efficiently computes the maximum sum of a subarray by keeping track of the maximum sum ending at each position in the array.

Here's a Java program to find the largest sum of contiguous integers:

```java
public class LargestContiguousSum {

    public static void main(String[] args) {
        int[] arr = {1, -3, 4, -2, -1, 6};

        int largestSum = findLargestContiguousSum(arr);

        System.out.println("Largest sum of contiguous integers: " + largestSum);
    }

    public static int findLargestContiguousSum(int[] arr) {
        int maxEndingHere = arr[0];
        int maxSoFar = arr[0];

        for (int i = 1; i < arr.length; i++) {
            // Calculate the maximum sum ending at the current position
            maxEndingHere = Math.max(arr[i], maxEndingHere + arr[i]);

            // Update the overall maximum sum found so far
            maxSoFar = Math.max(maxSoFar, maxEndingHere);
        }

        return maxSoFar;
    }
}
```

In this example, we have an integer array `arr`. The `findLargestContiguousSum` method takes this array as input and returns the largest sum of contiguous integers.

The method uses two variables, `maxEndingHere` and `maxSoFar`, to keep track of the maximum sum ending at the current position and the overall maximum sum found so far, respectively.

The algorithm iterates through the array starting from the second element. For each element, it calculates the maximum sum ending at that position (`maxEndingHere`) by taking the maximum of the current element and the sum of the current element and the maximum sum ending at the previous position.

The algorithm also updates `maxSoFar` to store the maximum of all `maxEndingHere` values, which represents the largest sum of contiguous integers found so far.

After the iteration, the `maxSoFar` value represents the largest sum of contiguous integers in the given array, and the method returns it.

For example, in the input array `{1, -3, 4, -2, -1, 6}`, the largest sum of contiguous integers is `7`, which is obtained from the subarray `{4, -2, -1, 6}`. The program will output:

```bash
Largest sum of contiguous integers: 7
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Return the sum two largest integers in an array

To return the sum of the two largest integers in an array, you can sort the array in descending order and then take the sum of the first two elements. Sorting the array allows you to quickly identify the two largest integers at the beginning of the sorted array.

Here's a Java program to return the sum of the two largest integers:

```java
import java.util.Arrays;

public class SumOfTwoLargestIntegers {

    public static void main(String[] args) {
        int[] arr = {5, 10, 2, 8, 20};

        int sumOfTwoLargest = findSumOfTwoLargestIntegers(arr);

        System.out.println("Sum of the two largest integers: " + sumOfTwoLargest);
    }

    public static int findSumOfTwoLargestIntegers(int[] arr) {
        if (arr == null || arr.length < 2) {
            throw new IllegalArgumentException("Array should have at least two elements.");
        }

        // Sort the array in descending order
        Arrays.sort(arr);

        // Take the sum of the first two elements (the two largest integers)
        return arr[arr.length - 1] + arr[arr.length - 2];
    }
}
```

In this example, we have an integer array `arr`. The `findSumOfTwoLargestIntegers` method takes this array as input and returns the sum of the two largest integers.

The method first checks if the array contains at least two elements. If not, it throws an `IllegalArgumentException`.

Then, it sorts the array in descending order using `Arrays.sort(arr)`.

Finally, it returns the sum of the first two elements of the sorted array, which are the two largest integers.

For example, in the input array `{5, 10, 2, 8, 20}`, the two largest integers are `20` and `10`, and their sum is `30`. The program will output:
```mathematica
Sum of the two largest integers: 30
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to search an array to check if an element exists there?

To search an array to check if an element exists, you can use a simple loop to iterate through the elements of the array and compare each element with the target element you want to find. If the target element is found, you can return `true`; otherwise, if the loop completes without finding the element, you can return `false`.

Here's a Java method to search an array for a target element:

```java
public class ArraySearch {

    public static void main(String[] args) {
        int[] arr = {5, 10, 15, 20, 25};
        int targetElement = 15;

        boolean elementExists = searchElement(arr, targetElement);

        if (elementExists) {
            System.out.println("The element exists in the array.");
        } else {
            System.out.println("The element does not exist in the array.");
        }
    }

    public static boolean searchElement(int[] arr, int target) {
        for (int element : arr) {
            if (element == target) {
                return true;
            }
        }
        return false;
    }
}
```

In this example, we have an integer array `arr` and a target integer `targetElement`. The `searchElement` method takes these two inputs and returns `true` if the `targetElement` is found in the array, or `false` otherwise.

The method uses an enhanced for loop (`for-each` loop) to iterate through each element of the array. For each element, it checks if it matches the `targetElement`. If a match is found, the method returns `true`. If no match is found after iterating through the entire array, the method returns `false`.

For example, in the input array `{5, 10, 15, 20, 25}`, if the target element is `15`, the method will return `true`, indicating that the element exists in the array. The program will output:
```arduino
The element exists in the array.
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to copy array in Java?

In Java, you can copy an array using various methods, depending on your requirements and the data type of the array. Here are three common ways to copy an array in Java:

1. Using a loop:
You can use a simple for loop to copy each element from the source array to the destination array.

```java
public class ArrayCopyExample {

    public static void main(String[] args) {
        int[] sourceArray = {1, 2, 3, 4, 5};
        int[] destinationArray = new int[sourceArray.length];

        // Copy the elements from sourceArray to destinationArray
        for (int i = 0; i < sourceArray.length; i++) {
            destinationArray[i] = sourceArray[i];
        }

        // Print the copied array
        for (int num : destinationArray) {
            System.out.print(num + " ");
        }
    }
}
```

2. Using `System.arraycopy` method:
Java provides a built-in `System.arraycopy` method that can efficiently copy elements from one array to another.

```java
public class ArrayCopyExample {

    public static void main(String[] args) {
        int[] sourceArray = {1, 2, 3, 4, 5};
        int[] destinationArray = new int[sourceArray.length];

        // Copy the elements from sourceArray to destinationArray
        System.arraycopy(sourceArray, 0, destinationArray, 0, sourceArray.length);

        // Print the copied array
        for (int num : destinationArray) {
            System.out.print(num + " ");
        }
    }
}
```

3. Using `Arrays.copyOf` method:
Java's `Arrays` class provides a `copyOf` method that can be used to copy an array easily.

```java
import java.util.Arrays;

public class ArrayCopyExample {

    public static void main(String[] args) {
        int[] sourceArray = {1, 2, 3, 4, 5};

        // Copy the elements from sourceArray to destinationArray
        int[] destinationArray = Arrays.copyOf(sourceArray, sourceArray.length);

        // Print the copied array
        for (int num : destinationArray) {
            System.out.print(num + " ");
        }
    }
}
```

All three methods will produce the same output, which is the copy of the original array:

```
1 2 3 4 5
```

Choose the method that best suits your needs and coding style. Note that these methods perform a shallow copy, meaning they copy the references to the elements in the array. If the array contains objects, only the references to those objects will be copied, not the objects themselves. If you need a deep copy (i.e., copying the objects as well), you'll need to perform a custom deep copy depending on the nature of the objects in the array.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a function to find out longest palindrome in a given string?

To find the longest palindrome in a given string, you can use a simple algorithm that checks all possible substrings to identify the longest palindrome. There are more efficient algorithms available, but this basic approach is easier to understand and implement.

Here's a Java function to find the longest palindrome in a given string:

```java
public class LongestPalindrome {

    public static void main(String[] args) {
        String input = "babad";
        String longestPalindrome = findLongestPalindrome(input);

        System.out.println("Longest palindrome: " + longestPalindrome);
    }

    public static String findLongestPalindrome(String s) {
        if (s == null || s.isEmpty()) {
            return "";
        }

        String longest = "";
        for (int i = 0; i < s.length(); i++) {
            String oddPalindrome = expandAroundCenter(s, i, i);
            String evenPalindrome = expandAroundCenter(s, i, i + 1);

            String currentLongest = oddPalindrome.length() > evenPalindrome.length() ? oddPalindrome : evenPalindrome;

            if (currentLongest.length() > longest.length()) {
                longest = currentLongest;
            }
        }

        return longest;
    }

    private static String expandAroundCenter(String s, int left, int right) {
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            left--;
            right++;
        }
        return s.substring(left + 1, right);
    }
}
```

In this example, the `findLongestPalindrome` method takes a string `s` as input and returns the longest palindrome found in the string. The `expandAroundCenter` method is a helper function that expands around a center to check if a palindrome exists.

The `findLongestPalindrome` function iterates through each character of the input string and treats it as the center of a possible palindrome. It then calls the `expandAroundCenter` function twice—one for odd-length palindromes and the other for even-length palindromes—to check if a palindrome exists with that center. The `expandAroundCenter` function expands outwards from the center to find the longest palindrome centered at the given index.

The function keeps track of the longest palindrome found so far and returns it as the result.

For example, in the input string "babad," the longest palindromes are "bab" and "aba." The function will return one of these, and the program will output:
```mathematica
Longest palindrome: bab
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Can you make array volatile in Java?

In Java, you cannot make an array volatile directly. The `volatile` keyword can only be applied to individual variables, not to arrays as a whole. When you mark a variable as `volatile`, it guarantees that any read or write to that variable will be directly performed on the main memory, ensuring visibility of changes across threads.

However, there is an alternative approach if you want to achieve volatile-like behavior for an array. Instead of making the array itself volatile, you can make the elements of the array volatile, assuming the elements are of reference type (e.g., objects). When the elements are volatile, the changes made to the elements in one thread will be visible to other threads.

Here's an example demonstrating how you can use volatile elements in an array:

```java
public class VolatileArrayExample {

    private volatile Integer[] sharedArray = new Integer[5];

    public static void main(String[] args) {
        VolatileArrayExample example = new VolatileArrayExample();

        Thread writerThread = new Thread(() -> {
            for (int i = 0; i < example.sharedArray.length; i++) {
                example.sharedArray[i] = i + 1;
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        });

        Thread readerThread = new Thread(() -> {
            while (true) {
                for (int i = 0; i < example.sharedArray.length; i++) {
                    System.out.print(example.sharedArray[i] + " ");
                }
                System.out.println();
                try {
                    Thread.sleep(500);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        });

        writerThread.start();
        readerThread.start();
    }
}
```

In this example, we have a `VolatileArrayExample` class with a `sharedArray` field, which is an array of `Integer` objects. The `sharedArray` is declared as `volatile`.

We have two threads: a writer thread that writes values into the `sharedArray` and a reader thread that reads and prints the values of the `sharedArray` repeatedly.

By making the elements of the array (`Integer` objects) volatile, we ensure that the changes made by the writer thread are immediately visible to the reader thread. This guarantees the visibility of changes across threads without directly making the array volatile.

Keep in mind that using volatile elements in an array works well when the array elements are of reference type. If the array contains primitive data types, you may need to use other synchronization mechanisms, like `Atomic` classes or explicit locking, to achieve thread safety and visibility of changes across threads.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find top two numbers from an integer array in Java?

To find the top two numbers from an integer array in Java, you can use a simple approach that iterates through the array to keep track of the largest and second-largest elements. This can be achieved by maintaining two variables to store the maximum and second-maximum values found so far while traversing the array.

Here's a Java program to find the top two numbers from an integer array:

```java
public class TopTwoNumbers {

    public static void main(String[] args) {
        int[] arr = {5, 10, 15, 7, 3, 20};

        int[] topTwo = findTopTwoNumbers(arr);

        System.out.println("Top two numbers: " + topTwo[0] + " and " + topTwo[1]);
    }

    public static int[] findTopTwoNumbers(int[] arr) {
        int max1 = Integer.MIN_VALUE;
        int max2 = Integer.MIN_VALUE;

        for (int num : arr) {
            if (num > max1) {
                // Current number is greater than the maximum found so far.
                // Shift the current maximum to second maximum, and update the maximum.
                max2 = max1;
                max1 = num;
            } else if (num > max2 && num != max1) {
                // Current number is greater than the second maximum found so far.
                max2 = num;
            }
        }

        return new int[]{max1, max2};
    }
}
```

In this example, we have an integer array `arr`. The `findTopTwoNumbers` method takes this array as input and returns an integer array containing the top two numbers.

The method initializes two variables, `max1` and `max2`, to `Integer.MIN_VALUE`. These variables are used to keep track of the two largest numbers found in the array.

The algorithm iterates through the array and updates `max1` and `max2` based on the comparison with the current element (`num`). If the current element is greater than `max1`, it becomes the new maximum, and the previous maximum is shifted to `max2`. If the current element is greater than `max2` but not equal to `max1`, it becomes the new second maximum.

After traversing the entire array, the method returns an array containing the values of `max1` and `max2`, which represent the top two numbers in the original array.

For example, in the input array `{5, 10, 15, 7, 3, 20}`, the top two numbers are `20` and `15`. The program will output:
```css
Top two numbers: 20 and 15
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Can you pass the negative number as an array size?

No, you cannot pass a negative number as an array size in Java. The size of an array must be a non-negative integer, as specified in the Java Language Specification.

According to the Java Language Specification (JLS) Section 10.4, Array Creation, the size of an array must be a `NonWildTypeArgument` that is either a `TypeArgument` or a `Wildcard`. And, as per JLS Section 4.5.1, a `TypeArgument` cannot be a negative number. It can be a type, a reference type, or a wildcard.

Attempting to create an array with a negative size will result in a `NegativeArraySizeException` being thrown at runtime. For example:

```java
public class NegativeArraySizeExample {

    public static void main(String[] args) {
        int[] arr;
        int negativeSize = -5;

        try {
            arr = new int[negativeSize]; // This will throw NegativeArraySizeException
        } catch (NegativeArraySizeException e) {
            System.out.println("Exception: NegativeArraySizeException - Array size cannot be negative.");
        }
    }
}
```

In this example, an attempt is made to create an array with a negative size (`negativeSize = -5`). When this code is executed, it will throw a `NegativeArraySizeException`, indicating that the array size cannot be negative.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. What is an anonymous array? Give example?

In Java, an anonymous array is an array that is created without explicitly declaring a variable name for it. It is a one-time, unnamed array used for a specific purpose without the need for a reference variable. Anonymous arrays are typically used for short-lived tasks and are not assigned to any variable.

Anonymous arrays are created directly at the point of use and are mostly used for passing arguments to methods or for instantiating arrays without the need for storing them in variables.

Here's an example of using an anonymous array to pass arguments to a method:

```java
public class AnonymousArrayExample {

    public static void main(String[] args) {
        printArray(new int[]{1, 2, 3, 4, 5}); // Passing an anonymous array to the method
    }

    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

In this example, the `printArray` method takes an integer array as its parameter and prints its elements. In the `main` method, we pass an anonymous array with elements `{1, 2, 3, 4, 5}` directly as an argument to the `printArray` method.

The anonymous array is created on the fly without assigning it to a variable name. It is used for a specific purpose (passing data to the `printArray` method), and there is no need to keep a reference to it after that.

Anonymous arrays can also be used for array instantiation directly without assigning them to a variable:

```java
public class AnonymousArrayExample {

    public static void main(String[] args) {
        // Creating an anonymous array for initialization
        int[] numbers = new int[]{10, 20, 30, 40, 50};

        // Using anonymous array directly as a parameter
        printArray(new int[]{1, 2, 3, 4, 5});
    }

    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

Anonymous arrays are particularly useful when you need a short-lived array for immediate use without creating an explicit reference variable. They are commonly used in scenarios where a temporary array is needed for quick data manipulation or for passing data to a method without storing the array in a variable.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. What is the difference between int[] a and int a[] ?

In Java, `int[] a` and `int a[]` both declare an array of integers, but they represent two different syntax styles for declaring arrays. However, both styles are equivalent in terms of creating an array of integers.

1. `int[] a` (Preferred Syntax):
   - This style is known as the "preferred" or "standard" syntax for declaring arrays in Java.
   - It explicitly declares `a` as an array of integers.
   - It is more consistent with how other data types are declared in Java, such as `String[] names`, `double[] values`, etc.
   - This syntax style is widely used and recommended by most Java developers.

Example:
```java
int[] numbers = new int[5]; // Declaring an array of integers using preferred syntax
```

2. `int a[]` (C-like Syntax):
   - This style is known as the "C-like" syntax for declaring arrays in Java.
   - It declares `a` as an integer array, but the brackets are placed after the variable name.
   - This syntax resembles the way arrays are declared in the C/C++ programming languages.
   - While this syntax is valid in Java, it is less commonly used and not preferred by most Java developers.

Example:
```java
int values[] = new int[10]; // Declaring an array of integers using C-like syntax
```

Both syntax styles are equivalent in functionality, and you can use either one to declare arrays in Java. However, the `int[] a` style is more widely adopted and considered more readable and consistent with the rest of the Java language, so it is generally recommended to use the preferred syntax for declaring arrays.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. What are jagged arrays in Java? Give example?

In Java, a jagged array is an array of arrays, where each sub-array can have a different length. In other words, a jagged array is an array of arrays that can have varying numbers of elements in each sub-array.

Unlike a regular two-dimensional array (or rectangular array), where all rows have the same length, a jagged array allows for flexibility in defining the size of each row independently. This can be useful in situations where you have irregular data structures or when you need to represent data of varying lengths.

Here's an example of a jagged array in Java:

```java
public class JaggedArrayExample {

    public static void main(String[] args) {
        int[][] jaggedArray = new int[3][]; // Creating a 2D jagged array with 3 rows

        // Initializing each row with a different number of elements
        jaggedArray[0] = new int[]{1, 2, 3};
        jaggedArray[1] = new int[]{4, 5};
        jaggedArray[2] = new int[]{6, 7, 8, 9};

        // Accessing and printing elements of the jagged array
        for (int i = 0; i < jaggedArray.length; i++) {
            for (int j = 0; j < jaggedArray[i].length; j++) {
                System.out.print(jaggedArray[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

In this example, we create a jagged array `jaggedArray` of size 3 (3 rows). Each row of the jagged array is initialized with a different number of elements. The first row has three elements, the second row has two elements, and the third row has four elements.

The output of the program will be:

```
1 2 3 
4 5 
6 7 8 9 
```

As you can see, each row of the jagged array can have a different length, making it a jagged structure.

Jagged arrays can be useful when dealing with non-rectangular data or when you want to save memory by using varying array sizes. However, keep in mind that accessing elements in a jagged array requires extra care to avoid `NullPointerException` when a row has not been initialized or contains `null`.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. While creating the multidimensional arrays, can you specify an array dimension after an empty dimension?

No, in Java, you cannot specify an array dimension after an empty dimension while creating multidimensional arrays. Java requires that all array dimensions are specified at the time of array creation.

In Java, multidimensional arrays are created using nested square brackets `[]` to represent each dimension. The syntax for creating a multidimensional array specifies the size of each dimension in order, from left to right.

For example, to create a 2D array in Java, you would specify the number of rows and columns in the array:

```java
int[][] twoDArray = new int[3][4]; // 3 rows and 4 columns
```

To create a 3D array, you would specify the number of layers, rows, and columns:

```java
int[][][] threeDArray = new int[2][3][4]; // 2 layers, each with 3 rows and 4 columns
```

You cannot have an empty dimension and specify its size later. The size of all dimensions must be provided at the time of array creation.

If you need a dynamically sized array with varying lengths in each dimension, you may consider using jagged arrays (arrays of arrays), which allow you to have varying lengths for each sub-array. Jagged arrays provide the flexibility to represent data with irregular structures.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to reverse Singly Linked List?

To reverse a singly linked list in Java, you need to manipulate the links between the nodes. The basic idea is to traverse the list, changing the next pointers of each node to point in the reverse direction. This will effectively reverse the order of the linked list.

Here's a Java program to reverse a singly linked list:

```java
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class ReverseLinkedList {

    public static void main(String[] args) {
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);

        System.out.println("Original linked list:");
        printLinkedList(head);

        Node reversedHead = reverseLinkedList(head);

        System.out.println("Reversed linked list:");
        printLinkedList(reversedHead);
    }

    public static Node reverseLinkedList(Node head) {
        Node prev = null;
        Node current = head;
        Node next;

        while (current != null) {
            next = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }

        return prev; // The new head of the reversed linked list
    }

    public static void printLinkedList(Node head) {
        Node current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }
}
```

In this example, we have a `Node` class representing each node of the singly linked list. The `reverseLinkedList` method takes the head node of the original linked list as input and returns the head node of the reversed linked list.

The `reverseLinkedList` method uses three pointers: `prev`, `current`, and `next`. It iterates through the linked list, reversing the direction of the links by changing the `next` pointers of each node. The `current` node becomes the `prev` node, and the `next` node becomes the `current` node.

Finally, the method returns the new head of the reversed linked list, which will be the last node of the original linked list after the reversal.

The `printLinkedList` method is a helper function to print the elements of the linked list. It is used to display both the original and reversed linked lists in the example.

When you run the program, it will display the original linked list and the reversed linked list:

```yaml
Original linked list:
1 2 3 4 5 
Reversed linked list:
5 4 3 2 1 
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Create a Java program to find middle node of linked list in Java in one pass?

To find the middle node of a linked list in one pass, you can use the two-pointer approach. The idea is to use two pointers: a slow pointer and a fast pointer. The slow pointer advances one step at a time, while the fast pointer advances two steps at a time. When the fast pointer reaches the end of the list, the slow pointer will be at the middle node.

Here's a Java program to find the middle node of a linked list in one pass:

```java
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class MiddleNodeLinkedList {

    public static void main(String[] args) {
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);

        System.out.println("Original linked list:");
        printLinkedList(head);

        Node middleNode = findMiddleNode(head);
        System.out.println("Middle node: " + middleNode.data);
    }

    public static Node findMiddleNode(Node head) {
        Node slowPointer = head;
        Node fastPointer = head;

        while (fastPointer != null && fastPointer.next != null) {
            slowPointer = slowPointer.next;
            fastPointer = fastPointer.next.next;
        }

        return slowPointer;
    }

    public static void printLinkedList(Node head) {
        Node current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }
}
```

In this example, we have a `Node` class representing each node of the linked list. The `findMiddleNode` method takes the head node of the linked list as input and returns the middle node.

The `findMiddleNode` method uses two pointers, `slowPointer` and `fastPointer`, both initialized to the head of the linked list. The `fastPointer` advances two steps at a time, and the `slowPointer` advances one step at a time.

When the `fastPointer` reaches the end of the list (i.e., it becomes `null` or `fastPointer.next` becomes `null`), the `slowPointer` will be at the middle node of the linked list.

Finally, the method returns the middle node.

The `printLinkedList` method is a helper function to print the elements of the linked list. It is used to display the original linked list and the middle node in the example.

When you run the program, it will display the original linked list and the middle node:

```yaml
Original linked list:
1 2 3 4 5 
Middle node: 3
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find if a linked list contains cycle or not in Java?

To determine if a linked list contains a cycle (i.e., a loop), you can use the Floyd's Cycle Detection algorithm, also known as the "Tortoise and Hare" algorithm. This algorithm uses two pointers to traverse the linked list—one moving one step at a time (slow pointer) and the other moving two steps at a time (fast pointer). If there is a cycle in the linked list, the fast pointer will eventually catch up to the slow pointer.

Here's a Java program to check if a linked list contains a cycle:

```java
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedListCycleDetection {

    public static void main(String[] args) {
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);

        // Create a cycle by connecting the last node to the second node
        head.next.next.next.next.next = head.next;

        boolean hasCycle = detectCycle(head);
        System.out.println("Does the linked list contain a cycle? " + hasCycle);
    }

    public static boolean detectCycle(Node head) {
        if (head == null || head.next == null) {
            return false;
        }

        Node slowPointer = head;
        Node fastPointer = head;

        while (fastPointer != null && fastPointer.next != null) {
            slowPointer = slowPointer.next;
            fastPointer = fastPointer.next.next;

            if (slowPointer == fastPointer) {
                return true; // Cycle detected
            }
        }

        return false; // No cycle detected
    }
}
```

In this example, we have a `Node` class representing each node of the linked list. The `detectCycle` method takes the head node of the linked list as input and returns a boolean indicating whether the linked list contains a cycle or not.

The `detectCycle` method uses two pointers, `slowPointer` and `fastPointer`, both initialized to the head of the linked list. The `fastPointer` moves two steps at a time, while the `slowPointer` moves one step at a time.

If there is a cycle in the linked list, the fast pointer will eventually catch up to the slow pointer, and they will meet at some node within the cycle. If there is no cycle, the fast pointer will reach the end of the linked list (i.e., become `null` or `fastPointer.next` will become `null`) before catching up to the slow pointer.

The method returns `true` if a cycle is detected and `false` otherwise.

In the example above, we intentionally create a cycle in the linked list by connecting the last node to the second node. When you run the program, it will detect the cycle and output:

```css
Does the linked list contain a cycle? true
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to find nth element from end of linked list

To find the nth element from the end of a linked list, you can use a two-pointer approach. The basic idea is to use two pointers: a fast pointer and a slow pointer. The fast pointer will advance n steps ahead of the slow pointer. When the fast pointer reaches the end of the list, the slow pointer will be at the nth element from the end.

Here's a Java program to find the nth element from the end of a linked list:

```java
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class NthElementFromEnd {

    public static void main(String[] args) {
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);

        int n = 2; // The value of n for which we want to find the element from the end

        int nthElement = findNthElementFromEnd(head, n);
        System.out.println("The " + n + "th element from the end is: " + nthElement);
    }

    public static int findNthElementFromEnd(Node head, int n) {
        if (head == null || n <= 0) {
            throw new IllegalArgumentException("Invalid input");
        }

        Node fastPointer = head;
        Node slowPointer = head;

        // Move the fast pointer n steps ahead
        for (int i = 0; i < n; i++) {
            if (fastPointer == null) {
                throw new IllegalArgumentException("List length is smaller than n");
            }
            fastPointer = fastPointer.next;
        }

        // Move both pointers until the fast pointer reaches the end of the list
        while (fastPointer != null) {
            fastPointer = fastPointer.next;
            slowPointer = slowPointer.next;
        }

        return slowPointer.data; // The data of the nth element from the end
    }
}
```

In this example, we have a `Node` class representing each node of the linked list. The `findNthElementFromEnd` method takes the head node of the linked list and the value of n as input and returns the data of the nth element from the end.

The method uses two pointers, `fastPointer` and `slowPointer`, both initialized to the head of the linked list. The fast pointer moves n steps ahead of the slow pointer.

Then, both pointers move simultaneously until the fast pointer reaches the end of the list (i.e., becomes `null`). At this point, the slow pointer will be at the nth element from the end.

The method returns the data of the node pointed to by the slow pointer, which is the nth element from the end.

In the example above, we want to find the 2nd element from the end, and the output will be:

```vbnet
The 2th element from the end is: 4
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to check if linked list is palindrome in Java

To check if a linked list is a palindrome in Java, you can use a two-step approach. First, find the middle node of the linked list using the slow and fast pointer technique. Next, reverse the second half of the linked list. Finally, compare the elements of the first half of the original linked list with the reversed second half to determine if it is a palindrome.

Here's a Java program to check if a linked list is a palindrome:

```java
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class PalindromeLinkedList {

    public static void main(String[] args) {
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(2);
        head.next.next.next.next = new Node(1);

        boolean isPalindrome = isLinkedListPalindrome(head);
        System.out.println("Is the linked list a palindrome? " + isPalindrome);
    }

    public static boolean isLinkedListPalindrome(Node head) {
        if (head == null || head.next == null) {
            return true; // An empty list or a single node is considered a palindrome
        }

        // Step 1: Find the middle node of the linked list
        Node slowPointer = head;
        Node fastPointer = head;

        while (fastPointer != null && fastPointer.next != null) {
            slowPointer = slowPointer.next;
            fastPointer = fastPointer.next.next;
        }

        // Step 2: Reverse the second half of the linked list
        Node secondHalf = reverseLinkedList(slowPointer);

        // Step 3: Compare elements of first half with reversed second half
        Node firstHalf = head;
        while (secondHalf != null) {
            if (firstHalf.data != secondHalf.data) {
                return false; // Not a palindrome
            }
            firstHalf = firstHalf.next;
            secondHalf = secondHalf.next;
        }

        return true; // The linked list is a palindrome
    }

    public static Node reverseLinkedList(Node head) {
        Node prev = null;
        Node current = head;
        Node next;

        while (current != null) {
            next = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }

        return prev; // The new head of the reversed linked list
    }
}
```

In this example, we have a `Node` class representing each node of the linked list. The `isLinkedListPalindrome` method takes the head node of the linked list as input and returns a boolean indicating whether the linked list is a palindrome or not.

The method uses the two-pointer approach to find the middle node of the linked list. Then, it reverses the second half of the linked list using the `reverseLinkedList` method.

Finally, the method compares the elements of the first half of the original linked list with the reversed second half. If they are the same, the linked list is a palindrome; otherwise, it is not.

In the example above, the linked list contains the elements {1, 2, 3, 2, 1}, which is a palindrome. The program will output:

```vbnet
Is the linked list a palindrome? true
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Add two numbers represented by linked list in Java

To add two numbers represented by linked lists in Java, you can traverse the two linked lists simultaneously and perform the addition digit by digit. The key is to handle carry from one digit to the next while iterating through both linked lists. If one linked list is shorter than the other, you can assume the shorter list has 0s as the missing digits for the addition.

Here's a Java program to add two numbers represented by linked lists:

```java
class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}

public class AddTwoNumbersLinkedList {

    public static void main(String[] args) {
        ListNode l1 = new ListNode(2);
        l1.next = new ListNode(4);
        l1.next.next = new ListNode(3);

        ListNode l2 = new ListNode(5);
        l2.next = new ListNode(6);
        l2.next.next = new ListNode(4);

        ListNode sum = addTwoNumbers(l1, l2);

        System.out.println("Result of adding two linked lists:");
        printLinkedList(sum);
    }

    public static ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummyHead = new ListNode(0);
        ListNode current = dummyHead;
        int carry = 0;

        while (l1 != null || l2 != null) {
            int x = (l1 != null) ? l1.val : 0;
            int y = (l2 != null) ? l2.val : 0;

            int sum = x + y + carry;
            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;

            if (l1 != null) l1 = l1.next;
            if (l2 != null) l2 = l2.next;
        }

        if (carry > 0) {
            current.next = new ListNode(carry);
        }

        return dummyHead.next;
    }

    public static void printLinkedList(ListNode head) {
        ListNode current = head;
        while (current != null) {
            System.out.print(current.val + " ");
            current = current.next;
        }
        System.out.println();
    }
}
```

In this example, we have a `ListNode` class representing each node of the linked list. The `addTwoNumbers` method takes two linked lists (`l1` and `l2`) representing the numbers to be added. It returns a new linked list representing the sum of the two numbers.

The method iterates through the linked lists simultaneously, calculating the sum of the digits and the carry for each digit. It creates a new linked list to store the result of the addition.

The `printLinkedList` method is a helper function to print the elements of the linked list. It is used to display the result of the addition in the example.

When you run the program, it will output:

```rust
Result of adding two linked lists:
7 0 8
```

In this example, the linked lists represent the numbers `342` and `465`, and the result of the addition is the linked list representing the number `807`.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to sort a Stack using a temporary Stack?

To sort a stack using a temporary stack in Java, you can use the following algorithm:

1. Create a temporary stack to hold the sorted elements.
2. While the original stack is not empty, pop the top element from the original stack.
3. If the temporary stack is empty or the popped element is greater than the top element of the temporary stack, push the popped element into the temporary stack.
4. If the popped element is smaller than or equal to the top element of the temporary stack, keep popping elements from the temporary stack and pushing them back to the original stack until the top element of the temporary stack is greater than the popped element.
5. Repeat steps 2 to 4 until the original stack becomes empty.
6. At this point, the temporary stack will be sorted in ascending order.
7. To make it a descending order, you can transfer the elements back to the original stack.

Here's a Java program to sort a stack using a temporary stack:

```java
import java.util.Stack;

public class SortStackUsingTemporaryStack {

    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        stack.push(10);
        stack.push(5);
        stack.push(8);
        stack.push(3);
        stack.push(7);

        System.out.println("Original Stack:");
        printStack(stack);

        sortStack(stack);

        System.out.println("Sorted Stack (in descending order):");
        printStack(stack);
    }

    public static void sortStack(Stack<Integer> stack) {
        Stack<Integer> tempStack = new Stack<>();

        while (!stack.isEmpty()) {
            int temp = stack.pop();

            while (!tempStack.isEmpty() && tempStack.peek() > temp) {
                stack.push(tempStack.pop());
            }

            tempStack.push(temp);
        }

        // To make the sorted stack in descending order
        while (!tempStack.isEmpty()) {
            stack.push(tempStack.pop());
        }
    }

    public static void printStack(Stack<Integer> stack) {
        for (Integer num : stack) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

In this example, we create a stack with integers and sort it in descending order using a temporary stack. The `sortStack` method sorts the elements of the original stack using a temporary stack.

When you run the program, it will display the original stack and the sorted stack in descending order:

```mathematica
Original Stack:
10 5 8 3 7 
Sorted Stack (in descending order):
10 8 7 5 3 
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Implement Binary Search Tree (BST)

 In this implementation, each node of the BST has an integer value, and the tree maintains the BST property where the value of each node is greater than all the values in its left subtree and less than all the values in its right subtree.

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinarySearchTree {

    private TreeNode root;

    public BinarySearchTree() {
        this.root = null;
    }

    public void insert(int val) {
        this.root = insertRec(this.root, val);
    }

    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }

        return root;
    }

    public boolean search(int val) {
        return searchRec(this.root, val);
    }

    private boolean searchRec(TreeNode root, int val) {
        if (root == null) {
            return false;
        }

        if (val == root.val) {
            return true;
        } else if (val < root.val) {
            return searchRec(root.left, val);
        } else {
            return searchRec(root.right, val);
        }
    }

    public void inorderTraversal() {
        inorderTraversalRec(this.root);
        System.out.println();
    }

    private void inorderTraversalRec(TreeNode root) {
        if (root != null) {
            inorderTraversalRec(root.left);
            System.out.print(root.val + " ");
            inorderTraversalRec(root.right);
        }
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        bst.insert(50);
        bst.insert(30);
        bst.insert(70);
        bst.insert(20);
        bst.insert(40);
        bst.insert(60);
        bst.insert(80);

        System.out.println("Inorder Traversal:");
        bst.inorderTraversal();

        int searchValue = 40;
        boolean isPresent = bst.search(searchValue);
        System.out.println("Is " + searchValue + " present in the BST? " + isPresent);
    }
}
```

In this implementation, the `TreeNode` class represents each node of the BST, and the `BinarySearchTree` class is the BST itself. The `insert` method is used to insert elements into the BST, and the `search` method is used to check if an element is present in the BST.

The `inorderTraversal` method performs an inorder traversal of the BST, which results in a sorted order when the elements are printed. The `main` method demonstrates the usage of the BST by inserting elements and performing a search operation.

When you run the program, it will display the inorder traversal of the BST and whether a particular value is present in the BST or not.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Find min and max value from Binary Search Tree (BST)

To find the minimum and maximum values from a Binary Search Tree (BST) in Java, you can simply traverse the tree as far left as possible to find the minimum value (the leftmost node) and as far right as possible to find the maximum value (the rightmost node).

Here's the Java code to find the minimum and maximum values from a BST:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinarySearchTree {

    private TreeNode root;

    public BinarySearchTree() {
        this.root = null;
    }

    public void insert(int val) {
        this.root = insertRec(this.root, val);
    }

    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }

        return root;
    }

    public int findMin() {
        if (root == null) {
            throw new IllegalStateException("BST is empty");
        }
        return findMinRec(root);
    }

    private int findMinRec(TreeNode root) {
        if (root.left == null) {
            return root.val;
        }
        return findMinRec(root.left);
    }

    public int findMax() {
        if (root == null) {
            throw new IllegalStateException("BST is empty");
        }
        return findMaxRec(root);
    }

    private int findMaxRec(TreeNode root) {
        if (root.right == null) {
            return root.val;
        }
        return findMaxRec(root.right);
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        bst.insert(50);
        bst.insert(30);
        bst.insert(70);
        bst.insert(20);
        bst.insert(40);
        bst.insert(60);
        bst.insert(80);

        int minValue = bst.findMin();
        int maxValue = bst.findMax();

        System.out.println("Minimum value in the BST: " + minValue);
        System.out.println("Maximum value in the BST: " + maxValue);
    }
}
```

In this implementation, we've added the `findMin` and `findMax` methods to the `BinarySearchTree` class. These methods use recursive helper methods, `findMinRec` and `findMaxRec`, to traverse the tree and find the minimum and maximum values, respectively.

The `findMinRec` method traverses the left subtree until it reaches the leftmost node, which holds the minimum value.

The `findMaxRec` method traverses the right subtree until it reaches the rightmost node, which holds the maximum value.

The `main` method demonstrates the usage of these methods by inserting elements into the BST and then finding the minimum and maximum values from the tree. When you run the program, it will display the minimum and maximum values from the BST:

```yaml
Minimum value in the BST: 20
Maximum value in the BST: 80
```

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Find height of a Binary Search Tree (BST)

To find the height of a Binary Search Tree (BST) in Java, you can use a recursive approach. The height of a BST is the maximum depth of the tree, which is the maximum number of edges from the root node to any leaf node.

Here's the Java code to find the height of a BST:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinarySearchTree {

    private TreeNode root;

    public BinarySearchTree() {
        this.root = null;
    }

    public void insert(int val) {
        this.root = insertRec(this.root, val);
    }

    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }

        return root;
    }

    public int findHeight() {
        return findHeightRec(this.root);
    }

    private int findHeightRec(TreeNode root) {
        if (root == null) {
            return -1; // For an empty tree, height is -1
        }

        int leftHeight = findHeightRec(root.left);
        int rightHeight = findHeightRec(root.right);

        // The height of the tree is the maximum of the left and right subtree heights,
        // plus 1 for the current node
        return Math.max(leftHeight, rightHeight) + 1;
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        bst.insert(50);
        bst.insert(30);
        bst.insert(70);
        bst.insert(20);
        bst.insert(40);
        bst.insert(60);
        bst.insert(80);

        int height = bst.findHeight();
        System.out.println("Height of the BST: " + height);
    }
}
```

In this implementation, we've added the `findHeight` method to the `BinarySearchTree` class. This method uses a recursive helper method, `findHeightRec`, to find the height of the BST.

The `findHeightRec` method recursively calculates the height of the tree. For each node, it calculates the height of its left and right subtrees using recursion. The height of the tree is the maximum of the left and right subtree heights, plus 1 for the current node.

The `main` method demonstrates the usage of the `findHeight` method by inserting elements into the BST and then finding the height of the tree. When you run the program, it will display the height of the BST:

```css
Height of the BST: 2
```

In this example, the height of the BST is 2, which means the BST has a maximum of two edges from the root node to any leaf node.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Implement Binary Search Tree (BST) Level order traversal (breadth first).

To implement the level order traversal (breadth-first traversal) of a Binary Search Tree (BST) in Java, you can use a queue data structure. The level order traversal visits nodes level by level, starting from the root and moving to the left and right subtrees.

Here's the Java code to perform the level order traversal of a BST:

```java
import java.util.LinkedList;
import java.util.Queue;

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinarySearchTree {

    private TreeNode root;

    public BinarySearchTree() {
        this.root = null;
    }

    public void insert(int val) {
        this.root = insertRec(this.root, val);
    }

    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }

        return root;
    }

    public void levelOrderTraversal() {
        if (root == null) {
            System.out.println("BST is empty");
            return;
        }

        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);

        System.out.println("Level Order Traversal:");

        while (!queue.isEmpty()) {
            TreeNode node = queue.poll();
            System.out.print(node.val + " ");

            if (node.left != null) {
                queue.add(node.left);
            }

            if (node.right != null) {
                queue.add(node.right);
            }
        }

        System.out.println();
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        bst.insert(50);
        bst.insert(30);
        bst.insert(70);
        bst.insert(20);
        bst.insert(40);
        bst.insert(60);
        bst.insert(80);

        bst.levelOrderTraversal();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the BST, and the `BinarySearchTree` class is the BST itself. The `insert` method is used to insert elements into the BST.

The `levelOrderTraversal` method performs the level order traversal of the BST. It uses a queue to keep track of the nodes at each level. We start by adding the root node to the queue and then loop through the queue. During each iteration, we remove the node from the front of the queue, print its value, and add its left and right children to the queue if they exist. This process continues until the queue becomes empty, ensuring all nodes are visited level by level.

The `main` method demonstrates the usage of the `levelOrderTraversal` method by inserting elements into the BST and then performing the level order traversal. When you run the program, it will display the level order traversal of the BST:

```mathematica
Level Order Traversal:
50 30 70 20 40 60 80
```

In this example, the level order traversal visits nodes in the BST level by level, starting from the root (50) and moving to the left and right subtrees.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Implement Binary Search Tree (BST) pre-order traversal (depth first).

To implement the pre-order traversal (depth-first traversal) of a Binary Search Tree (BST) in Java, you can use a recursive approach. Pre-order traversal visits the root node first, then its left subtree, and finally its right subtree.

Here's the Java code to perform the pre-order traversal of a BST:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinarySearchTree {

    private TreeNode root;

    public BinarySearchTree() {
        this.root = null;
    }

    public void insert(int val) {
        this.root = insertRec(this.root, val);
    }

    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }

        return root;
    }

    public void preOrderTraversal() {
        System.out.println("Pre-order Traversal:");
        preOrderTraversalRec(this.root);
        System.out.println();
    }

    private void preOrderTraversalRec(TreeNode root) {
        if (root != null) {
            System.out.print(root.val + " ");
            preOrderTraversalRec(root.left);
            preOrderTraversalRec(root.right);
        }
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        bst.insert(50);
        bst.insert(30);
        bst.insert(70);
        bst.insert(20);
        bst.insert(40);
        bst.insert(60);
        bst.insert(80);

        bst.preOrderTraversal();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the BST, and the `BinarySearchTree` class is the BST itself. The `insert` method is used to insert elements into the BST.

The `preOrderTraversal` method performs the pre-order traversal of the BST. It starts at the root and then recursively visits the left and right subtrees in a pre-order manner. During each visit, the value of the current node is printed.

The `preOrderTraversalRec` method is a recursive helper method that performs the actual pre-order traversal. It takes the current node as input and recursively traverses the BST using the pre-order approach.

The `main` method demonstrates the usage of the `preOrderTraversal` method by inserting elements into the BST and then performing the pre-order traversal. When you run the program, it will display the pre-order traversal of the BST:

```css
Pre-order Traversal:
50 30 20 40 70 60 80
```

In this example, the pre-order traversal visits the nodes of the BST in the order: root (50) -> left subtree (30, 20, 40) -> right subtree (70, 60, 80).

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Implement Binary Search Tree (BST) in-order traversal (depth first).

To implement the in-order traversal (depth-first traversal) of a Binary Search Tree (BST) in Java, you can use a recursive approach. In-order traversal visits the left subtree first, then the root node, and finally the right subtree.

Here's the Java code to perform the in-order traversal of a BST:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinarySearchTree {

    private TreeNode root;

    public BinarySearchTree() {
        this.root = null;
    }

    public void insert(int val) {
        this.root = insertRec(this.root, val);
    }

    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }

        return root;
    }

    public void inOrderTraversal() {
        System.out.println("In-order Traversal:");
        inOrderTraversalRec(this.root);
        System.out.println();
    }

    private void inOrderTraversalRec(TreeNode root) {
        if (root != null) {
            inOrderTraversalRec(root.left);
            System.out.print(root.val + " ");
            inOrderTraversalRec(root.right);
        }
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        bst.insert(50);
        bst.insert(30);
        bst.insert(70);
        bst.insert(20);
        bst.insert(40);
        bst.insert(60);
        bst.insert(80);

        bst.inOrderTraversal();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the BST, and the `BinarySearchTree` class is the BST itself. The `insert` method is used to insert elements into the BST.

The `inOrderTraversal` method performs the in-order traversal of the BST. It starts at the leftmost node, then visits the root node, and finally the right subtree. During each visit, the value of the current node is printed.

The `inOrderTraversalRec` method is a recursive helper method that performs the actual in-order traversal. It takes the current node as input and recursively traverses the BST using the in-order approach.

The `main` method demonstrates the usage of the `inOrderTraversal` method by inserting elements into the BST and then performing the in-order traversal. When you run the program, it will display the in-order traversal of the BST:

```css
In-order Traversal:
20 30 40 50 60 70 80
```

In this example, the in-order traversal visits the nodes of the BST in ascending order, as the BST maintains the property that the left child is always less than the parent, and the right child is always greater than the parent.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Implement Binary Search Tree (BST) post-order traversal (depth first).

To implement the post-order traversal (depth-first traversal) of a Binary Search Tree (BST) in Java, you can use a recursive approach. Post-order traversal visits the left subtree first, then the right subtree, and finally the root node.

Here's the Java code to perform the post-order traversal of a BST:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinarySearchTree {

    private TreeNode root;

    public BinarySearchTree() {
        this.root = null;
    }

    public void insert(int val) {
        this.root = insertRec(this.root, val);
    }

    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }

        return root;
    }

    public void postOrderTraversal() {
        System.out.println("Post-order Traversal:");
        postOrderTraversalRec(this.root);
        System.out.println();
    }

    private void postOrderTraversalRec(TreeNode root) {
        if (root != null) {
            postOrderTraversalRec(root.left);
            postOrderTraversalRec(root.right);
            System.out.print(root.val + " ");
        }
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        bst.insert(50);
        bst.insert(30);
        bst.insert(70);
        bst.insert(20);
        bst.insert(40);
        bst.insert(60);
        bst.insert(80);

        bst.postOrderTraversal();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the BST, and the `BinarySearchTree` class is the BST itself. The `insert` method is used to insert elements into the BST.

The `postOrderTraversal` method performs the post-order traversal of the BST. It starts at the leftmost node, then visits the right subtree, and finally the root node. During each visit, the value of the current node is printed.

The `postOrderTraversalRec` method is a recursive helper method that performs the actual post-order traversal. It takes the current node as input and recursively traverses the BST using the post-order approach.

The `main` method demonstrates the usage of the `postOrderTraversal` method by inserting elements into the BST and then performing the post-order traversal. When you run the program, it will display the post-order traversal of the BST:

```css
Post-order Traversal:
20 40 30 60 80 70 50
```

In this example, the post-order traversal visits the nodes of the BST in the order: left subtree (20, 40, 30) -> right subtree (60, 80, 70) -> root (50).

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to check the given Binary Tree is Binary Search Tree (BST) or not?

To check if a given binary tree is a Binary Search Tree (BST) in Java, you can perform an inorder traversal of the tree and check if the elements are in sorted order. In a BST, the inorder traversal of the tree will always produce a sorted list of elements.

Here's the Java code to check if a given binary tree is a Binary Search Tree (BST):

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public void insert(int val) {
        this.root = insertRec(this.root, val);
    }

    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }

        return root;
    }

    public boolean isBST() {
        return isBSTRec(this.root, Integer.MIN_VALUE, Integer.MAX_VALUE);
    }

    private boolean isBSTRec(TreeNode root, int min, int max) {
        if (root == null) {
            return true;
        }

        if (root.val <= min || root.val >= max) {
            return false;
        }

        return isBSTRec(root.left, min, root.val) && isBSTRec(root.right, root.val, max);
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.insert(50);
        binaryTree.insert(30);
        binaryTree.insert(70);
        binaryTree.insert(20);
        binaryTree.insert(40);
        binaryTree.insert(60);
        binaryTree.insert(80);

        boolean isBST = binaryTree.isBST();
        System.out.println("Is the given binary tree a BST? " + isBST);
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `insert` method is used to insert elements into the binary tree.

The `isBST` method is used to check if the binary tree is a BST. It calls the recursive helper method `isBSTRec`, which takes the current node, along with a minimum and maximum value, as input. The `isBSTRec` method checks if the value of the current node is within the allowed range based on its position in the tree and recursively checks the left and right subtrees.

The `main` method demonstrates the usage of the `isBST` method by inserting elements into the binary tree and then checking if it is a BST or not. When you run the program, it will display whether the given binary tree is a BST or not:

```vbnet
Is the given binary tree a BST? true
```

In this example, the given binary tree is a BST as it satisfies the BST property: the left subtree contains nodes with values less than the root, and the right subtree contains nodes with values greater than the root.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to delete a node from Binary Search Tree (BST)?

To delete a node from a Binary Search Tree (BST) in Java, you need to handle different cases based on the number of children the node has. There are three possible cases:

1. Node with no children (leaf node): Simply remove the node from the tree.
2. Node with one child: Remove the node and link its parent to its only child.
3. Node with two children: Find the inorder successor (the smallest node in the right subtree) of the node to be deleted, copy its value to the node, and then delete the inorder successor.

Here's the Java code to delete a node from a BST:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinarySearchTree {

    private TreeNode root;

    public BinarySearchTree() {
        this.root = null;
    }

    public void insert(int val) {
        this.root = insertRec(this.root, val);
    }

    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }

        return root;
    }

    public void delete(int val) {
        this.root = deleteRec(this.root, val);
    }

    private TreeNode deleteRec(TreeNode root, int val) {
        if (root == null) {
            return null;
        }

        if (val < root.val) {
            root.left = deleteRec(root.left, val);
        } else if (val > root.val) {
            root.right = deleteRec(root.right, val);
        } else {
            // Node with only one child or no child
            if (root.left == null) {
                return root.right;
            } else if (root.right == null) {
                return root.left;
            }

            // Node with two children: Find the inorder successor
            root.val = findMinValue(root.right);

            // Delete the inorder successor
            root.right = deleteRec(root.right, root.val);
        }

        return root;
    }

    private int findMinValue(TreeNode root) {
        int minValue = root.val;
        while (root.left != null) {
            minValue = root.left.val;
            root = root.left;
        }
        return minValue;
    }

    public void inOrderTraversal() {
        System.out.println("In-order Traversal:");
        inOrderTraversalRec(this.root);
        System.out.println();
    }

    private void inOrderTraversalRec(TreeNode root) {
        if (root != null) {
            inOrderTraversalRec(root.left);
            System.out.print(root.val + " ");
            inOrderTraversalRec(root.right);
        }
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        bst.insert(50);
        bst.insert(30);
        bst.insert(70);
        bst.insert(20);
        bst.insert(40);
        bst.insert(60);
        bst.insert(80);

        System.out.println("Before deletion:");
        bst.inOrderTraversal();

        int deleteValue = 50;
        bst.delete(deleteValue);

        System.out.println("After deleting " + deleteValue + ":");
        bst.inOrderTraversal();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the BST, and the `BinarySearchTree` class is the BST itself. The `insert` method is used to insert elements into the BST.

The `delete` method is used to delete a node with a given value from the BST. It calls the recursive helper method `deleteRec`, which handles different cases of deletion based on the number of children the node has.

The `findMinValue` method is used to find the minimum value in the right subtree of a node with two children. This is used to find the inorder successor during node deletion.

The `inOrderTraversal` method performs an inorder traversal of the BST, printing the values of nodes in sorted order.

The `main` method demonstrates the usage of the `delete` method by inserting elements into the BST, then deleting a node, and finally performing an inorder traversal before and after deletion. When you run the program, it will display the BST before and after deletion:

```mathematica
Before deletion:
20 30 40 50 60 70 80 
After deleting 50:
20 30 40 60 70 80 
```

In this example, the node with the value 50 is successfully deleted from the BST, and the BST maintains its properties after deletion.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Binary tree level order traversal

To perform the level-order traversal (breadth-first traversal) of a binary tree in Java, you can use a queue data structure. Level-order traversal visits nodes level by level, starting from the root and moving to the left and right subtrees.

Here's the Java code to perform the level-order traversal of a binary tree:

```java
import java.util.LinkedList;
import java.util.Queue;

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public void levelOrderTraversal() {
        if (root == null) {
            System.out.println("Binary tree is empty");
            return;
        }

        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);

        System.out.println("Level Order Traversal:");

        while (!queue.isEmpty()) {
            TreeNode node = queue.poll();
            System.out.print(node.val + " ");

            if (node.left != null) {
                queue.add(node.left);
            }

            if (node.right != null) {
                queue.add(node.right);
            }
        }

        System.out.println();
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);

        binaryTree.levelOrderTraversal();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `levelOrderTraversal` method performs the level-order traversal of the binary tree using a queue.

The `levelOrderTraversal` method starts by adding the root node to the queue and then loops through the queue. During each iteration, it removes the node from the front of the queue, prints its value, and adds its left and right children to the queue if they exist. This process continues until the queue becomes empty, ensuring all nodes are visited level by level.

The `main` method demonstrates the usage of the `levelOrderTraversal` method by creating a binary tree and then performing the level-order traversal. When you run the program, it will display the level-order traversal of the binary tree:

```mathematica
Level Order Traversal:
1 2 3 4 5
```

In this example, the level-order traversal visits the nodes of the binary tree level by level, starting from the root (1) and moving to the left and right subtrees (2, 3, 4, 5).

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Binary tree spiral order traversal

Binary tree spiral order traversal is a variation of level-order traversal where nodes are visited alternately from left to right and right to left at each level. To implement the spiral order traversal of a binary tree in Java, you can use a combination of two stacks.

Here's the Java code to perform the spiral order traversal of a binary tree:

```java
import java.util.Stack;

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public void spiralOrderTraversal() {
        if (root == null) {
            System.out.println("Binary tree is empty");
            return;
        }

        Stack<TreeNode> stack1 = new Stack<>();
        Stack<TreeNode> stack2 = new Stack<>();
        stack1.push(root);

        System.out.println("Spiral Order Traversal:");

        while (!stack1.isEmpty() || !stack2.isEmpty()) {
            while (!stack1.isEmpty()) {
                TreeNode node = stack1.pop();
                System.out.print(node.val + " ");

                if (node.right != null) {
                    stack2.push(node.right);
                }

                if (node.left != null) {
                    stack2.push(node.left);
                }
            }

            while (!stack2.isEmpty()) {
                TreeNode node = stack2.pop();
                System.out.print(node.val + " ");

                if (node.left != null) {
                    stack1.push(node.left);
                }

                if (node.right != null) {
                    stack1.push(node.right);
                }
            }
        }

        System.out.println();
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);
        binaryTree.root.right.left = new TreeNode(6);
        binaryTree.root.right.right = new TreeNode(7);

        binaryTree.spiralOrderTraversal();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `spiralOrderTraversal` method performs the spiral order traversal of the binary tree using two stacks.

The `spiralOrderTraversal` method uses `stack1` and `stack2` to traverse the binary tree in a spiral order. It starts by pushing the root node into `stack1` and then alternates between popping nodes from `stack1` and pushing their left and right children into `stack2`, and vice versa. This way, nodes are visited alternately from left to right and right to left at each level.

The `main` method demonstrates the usage of the `spiralOrderTraversal` method by creating a binary tree and then performing the spiral order traversal. When you run the program, it will display the spiral order traversal of the binary tree:

```css
Spiral Order Traversal:
1 2 3 7 6 5 4
```

In this example, the spiral order traversal visits the nodes of the binary tree in the order: root (1) -> left to right (2, 3) -> right to left (7, 6) -> left to right (5, 4).

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Binary tree reverse level order traversal

To perform the reverse level-order traversal of a binary tree in Java, you can use a queue and a stack data structure. The reverse level-order traversal visits nodes level by level, starting from the last level and moving up to the root.

Here's the Java code to perform the reverse level-order traversal of a binary tree:

```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Stack;

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public void reverseLevelOrderTraversal() {
        if (root == null) {
            System.out.println("Binary tree is empty");
            return;
        }

        Queue<TreeNode> queue = new LinkedList<>();
        Stack<TreeNode> stack = new Stack<>();
        queue.add(root);

        System.out.println("Reverse Level Order Traversal:");

        while (!queue.isEmpty()) {
            TreeNode node = queue.poll();
            stack.push(node);

            if (node.right != null) {
                queue.add(node.right);
            }

            if (node.left != null) {
                queue.add(node.left);
            }
        }

        while (!stack.isEmpty()) {
            System.out.print(stack.pop().val + " ");
        }

        System.out.println();
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);
        binaryTree.root.right.left = new TreeNode(6);
        binaryTree.root.right.right = new TreeNode(7);

        binaryTree.reverseLevelOrderTraversal();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `reverseLevelOrderTraversal` method performs the reverse level-order traversal of the binary tree using a queue and a stack.

The `reverseLevelOrderTraversal` method starts by adding the root node to the queue and then loops through the queue. During each iteration, it removes the node from the front of the queue, pushes it onto the stack, and adds its right and left children to the queue if they exist. This process continues until the queue becomes empty.

After adding all nodes to the stack, it prints the elements from the stack, which gives the reverse level-order traversal of the binary tree.

The `main` method demonstrates the usage of the `reverseLevelOrderTraversal` method by creating a binary tree and then performing the reverse level-order traversal. When you run the program, it will display the reverse level-order traversal of the binary tree:

```mathematica
Reverse Level Order Traversal:
4 5 6 7 2 3 1
```

In this example, the reverse level-order traversal visits the nodes of the binary tree in reverse level order, starting from the last level and moving up to the root.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Binary tree boundary traversal

Binary tree boundary traversal refers to traversing the boundary nodes of a binary tree in a specific order. The boundary nodes include the left boundary, the leaf nodes, and the right boundary. Here's the Java code to perform the binary tree boundary traversal:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public void boundaryTraversal() {
        if (root == null) {
            System.out.println("Binary tree is empty");
            return;
        }

        System.out.println("Boundary Traversal:");
        printLeftBoundary(root);
        printLeafNodes(root);
        printRightBoundary(root.right); // Avoids printing the root again
        System.out.println();
    }

    private void printLeftBoundary(TreeNode node) {
        if (node != null) {
            if (node.left != null) {
                System.out.print(node.val + " ");
                printLeftBoundary(node.left);
            } else if (node.right != null) {
                System.out.print(node.val + " ");
                printLeftBoundary(node.right);
            }
        }
    }

    private void printRightBoundary(TreeNode node) {
        if (node != null) {
            if (node.right != null) {
                printRightBoundary(node.right);
                System.out.print(node.val + " ");
            } else if (node.left != null) {
                printRightBoundary(node.left);
                System.out.print(node.val + " ");
            }
        }
    }

    private void printLeafNodes(TreeNode node) {
        if (node != null) {
            if (node.left == null && node.right == null) {
                System.out.print(node.val + " ");
            }
            printLeafNodes(node.left);
            printLeafNodes(node.right);
        }
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);
        binaryTree.root.right.left = new TreeNode(6);
        binaryTree.root.right.right = new TreeNode(7);
        binaryTree.root.left.left.left = new TreeNode(8);
        binaryTree.root.left.left.right = new TreeNode(9);
        binaryTree.root.left.right.left = new TreeNode(10);

        binaryTree.boundaryTraversal();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `boundaryTraversal` method performs the binary tree boundary traversal.

The `boundaryTraversal` method starts by printing the left boundary of the binary tree using the `printLeftBoundary` method. It then prints the leaf nodes of the binary tree using the `printLeafNodes` method. Finally, it prints the right boundary of the binary tree using the `printRightBoundary` method, but starting from the right child of the root to avoid printing the root twice.

The `printLeftBoundary` method recursively prints the left boundary of the binary tree, starting from the root and moving towards the leftmost leaf. The `printRightBoundary` method recursively prints the right boundary of the binary tree, starting from the rightmost leaf and moving towards the root.

The `printLeafNodes` method recursively prints all the leaf nodes of the binary tree.

The `main` method demonstrates the usage of the `boundaryTraversal` method by creating a binary tree and then performing the boundary traversal. When you run the program, it will display the boundary traversal of the binary tree:

```yaml
Boundary Traversal:
1 2 4 8 9 10 5 7 3 
```

In this example, the boundary traversal visits the left boundary (1, 2, 4, 8, 9, 10), then the leaf nodes (5, 7), and finally, the right boundary (3).

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Print leaf nodes of binary tree

To print the leaf nodes of a binary tree in Java, you can perform a simple recursive traversal of the tree and print the nodes that have no left or right children. Here's the Java code to print the leaf nodes of a binary tree:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public void printLeafNodes() {
        System.out.println("Leaf Nodes:");
        printLeafNodesRec(root);
        System.out.println();
    }

    private void printLeafNodesRec(TreeNode node) {
        if (node == null) {
            return;
        }

        if (node.left == null && node.right == null) {
            System.out.print(node.val + " ");
        }

        printLeafNodesRec(node.left);
        printLeafNodesRec(node.right);
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);
        binaryTree.root.right.left = new TreeNode(6);
        binaryTree.root.right.right = new TreeNode(7);

        binaryTree.printLeafNodes();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `printLeafNodes` method performs the printing of leaf nodes.

The `printLeafNodes` method starts the recursive process by calling the `printLeafNodesRec` method with the root of the binary tree. The `printLeafNodesRec` method recursively traverses the tree and prints the value of the nodes that have no left or right children, i.e., the leaf nodes.

The `main` method demonstrates the usage of the `printLeafNodes` method by creating a binary tree and then printing its leaf nodes. When you run the program, it will display the leaf nodes of the binary tree:

```yaml
Leaf Nodes:
4 5 6 7 
```

In this example, the leaf nodes of the binary tree are 4, 5, 6, and 7.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Count leaf nodes in binary tree

To count the leaf nodes in a binary tree in Java, you can perform a simple recursive traversal of the tree and increment a counter whenever a leaf node is encountered. Here's the Java code to count the leaf nodes in a binary tree:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public int countLeafNodes() {
        return countLeafNodesRec(root);
    }

    private int countLeafNodesRec(TreeNode node) {
        if (node == null) {
            return 0;
        }

        if (node.left == null && node.right == null) {
            return 1;
        }

        return countLeafNodesRec(node.left) + countLeafNodesRec(node.right);
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);
        binaryTree.root.right.left = new TreeNode(6);
        binaryTree.root.right.right = new TreeNode(7);

        int leafNodeCount = binaryTree.countLeafNodes();
        System.out.println("Number of leaf nodes in the binary tree: " + leafNodeCount);
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `countLeafNodes` method performs the counting of leaf nodes.

The `countLeafNodes` method starts the recursive process by calling the `countLeafNodesRec` method with the root of the binary tree. The `countLeafNodesRec` method recursively traverses the tree and increments the counter whenever a leaf node is encountered.

The `main` method demonstrates the usage of the `countLeafNodes` method by creating a binary tree and then counting its leaf nodes. When you run the program, it will display the number of leaf nodes in the binary tree:

```javascript
Number of leaf nodes in the binary tree: 4
```

In this example, the binary tree has four leaf nodes: 4, 5, 6, and 7.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Get maximum element in binary tree

To get the maximum element in a binary tree in Java, you can perform a simple recursive traversal of the tree, keeping track of the maximum value encountered during the traversal. Here's the Java code to get the maximum element in a binary tree:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public int getMaxElement() {
        if (root == null) {
            throw new IllegalStateException("Binary tree is empty");
        }
        return getMaxElementRec(root);
    }

    private int getMaxElementRec(TreeNode node) {
        if (node == null) {
            return Integer.MIN_VALUE;
        }

        int leftMax = getMaxElementRec(node.left);
        int rightMax = getMaxElementRec(node.right);

        return Math.max(node.val, Math.max(leftMax, rightMax));
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);
        binaryTree.root.right.left = new TreeNode(6);
        binaryTree.root.right.right = new TreeNode(7);

        int maxElement = binaryTree.getMaxElement();
        System.out.println("Maximum element in the binary tree: " + maxElement);
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `getMaxElement` method performs the retrieval of the maximum element.

The `getMaxElement` method starts the recursive process by calling the `getMaxElementRec` method with the root of the binary tree. The `getMaxElementRec` method recursively traverses the tree and calculates the maximum element from the node's value, left subtree's maximum, and right subtree's maximum using the `Math.max` function.

The `main` method demonstrates the usage of the `getMaxElement` method by creating a binary tree and then retrieving its maximum element. When you run the program, it will display the maximum element in the binary tree:

```php
Maximum element in the binary tree: 7
```

In this example, the maximum element in the binary tree is 7.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Print all paths from root to leaf in binary tree

To print all paths from the root to leaf nodes in a binary tree in Java, you can perform a recursive traversal of the tree and keep track of the current path while traversing. When you reach a leaf node, you can print the current path. Here's the Java code to print all paths from the root to leaf nodes in a binary tree:

```java
import java.util.ArrayList;
import java.util.List;

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public void printPaths() {
        List<Integer> path = new ArrayList<>();
        printPathsRec(root, path);
    }

    private void printPathsRec(TreeNode node, List<Integer> path) {
        if (node == null) {
            return;
        }

        path.add(node.val);

        if (node.left == null && node.right == null) {
            // Reached a leaf node, print the path
            printPath(path);
        } else {
            printPathsRec(node.left, path);
            printPathsRec(node.right, path);
        }

        path.remove(path.size() - 1);
    }

    private void printPath(List<Integer> path) {
        for (int i = 0; i < path.size() - 1; i++) {
            System.out.print(path.get(i) + " -> ");
        }
        System.out.println(path.get(path.size() - 1));
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);
        binaryTree.root.right.left = new TreeNode(6);
        binaryTree.root.right.right = new TreeNode(7);

        binaryTree.printPaths();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `printPaths` method performs the printing of all paths from the root to leaf nodes.

The `printPaths` method starts the recursive process by calling the `printPathsRec` method with the root of the binary tree and an empty list to store the current path. The `printPathsRec` method recursively traverses the tree and adds each node's value to the current path. When a leaf node is encountered, it prints the current path using the `printPath` method. After that, it backtracks and removes the last node from the path before continuing with the other subtree.

The `printPath` method prints a single path from the root to a leaf node by iterating through the elements in the `path` list.

The `main` method demonstrates the usage of the `printPaths` method by creating a binary tree and then printing all paths from the root to leaf nodes. When you run the program, it will display all paths from the root to leaf nodes:

```rust
1 -> 2 -> 4
1 -> 2 -> 5
1 -> 3 -> 6
1 -> 3 -> 7
```

In this example, the binary tree has four leaf nodes, and each path from the root to a leaf node is printed.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Print vertical sum of binary tree in Java

To print the vertical sum of a binary tree in Java, you can perform a vertical order traversal and keep track of the sum of nodes at each vertical level. You can use a TreeMap to maintain the vertical levels and their corresponding sums. Here's the Java code to print the vertical sum of a binary tree:

```java
import java.util.Map;
import java.util.TreeMap;

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public void printVerticalSum() {
        TreeMap<Integer, Integer> verticalSumMap = new TreeMap<>();
        calculateVerticalSum(root, 0, verticalSumMap);

        System.out.println("Vertical Sum:");
        for (Map.Entry<Integer, Integer> entry : verticalSumMap.entrySet()) {
            System.out.println("Vertical Level " + entry.getKey() + ": " + entry.getValue());
        }
    }

    private void calculateVerticalSum(TreeNode node, int verticalLevel, TreeMap<Integer, Integer> verticalSumMap) {
        if (node == null) {
            return;
        }

        verticalSumMap.put(verticalLevel, verticalSumMap.getOrDefault(verticalLevel, 0) + node.val);

        calculateVerticalSum(node.left, verticalLevel - 1, verticalSumMap);
        calculateVerticalSum(node.right, verticalLevel + 1, verticalSumMap);
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);
        binaryTree.root.right.left = new TreeNode(6);
        binaryTree.root.right.right = new TreeNode(7);

        binaryTree.printVerticalSum();
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `printVerticalSum` method performs the printing of the vertical sum.

The `printVerticalSum` method starts the vertical order traversal by calling the `calculateVerticalSum` method with the root of the binary tree, a vertical level of 0, and an empty TreeMap to store the vertical sums. The `calculateVerticalSum` method recursively traverses the tree and calculates the sum of nodes at each vertical level.

The TreeMap stores the sums for each vertical level in a sorted order. Finally, the method prints the vertical sum for each level.

The `main` method demonstrates the usage of the `printVerticalSum` method by creating a binary tree and then printing the vertical sum. When you run the program, it will display the vertical sum of the binary tree:

```mathematica
Vertical Sum:
Vertical Level -2: 4
Vertical Level -1: 2
Vertical Level 0: 13
Vertical Level 1: 3
```

In this example, the vertical sum for each vertical level of the binary tree is printed. Vertical levels are represented as keys, and their corresponding sums are the values in the TreeMap.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Get level of node in binary tree in Java

To get the level of a specific node in a binary tree in Java, you can perform a depth-first search (DFS) traversal of the tree while keeping track of the level of each node encountered. When the target node is found, you can return its level. Here's the Java code to get the level of a node in a binary tree:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public int getNodeLevel(int target) {
        return getNodeLevel(root, target, 0);
    }

    private int getNodeLevel(TreeNode node, int target, int level) {
        if (node == null) {
            return -1; // Node not found
        }

        if (node.val == target) {
            return level;
        }

        int leftLevel = getNodeLevel(node.left, target, level + 1);
        if (leftLevel != -1) {
            return leftLevel;
        }

        int rightLevel = getNodeLevel(node.right, target, level + 1);
        return rightLevel;
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(1);
        binaryTree.root.left = new TreeNode(2);
        binaryTree.root.right = new TreeNode(3);
        binaryTree.root.left.left = new TreeNode(4);
        binaryTree.root.left.right = new TreeNode(5);
        binaryTree.root.right.left = new TreeNode(6);
        binaryTree.root.right.right = new TreeNode(7);

        int targetNode = 5;
        int level = binaryTree.getNodeLevel(targetNode);
        if (level != -1) {
            System.out.println("Level of node " + targetNode + " is " + level);
        } else {
            System.out.println("Node not found in the binary tree.");
        }
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `getNodeLevel` method performs the retrieval of the level of the specified node.

The `getNodeLevel` method starts the depth-first search (DFS) traversal by calling the `getNodeLevel` method recursively with the root of the binary tree, the target node value, and the current level as 0. The method checks if the current node matches the target value. If yes, it returns the current level. If not, it continues to search for the target node in the left and right subtrees.

If the target node is found in either subtree, the method returns the level of the target node. Otherwise, it returns -1, indicating that the node is not found in the binary tree.

The `main` method demonstrates the usage of the `getNodeLevel` method by creating a binary tree and then retrieving the level of a specified node (in this case, node 5). When you run the program, it will display the level of the target node:

```csharp
Level of node 5 is 2
```

In this example, the level of node 5 in the binary tree is 2.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Lowest common ancestor(LCA) in binary tree in Java

To find the Lowest Common Ancestor (LCA) of two nodes in a binary tree in Java, you can perform a depth-first search (DFS) traversal of the tree. Starting from the root, you can search for the two given nodes in the left and right subtrees. Once you find both nodes in different subtrees or one of the nodes itself, the current node is the LCA. Here's the Java code to find the Lowest Common Ancestor in a binary tree:

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTree {

    private TreeNode root;

    public BinaryTree() {
        this.root = null;
    }

    public TreeNode findLowestCommonAncestor(int p, int q) {
        return findLCA(root, p, q);
    }

    private TreeNode findLCA(TreeNode node, int p, int q) {
        if (node == null) {
            return null;
        }

        if (node.val == p || node.val == q) {
            return node;
        }

        TreeNode leftLCA = findLCA(node.left, p, q);
        TreeNode rightLCA = findLCA(node.right, p, q);

        if (leftLCA != null && rightLCA != null) {
            return node; // Both p and q are found in different subtrees
        }

        return (leftLCA != null) ? leftLCA : rightLCA;
    }

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.root = new TreeNode(3);
        binaryTree.root.left = new TreeNode(5);
        binaryTree.root.right = new TreeNode(1);
        binaryTree.root.left.left = new TreeNode(6);
        binaryTree.root.left.right = new TreeNode(2);
        binaryTree.root.right.left = new TreeNode(0);
        binaryTree.root.right.right = new TreeNode(8);
        binaryTree.root.left.right.left = new TreeNode(7);
        binaryTree.root.left.right.right = new TreeNode(4);

        int p = 5;
        int q = 4;
        TreeNode lca = binaryTree.findLowestCommonAncestor(p, q);

        if (lca != null) {
            System.out.println("Lowest Common Ancestor of " + p + " and " + q + " is " + lca.val);
        } else {
            System.out.println("Either one or both nodes not found in the binary tree.");
        }
    }
}
```

In this implementation, we have a `TreeNode` class representing each node of the binary tree, and the `BinaryTree` class is the binary tree itself. The `findLowestCommonAncestor` method performs the retrieval of the Lowest Common Ancestor.

The `findLowestCommonAncestor` method starts the depth-first search (DFS) traversal by calling the `findLCA` method recursively with the root of the binary tree and the two target nodes, p and q. The `findLCA` method checks if the current node is one of the target nodes. If yes, it returns the node as the LCA. If not, it continues to search for the target nodes in the left and right subtrees.

If the target nodes are found in different subtrees, the current node is the Lowest Common Ancestor, and it is returned. If the target nodes are found in the same subtree, the search continues in that subtree.

The `main` method demonstrates the usage of the `findLowestCommonAncestor` method by creating a binary tree and then finding the Lowest Common Ancestor of two specified nodes (in this case, nodes 5 and 4). When you run the program, it will display the value of the Lowest Common Ancestor:

```csharp
Lowest Common Ancestor of 5 and 4 is 5
```

In this example, the Lowest Common Ancestor of nodes 5 and 4 in the binary tree is node 5.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Search element in row wise and column wise sorted matrix

To search for an element in a row-wise and column-wise sorted matrix efficiently, you can use a binary search approach. Since the matrix is sorted both row-wise and column-wise, you can perform a binary search in each row to find the target element.

Here's the Java code to search for an element in a row-wise and column-wise sorted matrix:

```java
public class SortedMatrixSearch {

    public static boolean searchMatrix(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return false;
        }

        int rows = matrix.length;
        int cols = matrix[0].length;

        int startRow = 0;
        int endRow = rows - 1;
        int startCol = 0;
        int endCol = cols - 1;

        while (startRow <= endRow && startCol <= endCol) {
            int midRow = (startRow + endRow) / 2;
            int midCol = (startCol + endCol) / 2;

            int midElement = matrix[midRow][midCol];

            if (midElement == target) {
                return true;
            } else if (midElement < target) {
                // Search in the right half of the matrix
                startRow = midRow + 1;
                startCol = midCol + 1;
            } else {
                // Search in the left half of the matrix
                endRow = midRow - 1;
                endCol = midCol - 1;
            }
        }

        // If the element is not found in the above process,
        // search in the remaining submatrices separately.
        return searchRemainingRows(matrix, target, startRow, endRow, endCol)
                || searchRemainingCols(matrix, target, startCol, endCol, endRow);
    }

    private static boolean searchRemainingRows(int[][] matrix, int target, int startRow, int endRow, int col) {
        while (startRow <= endRow) {
            int midRow = (startRow + endRow) / 2;
            int midElement = matrix[midRow][col];

            if (midElement == target) {
                return true;
            } else if (midElement < target) {
                startRow = midRow + 1;
            } else {
                endRow = midRow - 1;
            }
        }
        return false;
    }

    private static boolean searchRemainingCols(int[][] matrix, int target, int startCol, int endCol, int row) {
        while (startCol <= endCol) {
            int midCol = (startCol + endCol) / 2;
            int midElement = matrix[row][midCol];

            if (midElement == target) {
                return true;
            } else if (midElement < target) {
                startCol = midCol + 1;
            } else {
                endCol = midCol - 1;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        int[][] matrix = {
                {1, 4, 7, 11, 15},
                {2, 5, 8, 12, 19},
                {3, 6, 9, 16, 22},
                {10, 13, 14, 17, 24},
                {18, 21, 23, 26, 30}
        };

        int target = 9;
        boolean found = searchMatrix(matrix, target);
        System.out.println("Element " + target + " found in matrix: " + found);
    }
}
```

In this implementation, we use two helper methods `searchRemainingRows` and `searchRemainingCols` to perform binary search on the remaining rows and columns of the matrix after completing the main search.

The `searchMatrix` method takes the matrix and the target element as input and starts the binary search in the main diagonal. If the midElement is equal to the target, we return `true`. Otherwise, we adjust the pointers to search in the right half or left half of the matrix based on the comparison.

If the target is not found in the main diagonal, we further search in the remaining rows and columns separately using the helper methods. The process continues until the target is found, or the pointers cross each other, indicating that the element is not present in the matrix.

The `main` method demonstrates the usage of the `searchMatrix` method by creating a sample matrix and then searching for the target element (in this case, 9). When you run the program, it will display whether the element is found in the matrix or not.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Stock buy and sell to maximize profit.

To maximize profit by buying and selling stocks, you can use a simple approach that involves iterating through the array of stock prices and finding the local minima and local maxima. You can buy the stock at the local minima and sell it at the corresponding local maxima. Here's the Java code to maximize the profit through stock buy and sell:

```java
public class StockBuySell {

    public static int maximizeProfit(int[] prices) {
        int n = prices.length;
        if (n <= 1) {
            return 0; // No profit can be made with only one day
        }

        int maxProfit = 0;
        int buy = 0;
        int sell = 0;

        for (int i = 1; i < n; i++) {
            if (prices[i] > prices[i - 1]) {
                // If the price is increasing, sell the stock at this day
                sell = i;
            } else {
                // If the price is decreasing, sell the stock at the previous sell day (if it is greater than buy)
                if (sell > buy) {
                    maxProfit += prices[sell] - prices[buy];
                }
                // Reset the buy and sell days
                buy = i;
                sell = i;
            }
        }

        // If the last transaction results in profit, add it to the maxProfit
        if (sell > buy) {
            maxProfit += prices[sell] - prices[buy];
        }

        return maxProfit;
    }

    public static void main(String[] args) {
        int[] prices = {7, 1, 5, 3, 6, 4}; // Sample stock prices
        int maxProfit = maximizeProfit(prices);
        System.out.println("Maximum Profit: " + maxProfit);
    }
}
```

In this implementation, the `maximizeProfit` method takes an array of stock prices as input and returns the maximum profit that can be achieved through stock buy and sell.

The method iterates through the array of stock prices and updates the `buy` and `sell` days based on whether the price is increasing or decreasing. If the price is increasing, we update the `sell` day, and if the price is decreasing, we sell the stock at the previous `sell` day (if it is greater than `buy`) and then update the `buy` and `sell` days.

The profit is calculated by adding the difference between the sell price and buy price whenever a transaction results in a profit. The loop continues until all stock prices have been processed.

Finally, if the last transaction results in profit (i.e., the `sell` day is greater than the `buy` day), we add the profit from the last transaction to the `maxProfit`.

The `main` method demonstrates the usage of the `maximizeProfit` method with a sample array of stock prices. When you run the program, it will display the maximum profit that can be achieved through stock buy and sell:

```yaml
Maximum Profit: 5
```

In this example, the maximum profit that can be achieved through stock buy and sell is 5.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to implement merge sort in Java

To implement Merge Sort in Java, you can use a recursive approach to divide the array into two halves, sort them separately, and then merge the sorted halves back together. Here's the Java code for the Merge Sort algorithm:

```java
public class MergeSort {

    public static void mergeSort(int[] arr) {
        if (arr == null || arr.length <= 1) {
            return;
        }
        mergeSort(arr, 0, arr.length - 1);
    }

    private static void mergeSort(int[] arr, int left, int right) {
        if (left < right) {
            int mid = left + (right - left) / 2;

            mergeSort(arr, left, mid);
            mergeSort(arr, mid + 1, right);

            merge(arr, left, mid, right);
        }
    }

    private static void merge(int[] arr, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int[] leftArr = new int[n1];
        int[] rightArr = new int[n2];

        for (int i = 0; i < n1; i++) {
            leftArr[i] = arr[left + i];
        }

        for (int j = 0; j < n2; j++) {
            rightArr[j] = arr[mid + 1 + j];
        }

        int i = 0, j = 0;
        int k = left;

        while (i < n1 && j < n2) {
            if (leftArr[i] <= rightArr[j]) {
                arr[k] = leftArr[i];
                i++;
            } else {
                arr[k] = rightArr[j];
                j++;
            }
            k++;
        }

        while (i < n1) {
            arr[k] = leftArr[i];
            i++;
            k++;
        }

        while (j < n2) {
            arr[k] = rightArr[j];
            j++;
            k++;
        }
    }

    public static void main(String[] args) {
        int[] arr = {38, 27, 43, 3, 9, 82, 10};
        mergeSort(arr);

        System.out.println("Sorted Array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

In this implementation, we have a `mergeSort` method that is the entry point for the Merge Sort algorithm. It takes an array as input and sorts the entire array. The `mergeSort` method calls the recursive `mergeSort` method with the left and right indices to perform the actual sorting.

The `mergeSort` method uses the `merge` method to merge the sorted halves back together. The `merge` method takes three arguments: the array to merge, the left index of the first half, and the right index of the second half. It merges the two halves into a sorted array.

The Merge Sort algorithm recursively divides the input array into two halves until it reaches the base case of a single element in each subarray. Then, it merges the sorted subarrays back together to get the final sorted array.

The `main` method demonstrates the usage of the `mergeSort` method with a sample array. When you run the program, it will display the sorted array:

```javascript
Sorted Array:
3 9 10 27 38 43 82
```

In this example, the Merge Sort algorithm has sorted the array in ascending order.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to implement bubble sort in Java

To implement Bubble Sort in Java, you can use a nested loop that compares adjacent elements and swaps them if they are in the wrong order. The largest element "bubbles up" to the end of the array in each pass of the outer loop. Here's the Java code for the Bubble Sort algorithm:

```java
public class BubbleSort {

    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        boolean swapped;

        for (int i = 0; i < n - 1; i++) {
            swapped = false;

            // Compare adjacent elements and swap them if necessary
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    // Swap arr[j] and arr[j + 1]
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }

            // If no two elements were swapped in the inner loop, the array is already sorted
            if (!swapped) {
                break;
            }
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};
        bubbleSort(arr);

        System.out.println("Sorted Array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

In this implementation, we have a `bubbleSort` method that takes an array as input and sorts it using the Bubble Sort algorithm.

The outer loop (with the variable `i`) runs from 0 to `n - 1`, where `n` is the number of elements in the array. In each pass of the outer loop, the largest element is moved to the correct position at the end of the array.

The inner loop (with the variable `j`) runs from 0 to `n - i - 1`. Since the largest element gets bubbled up to the end after each pass, we don't need to compare the elements that have already been placed in their correct positions.

If during the inner loop, a swap occurs between adjacent elements, the `swapped` flag is set to true. If no swaps occur in an entire pass of the outer loop, it means that the array is already sorted, and we can break out of the outer loop early to improve the efficiency of the algorithm.

The `main` method demonstrates the usage of the `bubbleSort` method with a sample array. When you run the program, it will display the sorted array:

```javascript
Sorted Array:
11 12 22 25 34 64 90
```

In this example, the Bubble Sort algorithm has sorted the array in ascending order.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to implement insertion sort in Java

To implement Insertion Sort in Java, you can sort the array by dividing it into a sorted and an unsorted part. In each iteration, you pick an element from the unsorted part and insert it into the correct position in the sorted part of the array. Here's the Java code for the Insertion Sort algorithm:

```java
public class InsertionSort {

    public static void insertionSort(int[] arr) {
        int n = arr.length;

        for (int i = 1; i < n; i++) {
            int key = arr[i];
            int j = i - 1;

            // Move elements of arr[0..i-1] that are greater than key to one position ahead of their current position
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j--;
            }

            // Insert the key into its correct position
            arr[j + 1] = key;
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};
        insertionSort(arr);

        System.out.println("Sorted Array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

In this implementation, we have an `insertionSort` method that takes an array as input and sorts it using the Insertion Sort algorithm.

The outer loop (with the variable `i`) runs from 1 to `n - 1`, where `n` is the number of elements in the array. In each iteration, we pick the element `key` at index `i` and insert it into the correct position in the sorted part of the array, which is in the range `0` to `i - 1`.

The inner loop (with the variable `j`) starts from `i - 1` and goes backward until it finds the correct position for the `key`. The loop moves the elements that are greater than the `key` one position ahead to make space for inserting the `key`.

Finally, the `key` is placed at its correct position in the sorted part of the array.

The `main` method demonstrates the usage of the `insertionSort` method with a sample array. When you run the program, it will display the sorted array:

```javascript
Sorted Array:
11 12 22 25 34 64 90
```

In this example, the Insertion Sort algorithm has sorted the array in ascending order.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to implement hashcode and equals.

In Java, `hashCode()` and `equals()` are two important methods used for hashing and object comparison, respectively. The `hashCode()` method returns an integer value used as an index for storing objects in a hash-based data structure like HashMap, HashSet, etc. The `equals()` method is used to compare two objects for equality.

Here's an example of how to implement `hashCode()` and `equals()` in a simple Java class:

```java
public class Student {
    private int id;
    private String name;

    public Student(int id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + id;
        result = prime * result + ((name == null) ? 0 : name.hashCode());
        return result;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null || getClass() != obj.getClass())
            return false;
        Student other = (Student) obj;
        return id == other.id && (name == null ? other.name == null : name.equals(other.name));
    }

    public static void main(String[] args) {
        Student s1 = new Student(1, "Alice");
        Student s2 = new Student(2, "Bob");
        Student s3 = new Student(1, "Alice");

        // Test equals()
        System.out.println("s1.equals(s2): " + s1.equals(s2)); // false
        System.out.println("s1.equals(s3): " + s1.equals(s3)); // true

        // Test hashCode()
        System.out.println("s1.hashCode(): " + s1.hashCode()); // 66204
        System.out.println("s2.hashCode(): " + s2.hashCode()); // 66205
        System.out.println("s3.hashCode(): " + s3.hashCode()); // 66204
    }
}
```

In this example, we have a `Student` class with two properties: `id` and `name`. We override the `hashCode()` and `equals()` methods to provide custom implementations.

In the `hashCode()` method, we compute the hash code by combining the hash codes of the properties `id` and `name` using a prime number as a multiplier. This helps distribute the hash codes more uniformly.

In the `equals()` method, we first check if the objects being compared are the same (i.e., reference equality). If they are not the same object, we check if they are instances of the same class and then compare their properties for equality.

In the `main` method, we test the `equals()` method to compare two `Student` objects and the `hashCode()` method to get the hash code of each `Student` object.

When you run the program, it will produce the following output:

```makefile
s1.equals(s2): false
s1.equals(s3): true
s1.hashCode(): 66204
s2.hashCode(): 66205
s3.hashCode(): 66204
```

In this example, `s1` and `s3` have the same properties and return `true` when compared with `equals()`, and they also have the same hash code. On the other hand, `s1` and `s2` have different properties and return `false` when compared with `equals()`, and they have different hash codes.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write wait-notify code for producer-consumer problem?

The producer-consumer problem can be solved using the wait-notify mechanism in Java. In this problem, there are two threads: the producer thread that produces items and adds them to a shared buffer, and the consumer thread that consumes items from the shared buffer. The producer must wait when the buffer is full, and the consumer must wait when the buffer is empty.

Here's the Java code implementing the wait-notify mechanism for the producer-consumer problem:

```java
import java.util.LinkedList;
import java.util.Queue;

public class ProducerConsumer {
    private static final int BUFFER_SIZE = 5;
    private static final Queue<Integer> buffer = new LinkedList<>();
    
    public static void main(String[] args) {
        Thread producerThread = new Thread(() -> {
            for (int i = 1; i <= 10; i++) {
                produce(i);
            }
        });

        Thread consumerThread = new Thread(() -> {
            for (int i = 1; i <= 10; i++) {
                consume();
            }
        });

        producerThread.start();
        consumerThread.start();
    }

    private static void produce(int item) {
        synchronized (buffer) {
            while (buffer.size() == BUFFER_SIZE) {
                try {
                    System.out.println("Buffer is full. Producer is waiting...");
                    buffer.wait();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }

            buffer.add(item);
            System.out.println("Produced: " + item);
            buffer.notify(); // Notify the consumer that an item is available in the buffer
        }
    }

    private static void consume() {
        synchronized (buffer) {
            while (buffer.isEmpty()) {
                try {
                    System.out.println("Buffer is empty. Consumer is waiting...");
                    buffer.wait();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }

            int item = buffer.poll();
            System.out.println("Consumed: " + item);
            buffer.notify(); // Notify the producer that space is available in the buffer
        }
    }
}
```

In this code, we have a shared buffer implemented as a `Queue` (LinkedList) with a maximum size of `BUFFER_SIZE`. The producer thread produces integers from 1 to 10 and adds them to the buffer using the `produce()` method. The consumer thread consumes items from the buffer using the `consume()` method.

The `produce()` method acquires the lock on the buffer and checks if it is full. If the buffer is full, the producer waits using `buffer.wait()` until the consumer consumes an item and frees up space in the buffer. Once an item is added to the buffer, the producer calls `buffer.notify()` to notify the consumer that an item is available for consumption.

Similarly, the `consume()` method acquires the lock on the buffer and checks if it is empty. If the buffer is empty, the consumer waits using `buffer.wait()` until the producer produces an item and adds it to the buffer. Once an item is consumed from the buffer, the consumer calls `buffer.notify()` to notify the producer that space is available in the buffer for producing more items.

When you run this program, you will see the producer producing and the consumer consuming items in a synchronized manner. The output may vary between runs, but you should see that the producer waits when the buffer is full and the consumer waits when the buffer is empty.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to implement ArrayList.

Implementing a complete and efficient version of `ArrayList` in Java can be quite involved, as it requires handling dynamic resizing, adding elements, removing elements, and other functionalities efficiently. Below, I'll provide a simplified version of `ArrayList` that focuses on the core functionalities like adding elements, getting elements, and getting the size. Keep in mind that this implementation doesn't handle all edge cases and optimizations.

```java
public class MyArrayList<E> {
    private static final int DEFAULT_CAPACITY = 10;
    private Object[] array;
    private int size;

    public MyArrayList() {
        array = new Object[DEFAULT_CAPACITY];
        size = 0;
    }

    public void add(E element) {
        if (size == array.length) {
            ensureCapacity();
        }
        array[size++] = element;
    }

    public E get(int index) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Index out of range");
        }
        return (E) array[index];
    }

    public int size() {
        return size;
    }

    private void ensureCapacity() {
        int newCapacity = array.length * 2;
        Object[] newArray = new Object[newCapacity];
        System.arraycopy(array, 0, newArray, 0, size);
        array = newArray;
    }

    public static void main(String[] args) {
        MyArrayList<Integer> myList = new MyArrayList<>();

        myList.add(10);
        myList.add(20);
        myList.add(30);

        System.out.println("Size: " + myList.size());
        System.out.println("Element at index 0: " + myList.get(0));
        System.out.println("Element at index 1: " + myList.get(1));
        System.out.println("Element at index 2: " + myList.get(2));
    }
}
```

In this simplified implementation, we have the core functionalities of `ArrayList`: `add`, `get`, and `size`.

1. `add`: Adds an element to the end of the array. If the current capacity is not enough to accommodate the new element, the `ensureCapacity` method doubles the array's capacity.

2. `get`: Retrieves the element at the specified index. It checks for the valid index range before returning the element.

3. `size`: Returns the current size of the `ArrayList`.

4. `ensureCapacity`: This private method doubles the array's capacity when it is full. It creates a new array with increased capacity, copies the elements from the old array to the new one, and updates the `array` reference to the new array.

In the `main` method, we create an instance of `MyArrayList`, add three elements, and then print the size and elements at different indices to demonstrate its functionality.

Please note that this is a basic implementation for educational purposes. The actual `ArrayList` class in Java is more complex and has many other features and optimizations.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. A maximal subarray

To find the maximal subarray (i.e., the contiguous subarray with the largest sum) in a given array of integers, you can use the Kadane's algorithm. It is an efficient algorithm that works in a single pass through the array and has a time complexity of O(n).

Here's the Java code to find the maximal subarray using Kadane's algorithm:

```java
public class MaximalSubarray {

    public static int[] findMaximalSubarray(int[] nums) {
        if (nums == null || nums.length == 0) {
            return new int[0];
        }

        int maxSoFar = nums[0];
        int maxEndingHere = nums[0];
        int start = 0;
        int end = 0;
        int currentStart = 0;

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > maxEndingHere + nums[i]) {
                maxEndingHere = nums[i];
                currentStart = i;
            } else {
                maxEndingHere += nums[i];
            }

            if (maxEndingHere > maxSoFar) {
                maxSoFar = maxEndingHere;
                start = currentStart;
                end = i;
            }
        }

        // Extract the maximal subarray
        int[] result = new int[end - start + 1];
        System.arraycopy(nums, start, result, 0, result.length);
        return result;
    }

    public static void main(String[] args) {
        int[] nums = { -2, 1, -3, 4, -1, 2, 1, -5, 4 };
        int[] maximalSubarray = findMaximalSubarray(nums);

        System.out.println("Maximal Subarray:");
        for (int num : maximalSubarray) {
            System.out.print(num + " ");
        }
    }
}
```

In this implementation, the `findMaximalSubarray` method takes an array `nums` as input and returns the maximal subarray. The algorithm maintains two variables: `maxSoFar` and `maxEndingHere`, which represent the maximum sum found so far and the maximum sum ending at the current position, respectively.

The algorithm iterates through the array, updating `maxEndingHere` with each element and comparing it with the element itself. If `maxEndingHere` becomes negative, it means that the current subarray's sum is not contributing positively to the maximal subarray, so the algorithm resets `maxEndingHere` to the current element, and `currentStart` is updated to the current index.

The algorithm keeps track of the starting and ending indices of the maximal subarray whenever it finds a new maximum sum. Finally, it extracts the subarray from the original array and returns it as the result.

In the `main` method, we demonstrate the usage of the `findMaximalSubarray` method with a sample array `nums`. When you run the program, it will display the maximal subarray:

```yaml
Maximal Subarray:
4 -1 2 1
```

In this example, the maximal subarray is [4, -1, 2, 1], and its sum is 6.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Sort a linked list

To sort a linked list in Java, you can use the Merge Sort algorithm, as it is efficient and well-suited for linked lists. Merge Sort is a divide-and-conquer algorithm that recursively divides the list into two halves, sorts each half, and then merges them back together in a sorted order.

Here's the Java code to sort a linked list using Merge Sort:

```java
public class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = val;
    }
}

public class MergeSortLinkedList {

    public static ListNode sortList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }

        ListNode middle = getMiddle(head);
        ListNode nextOfMiddle = middle.next;
        middle.next = null;

        ListNode left = sortList(head);
        ListNode right = sortList(nextOfMiddle);

        return merge(left, right);
    }

    private static ListNode getMiddle(ListNode head) {
        if (head == null) {
            return null;
        }

        ListNode slow = head;
        ListNode fast = head;

        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        return slow;
    }

    private static ListNode merge(ListNode left, ListNode right) {
        ListNode dummy = new ListNode(-1);
        ListNode current = dummy;

        while (left != null && right != null) {
            if (left.val < right.val) {
                current.next = left;
                left = left.next;
            } else {
                current.next = right;
                right = right.next;
            }
            current = current.next;
        }

        if (left != null) {
            current.next = left;
        }
        if (right != null) {
            current.next = right;
        }

        return dummy.next;
    }

    // Helper method to print the linked list
    public static void printList(ListNode head) {
        ListNode current = head;
        while (current != null) {
            System.out.print(current.val + " ");
            current = current.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        ListNode head = new ListNode(5);
        head.next = new ListNode(2);
        head.next.next = new ListNode(7);
        head.next.next.next = new ListNode(1);
        head.next.next.next.next = new ListNode(3);

        System.out.println("Original Linked List:");
        printList(head);

        head = sortList(head);

        System.out.println("Sorted Linked List:");
        printList(head);
    }
}
```

In this code, we have the `ListNode` class to represent the nodes of the linked list. The `sortList` method is the entry point for the Merge Sort algorithm for the linked list. It takes the head of the linked list as input and returns the head of the sorted linked list.

The `getMiddle` method is used to find the middle node of the linked list, and the `merge` method is used to merge two sorted linked lists.

In the `main` method, we create a sample linked list and print it. Then, we call the `sortList` method to sort the linked list and print the sorted result.

When you run the program, it will display the original linked list and the sorted linked list:

```mathematica
Original Linked List:
5 2 7 1 3 
Sorted Linked List:
1 2 3 5 7 
```

In this example, the linked list is sorted in ascending order using the Merge Sort algorithm for linked lists.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Iterative Quick sort

Iterative Quick Sort is a variation of the Quick Sort algorithm that uses an explicit stack to simulate the function call stack of the recursive version. This implementation avoids the overhead of recursive function calls and is often more efficient for large arrays. Here's the Java code for Iterative Quick Sort:

```java
import java.util.Arrays;
import java.util.Stack;

public class IterativeQuickSort {

    public static void iterativeQuickSort(int[] arr) {
        if (arr == null || arr.length <= 1) {
            return;
        }

        Stack<Integer> stack = new Stack<>();
        int start = 0;
        int end = arr.length - 1;

        stack.push(start);
        stack.push(end);

        while (!stack.isEmpty()) {
            end = stack.pop();
            start = stack.pop();

            int partitionIndex = partition(arr, start, end);

            if (partitionIndex - 1 > start) {
                stack.push(start);
                stack.push(partitionIndex - 1);
            }

            if (partitionIndex + 1 < end) {
                stack.push(partitionIndex + 1);
                stack.push(end);
            }
        }
    }

    private static int partition(int[] arr, int start, int end) {
        int pivot = arr[end];
        int i = start - 1;

        for (int j = start; j < end; j++) {
            if (arr[j] <= pivot) {
                i++;
                swap(arr, i, j);
            }
        }

        swap(arr, i + 1, end);
        return i + 1;
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};

        System.out.println("Original Array:");
        System.out.println(Arrays.toString(arr));

        iterativeQuickSort(arr);

        System.out.println("Sorted Array:");
        System.out.println(Arrays.toString(arr));
    }
}
```

In this implementation, we have the `iterativeQuickSort` method, which takes an array `arr` as input and sorts it using Iterative Quick Sort.

The main idea of Iterative Quick Sort is to simulate the recursive calls using a stack. We use a stack to keep track of the subarray boundaries that need to be sorted. We start with the entire array and keep dividing it into smaller subarrays until the stack is empty.

The `partition` method is used to find the pivot element's correct position in the array and arrange the elements such that all elements to the left of the pivot are less than or equal to it, and all elements to the right are greater than it.

The `swap` method is a utility method to swap elements in the array.

In the `main` method, we demonstrate the usage of the `iterativeQuickSort` method with a sample array `arr`. When you run the program, it will display the original array and the sorted array using Iterative Quick Sort.

Please note that Iterative Quick Sort has the same time complexity as the recursive Quick Sort (average-case O(n log n) and worst-case O(n^2)), but it avoids the overhead of function calls, which may make it more efficient for large arrays.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Bucket sort

Bucket Sort is a sorting algorithm that divides an array into a number of buckets, then sorts the elements within each bucket individually, and finally concatenates the sorted buckets to obtain the sorted array. It is an efficient sorting algorithm for uniformly distributed data.

Here's the Java code for Bucket Sort:

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;

public class BucketSort {

    public static void bucketSort(int[] arr, int numBuckets) {
        if (arr == null || arr.length <= 1 || numBuckets <= 0) {
            return;
        }

        // Find the minimum and maximum values in the array
        int minValue = arr[0];
        int maxValue = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] < minValue) {
                minValue = arr[i];
            } else if (arr[i] > maxValue) {
                maxValue = arr[i];
            }
        }

        // Calculate the range of each bucket
        double range = (double) (maxValue - minValue + 1) / numBuckets;

        // Create and initialize buckets
        ArrayList<Integer>[] buckets = new ArrayList[numBuckets];
        for (int i = 0; i < numBuckets; i++) {
            buckets[i] = new ArrayList<>();
        }

        // Distribute elements into buckets
        for (int i = 0; i < arr.length; i++) {
            int bucketIndex = (int) ((arr[i] - minValue) / range);
            buckets[bucketIndex].add(arr[i]);
        }

        // Sort elements within each bucket
        for (int i = 0; i < numBuckets; i++) {
            Collections.sort(buckets[i]);
        }

        // Concatenate the sorted buckets to obtain the sorted array
        int index = 0;
        for (int i = 0; i < numBuckets; i++) {
            for (int j = 0; j < buckets[i].size(); j++) {
                arr[index++] = buckets[i].get(j);
            }
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};

        System.out.println("Original Array:");
        System.out.println(Arrays.toString(arr));

        bucketSort(arr, 5);

        System.out.println("Sorted Array:");
        System.out.println(Arrays.toString(arr));
    }
}
```

In this implementation, we have the `bucketSort` method, which takes an array `arr` and the number of buckets `numBuckets` as inputs and sorts the array using Bucket Sort.

The algorithm first finds the minimum and maximum values in the array to determine the range of elements. It then creates `numBuckets` buckets and distributes the elements into these buckets based on their range. After that, it sorts the elements within each bucket, typically using an efficient sorting algorithm like insertion sort or quicksort. Finally, it concatenates the sorted buckets to obtain the sorted array.

In the `main` method, we demonstrate the usage of the `bucketSort` method with a sample array `arr` and 5 buckets. When you run the program, it will display the original array and the sorted array using Bucket Sort.

Please note that the performance of Bucket Sort depends on the distribution of the data. For uniformly distributed data, it can be very efficient, but for non-uniformly distributed data, its performance may degrade, and other sorting algorithms like Quick Sort or Merge Sort may be more suitable.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Counting sort

Counting Sort is an efficient sorting algorithm that works well for non-negative integer arrays with a limited range of values. It creates a count array to store the frequency of each element and then uses this information to reconstruct the sorted array.

Here's the Java code for Counting Sort:

```java
import java.util.Arrays;

public class CountingSort {

    public static void countingSort(int[] arr) {
        if (arr == null || arr.length <= 1) {
            return;
        }

        int max = findMaxValue(arr);

        int[] countArray = new int[max + 1];

        // Count the occurrences of each element
        for (int num : arr) {
            countArray[num]++;
        }

        // Update countArray to store the actual position of each element
        for (int i = 1; i < countArray.length; i++) {
            countArray[i] += countArray[i - 1];
        }

        // Create the sorted array
        int[] sortedArray = new int[arr.length];
        for (int i = arr.length - 1; i >= 0; i--) {
            int num = arr[i];
            sortedArray[countArray[num] - 1] = num;
            countArray[num]--;
        }

        // Copy the sorted array back to the original array
        System.arraycopy(sortedArray, 0, arr, 0, arr.length);
    }

    private static int findMaxValue(int[] arr) {
        int max = arr[0];
        for (int num : arr) {
            if (num > max) {
                max = num;
            }
        }
        return max;
    }

    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};

        System.out.println("Original Array:");
        System.out.println(Arrays.toString(arr));

        countingSort(arr);

        System.out.println("Sorted Array:");
        System.out.println(Arrays.toString(arr));
    }
}
```

In this implementation, we have the `countingSort` method, which takes an array `arr` as input and sorts it using Counting Sort.

The algorithm first finds the maximum value in the array to determine the range of elements. It then creates a count array to store the frequency of each element. The count array size is determined by the maximum value found in the original array.

Next, it updates the count array to store the actual position of each element in the sorted array. It does this by adding the current count with the previous count in the count array.

Then, it creates the sorted array by placing each element in its correct position based on the count array. Finally, it copies the sorted array back to the original array.

In the `main` method, we demonstrate the usage of the `countingSort` method with a sample array `arr`. When you run the program, it will display the original array and the sorted array using Counting Sort.

Counting Sort has a time complexity of O(n + k), where n is the number of elements in the array, and k is the range of elements. It is efficient when the range of values is not significantly larger than the number of elements. However, it may not be suitable for arrays with large ranges or negative numbers. In such cases, other sorting algorithms like Merge Sort or Quick Sort are more appropriate.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Square root of number

In Java, you can find the square root of a number using the `Math.sqrt()` method from the `java.lang.Math` class. This method returns the square root of the given double value.

Here's an example of finding the square root of a number in Java:

```java
public class SquareRootExample {

    public static void main(String[] args) {
        double number = 25.0;

        double squareRoot = Math.sqrt(number);

        System.out.println("Square root of " + number + " is: " + squareRoot);
    }
}
```

In this example, we have a variable `number` initialized with the value `25.0`. We then use the `Math.sqrt()` method to find its square root and store it in the variable `squareRoot`. Finally, we print the square root using the `System.out.println()` method.

When you run this program, it will output:

```csharp
Square root of 25.0 is: 5.0
```

The `Math.sqrt()` method can handle both positive and non-positive numbers. If you pass a negative number as an argument to `Math.sqrt()`, it will return `NaN` (Not a Number).

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Printing patterns

Printing patterns in Java involves using loops to display various patterns of characters, numbers, or symbols on the console. Below are some examples of common patterns:

1. Printing a right-angled triangle pattern:

```java
public class RightAngleTrianglePattern {
    public static void main(String[] args) {
        int n = 5; // Number of rows

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

Output:
```
* 
* * 
* * * 
* * * * 
* * * * *
```

2. Printing an inverted right-angled triangle pattern:

```java
public class InvertedRightAngleTrianglePattern {
    public static void main(String[] args) {
        int n = 5; // Number of rows

        for (int i = n; i >= 1; i--) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

Output:
```
* * * * * 
* * * * 
* * * 
* * 
*
```

3. Printing a pyramid pattern:

```java
public class PyramidPattern {
    public static void main(String[] args) {
        int n = 5; // Number of rows
        int space = n - 1;

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= space; j++) {
                System.out.print(" ");
            }

            for (int j = 1; j <= 2 * i - 1; j++) {
                System.out.print("*");
            }

            System.out.println();
            space--;
        }
    }
}
```

Output:
```
    *
   ***
  *****
 *******
*********
```

4. Printing a diamond pattern:

```java
public class DiamondPattern {
    public static void main(String[] args) {
        int n = 5; // Number of rows
        int space = n - 1;

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= space; j++) {
                System.out.print(" ");
            }

            for (int j = 1; j <= 2 * i - 1; j++) {
                System.out.print("*");
            }

            System.out.println();
            space--;
        }

        space = 1;

        for (int i = n - 1; i >= 1; i--) {
            for (int j = 1; j <= space; j++) {
                System.out.print(" ");
            }

            for (int j = 1; j <= 2 * i - 1; j++) {
                System.out.print("*");
            }

            System.out.println();
            space++;
        }
    }
}
```

Output:
```
    *
   ***
  *****
 *******
*********
 *******
  *****
   ***
    *
```

These are just a few examples of patterns that can be printed using loops in Java. You can create various other patterns by modifying the loop conditions and the characters or symbols used for printing.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Leap year

In Java, you can check if a year is a leap year or not using the following logic:

1. If the year is divisible by 4, but not divisible by 100, it is a leap year.
2. If the year is divisible by 400, it is also a leap year.

Here's the Java code to determine if a year is a leap year or not:

```java
public class LeapYearExample {

    public static boolean isLeapYear(int year) {
        // Check if the year is divisible by 4 but not divisible by 100,
        // or if it is divisible by 400.
        return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
    }

    public static void main(String[] args) {
        int year = 2024;

        if (isLeapYear(year)) {
            System.out.println(year + " is a leap year.");
        } else {
            System.out.println(year + " is not a leap year.");
        }
    }
}
```

In this example, we have the `isLeapYear` method, which takes an integer `year` as input and returns a boolean value indicating whether it is a leap year or not, based on the conditions mentioned above.

In the `main` method, we demonstrate the usage of the `isLeapYear` method with the year `2024`. When you run the program, it will display:

```csharp
2024 is a leap year.
```

Leap years occur every four years, except for years that are divisible by 100 but not divisible by 400. For example, the year 2000 is a leap year because it is divisible by 400, but the year 1900 is not a leap year because it is divisible by 100 and not divisible by 400.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Design a Vending Machine

Designing a vending machine is a complex task involving various components and functionalities. Below is a simplified version of a vending machine in Java, focusing on basic operations like selecting items, adding money, and dispensing items:

```java
import java.util.HashMap;
import java.util.Map;

class Item {
    private String name;
    private double price;

    public Item(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }
}

class VendingMachine {
    private Map<String, Item> items;
    private double currentBalance;

    public VendingMachine() {
        items = new HashMap<>();
        currentBalance = 0.0;
    }

    public void addItem(String code, String name, double price) {
        items.put(code, new Item(name, price));
    }

    public void insertCoin(double amount) {
        currentBalance += amount;
    }

    public void displayItems() {
        System.out.println("Available Items:");
        for (String code : items.keySet()) {
            Item item = items.get(code);
            System.out.println(code + " - " + item.getName() + " - $" + item.getPrice());
        }
    }

    public void selectItem(String code) {
        if (items.containsKey(code)) {
            Item selectedItem = items.get(code);
            if (currentBalance >= selectedItem.getPrice()) {
                System.out.println("Dispensing " + selectedItem.getName() + ".");
                double change = currentBalance - selectedItem.getPrice();
                if (change > 0) {
                    System.out.println("Change: $" + change);
                }
                currentBalance = 0.0;
            } else {
                System.out.println("Insufficient balance. Please insert more coins.");
            }
        } else {
            System.out.println("Invalid item code. Please try again.");
        }
    }

    public double getCurrentBalance() {
        return currentBalance;
    }
}

public class Main {
    public static void main(String[] args) {
        VendingMachine vendingMachine = new VendingMachine();

        // Adding items to the vending machine
        vendingMachine.addItem("A1", "Soda", 1.5);
        vendingMachine.addItem("B2", "Chips", 1.0);
        vendingMachine.addItem("C3", "Candy", 0.75);

        // Display available items
        vendingMachine.displayItems();

        // Inserting coins
        vendingMachine.insertCoin(1.0);
        vendingMachine.insertCoin(0.5);

        // Selecting an item
        vendingMachine.selectItem("A1");

        // Check current balance
        System.out.println("Current balance: $" + vendingMachine.getCurrentBalance());
    }
}
```

In this simplified implementation, we have a `VendingMachine` class with methods to add items, insert coins, display available items, select an item, and check the current balance.

The `Item` class represents an item in the vending machine, with a name and a price.

In the `main` method, we create a `VendingMachine` object, add items to it, display available items, insert coins, select an item, and check the current balance.

Please note that this is a basic design, and a real-world vending machine would require more complex functionalities, such as handling change, keeping track of inventory, and handling multiple users simultaneously. Depending on the specific requirements, the design can be extended to support these additional functionalities.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Transpose a matrix

To transpose a matrix in Java, you need to swap the rows and columns of the original matrix. Here's the Java code to transpose a matrix:

```java
public class MatrixTranspose {
    public static int[][] transpose(int[][] matrix) {
        int rows = matrix.length;
        int columns = matrix[0].length;

        int[][] transposedMatrix = new int[columns][rows];

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < columns; j++) {
                transposedMatrix[j][i] = matrix[i][j];
            }
        }

        return transposedMatrix;
    }

    public static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int num : row) {
                System.out.print(num + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        System.out.println("Original Matrix:");
        printMatrix(matrix);

        int[][] transposedMatrix = transpose(matrix);

        System.out.println("Transposed Matrix:");
        printMatrix(transposedMatrix);
    }
}
```

In this code, we have a `transpose` method that takes a 2D array `matrix` as input and returns the transposed matrix. We create a new 2D array `transposedMatrix` with the dimensions swapped (rows become columns, and columns become rows). Then, we copy the elements from the original matrix to the transposed matrix in the correct positions.

The `printMatrix` method is used to display the contents of a 2D array in a matrix format.

In the `main` method, we demonstrate the usage of the `transpose` method with a sample 3x3 matrix. When you run the program, it will display both the original matrix and the transposed matrix.

Output:
```
Original Matrix:
1 2 3 
4 5 6 
7 8 9 
Transposed Matrix:
1 4 7 
2 5 8 
3 6 9 
```

As you can see, the rows of the original matrix become the columns of the transposed matrix, and the columns of the original matrix become the rows of the transposed matrix.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Adding two matrices in Java

To add two matrices in Java, the matrices must have the same dimensions (same number of rows and columns). The addition of two matrices is performed by adding the corresponding elements of both matrices. Here's the Java code to add two matrices:

```java
public class MatrixAddition {
    public static int[][] addMatrices(int[][] matrix1, int[][] matrix2) {
        int rows = matrix1.length;
        int columns = matrix1[0].length;
        int[][] result = new int[rows][columns];

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < columns; j++) {
                result[i][j] = matrix1[i][j] + matrix2[i][j];
            }
        }

        return result;
    }

    public static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int num : row) {
                System.out.print(num + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int[][] matrix1 = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int[][] matrix2 = {
            {9, 8, 7},
            {6, 5, 4},
            {3, 2, 1}
        };

        System.out.println("Matrix 1:");
        printMatrix(matrix1);

        System.out.println("Matrix 2:");
        printMatrix(matrix2);

        int[][] sumMatrix = addMatrices(matrix1, matrix2);

        System.out.println("Sum Matrix:");
        printMatrix(sumMatrix);
    }
}
```

In this code, we have a `addMatrices` method that takes two 2D arrays `matrix1` and `matrix2` as input and returns the sum matrix. We create a new 2D array `result` with the same dimensions as the input matrices. Then, we add the corresponding elements from `matrix1` and `matrix2` and store the result in the `result` matrix.

The `printMatrix` method is used to display the contents of a 2D array in a matrix format.

In the `main` method, we demonstrate the usage of the `addMatrices` method with two sample matrices. When you run the program, it will display both the original matrices and the sum matrix.

Output:
```yaml
Matrix 1:
1 2 3 
4 5 6 
7 8 9 
Matrix 2:
9 8 7 
6 5 4 
3 2 1 
Sum Matrix:
10 10 10 
10 10 10 
10 10 10 
```

As you can see, the elements of the sum matrix are obtained by adding the corresponding elements of `matrix1` and `matrix2`.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Matrix multiplication

Matrix multiplication in Java involves multiplying two matrices to produce a third matrix. The number of columns in the first matrix must be equal to the number of rows in the second matrix for multiplication to be possible.

Here's the Java code to perform matrix multiplication:

```java
public class MatrixMultiplication {
    public static int[][] multiplyMatrices(int[][] matrix1, int[][] matrix2) {
        int rows1 = matrix1.length;
        int columns1 = matrix1[0].length;
        int rows2 = matrix2.length;
        int columns2 = matrix2[0].length;

        if (columns1 != rows2) {
            throw new IllegalArgumentException("Invalid matrix dimensions for multiplication.");
        }

        int[][] result = new int[rows1][columns2];

        for (int i = 0; i < rows1; i++) {
            for (int j = 0; j < columns2; j++) {
                for (int k = 0; k < columns1; k++) {
                    result[i][j] += matrix1[i][k] * matrix2[k][j];
                }
            }
        }

        return result;
    }

    public static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int num : row) {
                System.out.print(num + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int[][] matrix1 = {
            {1, 2},
            {3, 4}
        };

        int[][] matrix2 = {
            {5, 6},
            {7, 8}
        };

        System.out.println("Matrix 1:");
        printMatrix(matrix1);

        System.out.println("Matrix 2:");
        printMatrix(matrix2);

        int[][] productMatrix = multiplyMatrices(matrix1, matrix2);

        System.out.println("Product Matrix:");
        printMatrix(productMatrix);
    }
}
```

In this code, we have a `multiplyMatrices` method that takes two 2D arrays `matrix1` and `matrix2` as input and returns the product matrix. Before multiplication, we check whether the matrices have valid dimensions for multiplication.

The product matrix has dimensions `rows1 x columns2`, where `rows1` is the number of rows in the first matrix and `columns2` is the number of columns in the second matrix. We use three nested loops to perform the matrix multiplication.

The `printMatrix` method is used to display the contents of a 2D array in a matrix format.

In the `main` method, we demonstrate the usage of the `multiplyMatrices` method with two sample matrices. When you run the program, it will display both the original matrices and the product matrix.

Output:
```yaml
Matrix 1:
1 2 
3 4 
Matrix 2:
5 6 
7 8 
Product Matrix:
19 22 
43 50 
```

As you can see, the product matrix is obtained by multiplying the elements of `matrix1` and `matrix2` following the matrix multiplication rules.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a Java program to print Floyd’s Triangle?

Floyd's Triangle is a right-angled triangular pattern of numbers named after the mathematician Robert Floyd. Each row in Floyd's Triangle starts with the number one and increments by one for each subsequent number. Here's a Java program to print Floyd's Triangle:

```java
public class FloydsTriangle {
    public static void main(String[] args) {
        int rows = 5; // Number of rows in the triangle
        int number = 1; // The initial number to be printed

        for (int i = 1; i <= rows; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print(number + " ");
                number++;
            }
            System.out.println();
        }
    }
}
```

In this program, we have a loop that iterates over each row of the triangle. For each row, another loop is used to print the numbers in that row, starting from the initial number and incrementing it by one for each subsequent number. The outer loop controls the number of rows to be printed.

When you run the program, it will display the following Floyd's Triangle:

```
1 
2 3 
4 5 6 
7 8 9 10 
11 12 13 14 15 
```

As you can see, each row starts with the number one and increments by one for each subsequent number, forming Floyd's Triangle. The number of rows in the triangle can be adjusted by changing the value of the `rows` variable in the program.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Spiral Matrix Program.

A spiral matrix is a square matrix in which the elements are arranged in a spiral pattern, starting from the top-left corner and moving towards the center in a clockwise direction. Here's a Java program to print a spiral matrix:

```java
public class SpiralMatrix {
    public static void printSpiralMatrix(int n) {
        int[][] matrix = new int[n][n];

        int num = 1;
        int left = 0, right = n - 1, top = 0, bottom = n - 1;

        while (num <= n * n) {
            // Traverse from left to right
            for (int i = left; i <= right; i++) {
                matrix[top][i] = num;
                num++;
            }
            top++;

            // Traverse from top to bottom
            for (int i = top; i <= bottom; i++) {
                matrix[i][right] = num;
                num++;
            }
            right--;

            // Traverse from right to left
            for (int i = right; i >= left; i--) {
                matrix[bottom][i] = num;
                num++;
            }
            bottom--;

            // Traverse from bottom to top
            for (int i = bottom; i >= top; i--) {
                matrix[i][left] = num;
                num++;
            }
            left++;
        }

        // Print the spiral matrix
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print(matrix[i][j] + "\t");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int n = 5; // Size of the square matrix
        printSpiralMatrix(n);
    }
}
```

In this program, we have a `printSpiralMatrix` method that takes an integer `n` as input, representing the size of the square matrix. The method creates a 2D array `matrix` of size `n x n` to store the elements of the spiral matrix.

We use four variables `left`, `right`, `top`, and `bottom` to keep track of the boundaries while traversing the matrix in a spiral pattern. The `num` variable is used to fill the elements of the matrix in a sequential manner.

The four loops inside the `while` loop traverse the matrix in a clockwise direction, starting from the top-left corner. We fill the elements from left to right, then from top to bottom, then from right to left, and finally from bottom to top.

After filling the matrix, the program prints the spiral matrix to the console.

When you run the program with `n = 5`, it will display the following spiral matrix:

```
1	2	3	4	5	
16	17	18	19	6	
15	24	25	20	7	
14	23	22	21	8	
13	12	11	10	9	
```

The elements are arranged in a spiral pattern starting from 1 and moving towards the center of the matrix in a clockwise direction.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Anagram program in Java

An Anagram is a word or phrase formed by rearranging the letters of another word or phrase, typically using all the original letters exactly once. Here's a Java program to check if two strings are anagrams:

```java
import java.util.Arrays;

public class AnagramChecker {
    public static boolean areAnagrams(String str1, String str2) {
        // Remove spaces and convert both strings to lowercase
        String s1 = str1.replaceAll("\\s", "").toLowerCase();
        String s2 = str2.replaceAll("\\s", "").toLowerCase();

        // Check if the lengths of both strings are equal
        if (s1.length() != s2.length()) {
            return false;
        }

        // Convert strings to char arrays and sort them
        char[] charArray1 = s1.toCharArray();
        char[] charArray2 = s2.toCharArray();
        Arrays.sort(charArray1);
        Arrays.sort(charArray2);

        // Check if the sorted char arrays are equal
        return Arrays.equals(charArray1, charArray2);
    }

    public static void main(String[] args) {
        String str1 = "listen";
        String str2 = "silent";

        if (areAnagrams(str1, str2)) {
            System.out.println(str1 + " and " + str2 + " are anagrams.");
        } else {
            System.out.println(str1 + " and " + str2 + " are not anagrams.");
        }
    }
}
```

In this program, we have a method `areAnagrams` that takes two strings `str1` and `str2` as input and returns a boolean value indicating whether they are anagrams or not.

Before comparing the strings, we remove any spaces and convert both strings to lowercase using the `replaceAll` and `toLowerCase` methods. Then, we check if the lengths of both strings are equal. If they are not, they cannot be anagrams, so we return `false`.

Next, we convert both strings to character arrays and sort them using `Arrays.sort()`. Finally, we compare the sorted character arrays using `Arrays.equals()`. If the sorted arrays are equal, it means the two strings are anagrams, and we return `true`; otherwise, we return `false`.

In the `main` method, we demonstrate the usage of the `areAnagrams` method by checking if "listen" and "silent" are anagrams. When you run the program, it will output:

```arduino
listen and silent are anagrams.
```

Both strings "listen" and "silent" are anagrams of each other because they can be formed by rearranging the same letters.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to print Fibonacci series.

The Fibonacci series is a sequence of numbers in which each number is the sum of the two preceding ones, starting from 0 and 1. Here's a Java program to print the Fibonacci series up to a given number of terms:

```java
import java.util.Scanner;

public class FibonacciSeries {
    public static void printFibonacci(int n) {
        int firstNum = 0, secondNum = 1;

        System.out.print("Fibonacci Series: ");

        for (int i = 0; i < n; i++) {
            System.out.print(firstNum + " ");

            int nextNum = firstNum + secondNum;
            firstNum = secondNum;
            secondNum = nextNum;
        }

        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of terms in the Fibonacci series: ");
        int n = scanner.nextInt();

        printFibonacci(n);

        scanner.close();
    }
}
```

In this program, we have a `printFibonacci` method that takes an integer `n` as input and prints the Fibonacci series up to `n` terms.

We start by initializing the first two numbers of the Fibonacci series, `firstNum` and `secondNum`, to 0 and 1, respectively. Then, we use a loop to generate and print the next number in the series for `n` times. In each iteration of the loop, we print the current number (`firstNum`) and calculate the next number as the sum of the two preceding numbers (`firstNum` and `secondNum`). We update `firstNum` and `secondNum` accordingly for the next iteration.

In the `main` method, we read the number of terms (`n`) from the user and call the `printFibonacci` method to print the Fibonacci series up to `n` terms.

When you run the program and enter `10` as the number of terms, it will output:

```mathematica
Enter the number of terms in the Fibonacci series: 10
Fibonacci Series: 0 1 1 2 3 5 8 13 21 34
```

The program prints the first 10 terms of the Fibonacci series. You can change the value of `n` to print a different number of terms.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to you calculate the difference between two dates in Java?

In Java, you can calculate the difference between two dates using the `java.time` package, which was introduced in Java 8 to handle date and time operations. The key classes for date manipulation in this package are `LocalDate` and `Period`. Here's how you can calculate the difference between two dates in Java:

```java
import java.time.LocalDate;
import java.time.Period;

public class DateDifference {
    public static void main(String[] args) {
        // Example dates
        LocalDate date1 = LocalDate.of(2022, 5, 10);
        LocalDate date2 = LocalDate.of(2023, 9, 15);

        // Calculate the difference between the two dates
        Period period = Period.between(date1, date2);

        // Display the difference
        int years = period.getYears();
        int months = period.getMonths();
        int days = period.getDays();

        System.out.println("Difference between the two dates:");
        System.out.println("Years: " + years);
        System.out.println("Months: " + months);
        System.out.println("Days: " + days);
    }
}
```

In this program, we have two example dates, `date1` and `date2`, represented as `LocalDate` objects. The `LocalDate` class is used to represent a date without a time component.

To calculate the difference between the two dates, we use the `Period.between` method, which returns a `Period` object representing the difference. The `Period` class represents a period of time, such as the difference between two dates in years, months, and days.

We then extract the years, months, and days components from the `Period` object using the `getYears`, `getMonths`, and `getDays` methods, respectively.

Finally, we display the difference between the two dates in years, months, and days using `System.out.println`.

When you run the program with the provided example dates, it will output:

```yaml
Difference between the two dates:
Years: 1
Months: 4
Days: 5
```

This means that there is a difference of 1 year, 4 months, and 5 days between `date1` and `date2`. You can use this approach to calculate the difference between any two valid dates in Java.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Java Program to find gcd and lcm of two numbers

To find the Greatest Common Divisor (GCD) and Least Common Multiple (LCM) of two numbers in Java, you can use the Euclidean algorithm to find the GCD and then calculate the LCM using the formula:

LCM = (num1 * num2) / GCD(num1, num2)

Here's the Java program to find the GCD and LCM of two numbers:

```java
import java.util.Scanner;

public class GcdLcmCalculator {
    public static int findGCD(int num1, int num2) {
        // Use Euclidean algorithm to find GCD
        while (num2 != 0) {
            int temp = num2;
            num2 = num1 % num2;
            num1 = temp;
        }
        return num1;
    }

    public static int findLCM(int num1, int num2) {
        // Calculate LCM using the formula LCM = (num1 * num2) / GCD(num1, num2)
        int gcd = findGCD(num1, num2);
        return (num1 * num2) / gcd;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the first number: ");
        int num1 = scanner.nextInt();

        System.out.print("Enter the second number: ");
        int num2 = scanner.nextInt();

        int gcd = findGCD(num1, num2);
        int lcm = findLCM(num1, num2);

        System.out.println("GCD of " + num1 + " and " + num2 + " is: " + gcd);
        System.out.println("LCM of " + num1 + " and " + num2 + " is: " + lcm);

        scanner.close();
    }
}
```

In this program, we have two methods, `findGCD` and `findLCM`, to calculate the GCD and LCM, respectively. The `findGCD` method uses the Euclidean algorithm to find the GCD of two numbers. The `findLCM` method then uses the GCD to calculate the LCM using the formula mentioned above.

In the `main` method, we read two numbers (`num1` and `num2`) from the user and call the `findGCD` and `findLCM` methods to calculate the GCD and LCM, respectively. Finally, we display the GCD and LCM to the console.

When you run the program and enter two numbers, for example, `24` and `36`, it will output:

```mathematica
Enter the first number: 24
Enter the second number: 36
GCD of 24 and 36 is: 12
LCM of 24 and 36 is: 72
```

This means that the GCD of 24 and 36 is 12, and the LCM is 72.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. Write a program to find the sum of the first 1000 prime numbers?

To find the sum of the first 1000 prime numbers in Java, you can create a method to check if a number is prime, and then use a loop to find the first 1000 prime numbers and calculate their sum. Here's a Java program to achieve this:

```java
public class PrimeNumberSum {
    public static boolean isPrime(int num) {
        if (num <= 1) {
            return false;
        }
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        int count = 0; // Number of prime numbers found so far
        int num = 2; // Start checking from 2, the first prime number
        long sum = 0; // Variable to store the sum of prime numbers

        while (count < 1000) {
            if (isPrime(num)) {
                sum += num;
                count++;
            }
            num++;
        }

        System.out.println("Sum of the first 1000 prime numbers: " + sum);
    }
}
```

In this program, we have a method `isPrime` that checks whether a given number is prime or not. It returns `true` if the number is prime and `false` otherwise.

In the `main` method, we initialize `count` to 0, `num` to 2 (the first prime number), and `sum` to 0. We use a `while` loop to find the first 1000 prime numbers. Inside the loop, we check if the current number (`num`) is prime using the `isPrime` method. If it is prime, we add it to the `sum` and increment the `count`. We continue this process until we find 1000 prime numbers.

Finally, we print the sum of the first 1000 prime numbers to the console.

When you run the program, it will display the sum of the first 1000 prime numbers:

```mathematica
Sum of the first 1000 prime numbers: 3682913
```

The sum of the first 1000 prime numbers is 3682913.

<div align="right">
    <b><a href="#related-topics">↥ back to top</a></b>
</div>

## Q. How to perform matrix operations in Java?

In Java, you can perform various matrix operations using multi-dimensional arrays and loops. Here are some common matrix operations, along with their Java implementations:

1. Matrix Addition:
To add two matrices, the matrices must have the same dimensions (same number of rows and columns).

```java
public class MatrixOperations {
    public static int[][] addMatrices(int[][] matrix1, int[][] matrix2) {
        int rows = matrix1.length;
        int columns = matrix1[0].length;
        int[][] result = new int[rows][columns];

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < columns; j++) {
                result[i][j] = matrix1[i][j] + matrix2[i][j];
            }
        }
        return result;
    }

    public static void main(String[] args) {
        int[][] matrix1 = { {1, 2}, {3, 4} };
        int[][] matrix2 = { {5, 6}, {7, 8} };

        int[][] sumMatrix = addMatrices(matrix1, matrix2);

        // Print the sumMatrix here...
    }
}
```

2. Matrix Subtraction:
Similar to matrix addition, the matrices must have the same dimensions to perform matrix subtraction.

3. Matrix Multiplication:
To multiply two matrices, the number of columns in the first matrix must be equal to the number of rows in the second matrix.

```java
public class MatrixOperations {
    public static int[][] multiplyMatrices(int[][] matrix1, int[][] matrix2) {
        int rows1 = matrix1.length;
        int columns1 = matrix1[0].length;
        int rows2 = matrix2.length;
        int columns2 = matrix2[0].length;

        if (columns1 != rows2) {
            throw new IllegalArgumentException("Invalid matrix dimensions for multiplication.");
        }

        int[][] result = new int[rows1][columns2];

        for (int i = 0; i < rows1; i++) {
            for (int j = 0; j < columns2; j++) {
                for (int k = 0; k < columns1; k++) {
                    result[i][j] += matrix1[i][k] * matrix2[k][j];
                }
            }
        }

        return result;
    }

    public static void main(String[] args) {
        int[][] matrix1 = { {1, 2}, {3, 4} };
        int[][] matrix2 = { {5, 6}, {7, 8} };

        int[][] productMatrix = multiplyMatrices(matrix1, matrix2);

        // Print the productMatrix here...
    }
}
```

4. Scalar Multiplication:
To multiply a matrix by a scalar value, you simply multiply each element of the matrix by the scalar.

5. Transpose of a Matrix:
The transpose of a matrix is obtained by exchanging rows and columns. The rows of the original matrix become the columns of the transposed matrix.

```java
public class MatrixOperations {
    public static int[][] transposeMatrix(int[][] matrix) {
        int rows = matrix.length;
        int columns = matrix[0].length;
        int[][] result = new int[columns][rows];

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < columns; j++) {
                result[j][i] = matrix[i][j];
            }
        }
        return result;
    }

    public static void main(String[] args) {
        int[][] matrix = { {1, 2, 3}, {4, 5, 6} };

        int[][] transposedMatrix = transposeMatrix(matrix);

        // Print the transposedMatrix here...
    }
}
```

These are some of the common matrix operations in Java. Depending on your requirements, you can implement other matrix operations as well. Note that in real-world scenarios, you may want to use libraries like Apache Commons Math or JAMA for more efficient and comprehensive matrix operations.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
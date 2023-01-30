## Part 1
```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler {
    String str="";

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                str+=parameters[1]+"\n";
            }
        }
        return str;
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

After running the code, two lines of strings were entered into the url: "line 1 of strings" and "line 2 of strings". This was able to see the code work with chars and ints. In the end, they were all converted to strings.

![sc1](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report2/addmessagess.PNG?raw=true)
![sc2](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report2/addmessagess2.PNG?raw=true)

In both screenshots, the method handleRequest was called. The argument for handleRequest is an URI, url, which is the url to the web server. Depending on the path of the url, certain actions are done. If the url path is equal to "/add-message" then a string will be added to the page. The string str contains the entire string that is returned and outputed on the page. The array parameters holds the query in index 1, which contains the message to be added to str. Whenever this specific request is made, the string in the query followed by a newline is added to str. In the first screenshot, the path is "/add-message" and the query was "line 1 of strings", which was added to the page. Similarly "line 2 of strings" in screenshot 2 was added as well.

## Part 2
ArrayExample
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
}
```
Failure-Inducing Input
```
@Test
  public void testReversedLonger() {
    int[] input1 = {1,2,3,4,5};
    assertArrayEquals(new int[]{5,4,3,2,1}, ArrayExamples.reversed(input1));
}
```
This test produced the following output:
```
There was 1 failure:
1) testReversedLonger(ArrayTests)
arrays first differed at element [0]; expected:<5> but was:<0>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversedLonger(ArrayTests.java:25)
 ```
Rather than reversing the array, the output replaced everything with 0. This symptom was caused due to changing the elements in arr with those from newArray. However, since newArray was just created, all values are 0 by default, overwriting all values of arr to 0. Furthermore, arr is returned as well, so the output array is all 0. This bug can be resolved by switching arr and newArray in the for loop and returning newArray. This will take the needed values from the input array in reverse order and then put them into the new array. The newArray now has the properly reversed values, and since it is returned, the output array will be correct.

Fixed Code:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
}
```
Here is a test that passed despite the bug:
```
@Test
  public void testReversed() {
    int[] input1 = {0};
    assertArrayEquals(new int[]{0}, ArrayExamples.reversed(input1));
}
```
Since the original array was only one 0, the output array should also just be one 0, which is in line with what the bug was doing.

## Part 3
In week 2, I learned about setting up a web server. We can run it either locally on our computer or remotely when remotely connected to another device. To do so in Java, we make use of the URI. We can also make use of the URLHandler to make our program do something when a certain path or query is entered in the url.

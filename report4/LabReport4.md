## Step 4
`<up><enter>`

This was used to access the command from the bash history, which was saved in a previous run. Five `<up>`s were used since there were four other commands involved from the start of the previous run. Only one `<up>` was necessary since all the other commands were run from remotely. The resulting command was to ssh into the remote machine.

`ssh cs15lwi23aqa@ieng6.ucsd.edu`

## Step 5-9
`<up><up><up><up><enter>`

Similarly, this also got a command from the bash history, from a previous run. This one command made use of `;`, which separated commands in order to run multiple in one line. Every command was run from one line to be as efficient. The command was four up in history as three other commands were used to reset for the next run: `cd ..`, `rm -r -f lab7`, `exit`.

The commands used in the line
`git clone git@github.com:jliu0140/lab7.git` - This command cloned the repository from github.

`javac -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" *.java` - This command compiled the java files.

`java -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples` - This ran the tester.

`echo -e '...' > ListExamples.java` - This command took the output of echo, which was the ListExamples.java file with the corrections, and redirected it into ListExamples.java. This was how ListExamples.java was directly edited from terminal without using an editor. The `-e` option allowed the use of `\n` to create new lines.

The java files were compiled and the tester was ran again here using the same commands above.

`git add ListExamples.java` - This adds the changed file to the commit.

`git commit -m "updated" - This commited the changes to the repository with the message of "updated".

`git push` - This pushed the changes to github.
```
git clone git@github.com:jliu0140/lab7.git; cd lab7; javac -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" *.java; java -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples; echo -e 'import java.util.ArrayList;\nimport java.util.List;\n\ninterface StringChecker { boolean checkString(String s); }\n\nclass ListExamples {\n      // Returns a new list that has all the elements of the input list for which\n    // the StringChecker returns true, and not the elements that return false, in\n      // the same order they appeared in the input list;\n      static List<String> filter(List<String> list, StringChecker sc) {\n        List<String> result = new ArrayList<>();\n        for(String s: list) {\n          if(sc.checkString(s)) {\n            result.add(0, s);\n          }\n        }\n        return result;\n      }\n      // Takes two sorted list of strings (so "a" appears before "b" and so on),\n      // and return a new list that has all the strings in both list in sorted order.\n      static List<String> merge(List<String> list1, List<String> list2) {\n        List<String> result = new ArrayList<>();\n        int index1 = 0, index2 = 0;\n        while(index1 < list1.size() && index2 < list2.size()) {\n          if(list1.get(index1).compareTo(list2.get(index2)) < 0) {\n            result.add(list1.get(index1));\n            index1 += 1;\n          }\n          else {\n            result.add(list2.get(index2));\n            index2 += 1;\n          }\n        }\n        while(index1 < list1.size()) {\n          result.add(list1.get(index1));\n          index1 += 1;\n        }\n        while(index2 < list2.size()) {\n          result.add(list2.get(index2));\n          index2 += 1;\n        }\n        return result;\n      }\n    }' > ListExamples.java; javac -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" *.java; java -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples; git add ListExamples.java; git commit -m "updated"; git push
```
With some spacing
```
git clone git@github.com:jliu0140/lab7.git; cd lab7; javac -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" *.java; java -cp ".:lib/junit-
4.13.2.jar:lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples; echo -e 'import java.util.ArrayList;\nimport java.util.List;\n\ninterface 
StringChecker { boolean checkString(String s); }\n\nclass ListExamples {\n      // Returns a new list that has all the elements of the input list for which\n    // the 
StringChecker returns true, and not the elements that return false, in\n      // the same order they appeared in the input list;\n      static List<String> 
filter(List<String> list, StringChecker sc) {\n        List<String> result = new ArrayList<>();\n        for(String s: list) {\n          if(sc.checkString(s)) {\n     
       result.add(0, s);\n          }\n        }\n        return result;\n      }\n      // Takes two sorted list of strings (so "a" appears before "b" and so on),\n      
// and return a new list that has all the strings in both list in sorted order.\n      static List<String> merge(List<String> list1, List<String> list2) {\n        
List<String> result = new ArrayList<>();\n        int index1 = 0, index2 = 0;\n        while(index1 < list1.size() && index2 < list2.size()) {\n          
if(list1.get(index1).compareTo(list2.get(index2)) < 0) {\n            result.add(list1.get(index1));\n            index1 += 1;\n          }\n          else {\n          
   result.add(list2.get(index2));\n            index2 += 1;\n          }\n        }\n        while(index1 < list1.size()) {\n          result.add(list1.get(index1));\n          
         index1 += 1;\n        }\n        while(index2 < list2.size()) {\n          result.add(list2.get(index2));\n          index2 += 1;\n        }\n        return 
result;\n      }\n    }' > ListExamples.java; javac -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" *.java; java -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-
1.3.jar" org.junit.runner.JUnitCore TestListExamples; git add ListExamples.java; git commit -m "updated"; git push
```

## Grading Script
```
CPATH='.;../lib/hamcrest-core-1.3.jar;../lib/junit-4.13.2.jar'

rm -rf student-submission
git clone $1 student-submission
echo 'Finished cloning'
cd student-submission

if [[ -e ListExamples.java ]]
then
    echo 'File ListExamples.java found'
else
    echo 'Missing file ListExamples.java'
    exit 1
fi

cp ../TestListExamples.java ./

javac -cp $CPATH *.java
if [[ $? -ne 0 ]]
then
    echo 'Compiler failed'
    exit 1
else
    echo 'Compiler passed'
fi

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > results.txt

PASSED=`grep -c FAILURES! results.txt`
if [[ $PASSED -eq 0 ]]
then
    echo 'All Tests Passed'
else
    grep "Tests run:" results.txt
    grep "test" results.txt
fi
```
## Details
When writing the script, I broke it down into four parts that I wanted to do and wrote them one at a time. The four parts include setting up for the tests, checking for the correct file, compiling the file (and checking it compiled correctly), and running the tests.
```
CPATH='.;../lib/hamcrest-core-1.3.jar;../lib/junit-4.13.2.jar'

rm -rf student-submission
git clone $1 student-submission
echo 'Finished cloning'
cd student-submission
```
This section of the script sets up the environment for the tester.

The variable stored at the top `CPATH` contains the classpath for junit testing. Having the variable makes it easier to write out when compiling and running the tester.

`rm -rf student-submission` removes the student-submission directory, cleaning out previous runs of the grading script. This sets up for cloning the student repository into a student-submission directory.

`git clone $1 student-submission` clones the student repository into a directory named `student-submission`. With this cloned, we can test the student submission.

`echo 'Finished cloning'` will print a message stating the the cloning of the repository has finished.

`cd student-submission` changes the working directory to `student-submission` to make it easier to run commands.

```
if [[ -e ListExamples.java ]]
then
    echo 'File ListExamples.java found'
else
    echo 'Missing file ListExamples.java'
    exit 1
fi

cp ../TestListExamples.java ./
```
This section of the script checks for the correct submitted file and prepares to run the tester.

`if [[ -e ListExamples.java ]]` checks to see if `ListExamples.java` exists in the directory. If it does, then `echo 'File ListExamples.java found'` will be run to notify that the file exists. Otherwise `echo 'Missing file ListExamples.java'` will be run to notify the file is not there. If the file is not there, then `exit 1` will be run to stop the script. If the file being graded is not there, there is no reason to continue the script. `exit 1` was used to notify that there was some error in running the script, which was the nonexistence of `ListExamples.java`.

`cp ../TestListExamples.java ./` copies the tester file into the current working directory so it can be run to check the implementation of the student submission.

```
javac -cp $CPATH *.java
if [[ $? -ne 0 ]]
then
    echo 'Compiler failed'
    exit 1
else
    echo 'Compiler passed'
fi
```
This section checks if the student submission compiles properly.

`javac -cp $CPATH *.java` compiles the student submission and the tester using the `-cp` option and the classpath for junit. This is required in order to compile files using junit, such as the tester file.

`if [[ $? -ne 0 ]]` checks the exit code of the previous command, which compiled the java files. If the exit command is 0, then it compiled with no issue. If not, then there was some error in compiling. `$?` stores the previous exit code and the `-ne` option checks for not equals. If the exit code is not 0, then the if statement will run.

If the if statement is true and something was wrong with the compiler, then `echo 'Compiler failed'` will be run to notify the error in compiling and `exit 1` is run to terminate the script. The 1 was used to signal there was some error in running the script, which was the files not compiling.

Otherwise, `echo 'Compiler passed'` will run if the compiler worked, notifying the success in compilation.

```
java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > results.txt

PASSED=`grep -c FAILURES! results.txt`
if [[ $PASSED -eq 0 ]]
then
    echo 'All Tests Passed'
else
    grep "Tests run:" results.txt
    grep "test" results.txt
fi
```
This section will run the tester and print the results.

`java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > results.txt` will run the tester file using `-cp` and `CPATH` similarly to `javac` and redirect the output into `results.txt`. This way, we can pick which outputs we want to make it cleaner.

``PASSED=grep -c FAILURES! results.txt`` will store if all tests were passed. The `-c` option for `grep` will count how many times the given line occurs. In this case, if all tests are passed, then "FAILURES" will not be outputted. However, if there are some failures, then this line will be outputted. Therefore, if `PASSED` is 0, then all tests were passed.

`if [[ $PASSED -eq 0 ]]` checks if all tests were passed. `-eq` checks for equality in numbers. As explained earlier, if `PASSED` is 0, then all tests were passed. `echo 'All Tests Passed'` is run afterwards to notify the student's success.

If there were failures, then `grep "Tests run:" results.txt` will be run to print how many tests and failures there were. This will print out the part of the output that says "Tests run: x, Failures: y". Afterwards, `grep "test" results.txt` is run to print out each of the individual tests that failed inside `results.txt`. The output is done this way rather than printing all of it in order to keep it clean. This removes the unncessary information such as the time it took to run and the tests when they were running.
## Results
Submission with incorrect implementation (doesn't pass all tests):

![lab3](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report5/lab3.PNG?raw=true)

Submission with correct implementation (passes all tests):

![lab3-corrected](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report5/lab3%20corrected.PNG?raw=true)

Submission with syntax error (compiler error):

![compiler-error](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report5/compiler%20error.PNG?raw=true)

Submission with wrong method signature (stops at compilation):

![signature](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report5/wrong%20signature.PNG?raw=true)

Submission with wrong file name (file not found):

![wrong-name](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report5/wrong%20name.PNG?raw=true)

Submission with file nested in another directory (unable to access file):

![nested](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report5/nested%20file.PNG?raw=true)

Submission with more subtle bugs in implementation (doesn't pass all tests):

![subtle](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report5/subtle.PNG?raw=true)

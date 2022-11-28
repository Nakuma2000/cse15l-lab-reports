>[Return to homepage](index.md)
# Lab Report 5
### Hello!
This page will serve as a report for Week 7 of cse15L.

## Part 1 - Grading Script
For this lab, I will be reporting on my grading script `grade.sh` created to grade student submissions of test list examples. The assumed spec is to submit:
* Repository with file called `ListExamples.java`
* In that file, a class called `ListExamples`
* In that class, two methods:
    * `static List<String> filter(List<String> s, StringChecker sc)`
    * `static List<String> merge(List<String> list1, List<String> list2)`
* the methods should have the implementations suggested in lab 3

The grading script will let the user know if the test has passed or failed, with feedback messages during testing to help identify the problem. Here is the code below:

~~~
CP=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

rm -rf student-submission

git clone $1 student-submission
echo "github repository successfully cloned"

cd student-submission
if [[ ! -f "ListExamples.java"]]
then
    echo "file name does not match"
    exit 1
fi
echo "file name matches"

cp TestListExamples.java student-submission/


javac -cp $CP *.java 2> output-error.txt
echo "file compiled successfully"

if [[ -s outpur-error.txt]]
then
    echo "compiled successfully"
else
    echo "program did not compile"
    exit 1
fi

java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
echo $?
~~~

## Part 2 - Running on student submissions
Below are screenshots of the grade.sh script running on student submissions and their reported grade as loaded in the browser.

## Part 3 - Trade of `grade.sh`

### That's it for this lab report, I hope this is helpful. 

### - Nathan

>[Return to homepage](index.md)
>[Return to homepage](index.md)
# Lab 3 Report
### Hello!
This page will serve as a report for Week 5 of cse15L.

## Part 1 - `grep` Command-Line Options
In this report we will be exploring three different command-line options for the `grep` command: `-A/B/C`, `-n`, `-w/c`. Three examples of each of these options and their inputs will be displayed and explained. Each example is used on files and directories from `./technical`.

## Part 2 - `grep -A/B/C n`
I am grouping three options for the first set of examples as they are very similar. \
 `-A n` will print the searched line and `n` lines *after* the result. \
 `-B n` will print the searched line and `n` lines *before* the result. \
 `-C n` will print the searched line and `n` lines before *and* after the result. 
 Below are three examples:

`grep -A 2 "Introduction" technical/biomed/1468-6708-3-1.txt`
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:218$ grep -A 7 "Introduction" technical/biomed/1468-6708-3-1.txt
        Introduction
        Older adults are frequently counseled to lose weight,
        even though there is little evidence that overweight is
        associated with increased mortality in those over age 65.
        Six large controlled population-based studies of
        non-smoking older adults have investigated the association
        between body mass index (BMI) and mortality, controlling
        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
~~~
In this example, `grep` searches for the String "Introduction", then also outputs the 7 lines succeeding that line. The option is useful in this example because we search for a header as an easy way to locate a section of information, and then the option allows us to also output the relevant information.

`grep -B 2 "data not shown" technical/biomed/1468-6708-3-1.txt`
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:217$ grep -B 2 "data not shown" technical/biomed/1468-6708-3-1.txt
        unintended weight loss, YOL, YHL, years of unhealthy life,
        and years lost to death. Whites in the sample had higher
        income and education (data not shown). After adjusting for
~~~
In this example, `grep` searches for the line the string "data not shown" is located in, and also outputs the two lines proceeding it. It is useful in this example to output the entire sentence the string is found in, instead of just the line.

`grep -C 2 "large controlled" technical/biomed/*.txt`
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:213$ grep -C 2 "large controlled" technical/biomed/*.txt
technical/biomed/1468-6708-3-1.txt-        even though there is little evidence that overweight is
technical/biomed/1468-6708-3-1.txt-        associated with increased mortality in those over age 65.
technical/biomed/1468-6708-3-1.txt:        Six large controlled population-based studies of
technical/biomed/1468-6708-3-1.txt-        non-smoking older adults have investigated the association
technical/biomed/1468-6708-3-1.txt-        between body mass index (BMI) and mortality, controlling
~~~
After finding the line the text string 'large controlled' is located in, `grep` prints out the two lines proceeding and the two lines succeeding that line. This option can be useful if context surrounding the string is required, or if several lines of output are required in a file storing a sequential list seperated by new lines.

## Part 3 - `grep -n`

The `-n` option for grep will display the matched lines along with their line numbers.

`grep -n "NEADS: On its way towards Washington?" */*/chapter-1.txt`
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:222$ grep -n "NEADS: On its way towards Washington?" */*/chapter-1.txt
416:    NEADS: On its way towards Washington?
~~~
In this example, the `-n` option finds the line the given string appears in, and displays the line number along with it (line 416). This is useful for finding which line a specific phrase appears on and quickly locating it, especially when it is deep into a long document.

`grep -n "Jihad" */*/chapter-13.5.txt`
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:223$ grep -n "Jihad" */*/chapter-13.5.txt
38:            7. Saeed Abdullah Saeed ("Jihad") al Ghamdi. He arranged to travel to Afghanistan in
531:                Jihad leader Ayman al Zawahiri learned of the operation, and only after his group
778:                "Strategy for Eliminating the Threat from the Jihadists Networks of al Qida: Status
2853:                option for reviving armed struggle in the new millennium." Gilles Kepel, Jihad: The
2905:            18. Neil MacFarquhar, "Saudis Support a Jihad in Iraq, Not Back Home," New York
~~~
Option `-n` behaves the same way in this example, but outputs several lines and their line numbers as the given string appears several times. This is useful when needing to search for every mention of a specific phrase in a given file.

`grep -n "medical service" */*/*.txt`
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:225$ grep -n "medical service" */*/*.txt
technical/911report/chapter-3.txt:1330:                medical services, air traffic control, financial services, telephone systems, and
technical/911report/chapter-9.txt:10:                medical service, and building safety professionals.
technical/911report/chapter-9.txt:514:            Emergency medical services (EMS) personnel were directed to one of four triage areas
technical/biomed/1471-2334-3-11.txt:177:        less likely to receive medical services particularly
technical/biomed/1471-2334-3-11.txt:195:        medical services.
technical/biomed/1471-2377-3-4.txt:375:            emergency medical service or in the emergency
technical/biomed/1471-2407-2-31.txt:63:          medical services at the Roswell Park Cancer Institute
technical/biomed/1471-2407-2-31.txt:71:          individuals, who received medical services at RPCI for
technical/biomed/1471-2407-3-14.txt:350:        to use medical services [ 27 28 ] , with one study finding
technical/biomed/1471-2458-2-18.txt:71:        to 85, who received medical services at RPCI for
technical/biomed/1472-6963-1-8.txt:327:          cost of medical services received in the 3-month period
technical/biomed/1472-6963-2-10.txt:62:          medical services and quality of hotel services and
technical/plos/pmed.0020118.txt:18:        all the needs of medical services today. In the United Kingdom, two striking observations
technical/plos/pmed.0020246.txt:388:            (d) The creation of conditions which would assure to all medical service and
~~~
In this example, the patter `*/*/*.txt` is passed to `grep` to search through multiple files. the `-n` option is useful in this case by providing more specified information that would make a search for the given string easier; `grep -n` displays the line numbers the string appears in for every file.

## Part 4 - `grep -w/c`

The `-w` option for `grep` will match the whole word; appearances of the text string within another word are omitted.

`grep -w  "with" */*/preface.txt` \
For this first example, we will first show the command run wiithout the `-w` option.
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:230$ grep "with" */*/preface.txt
                partisan division-have come together to present this report without dissent.
            We have come together with a unity of purpose because our nation demands it.
                can with the American people. To that end, we held 19 days of hearings and took
            We learned that the institutions charged with protecting our borders, civil aviation,
                fault lines within our government-between foreign and domestic intelligence, and
                between and within agencies. We learned of the pervasive problems of managing and
                officials, past and present, who were generous with their time and provided us with
                fine work helped us get started. We thank the City of New York for assistance with
                whose persistence and dedication helped create the Commission. They have been with
                preparing to respond if it becomes necessary. We emerge from this investigation with
                enormous sympathy for the victims and their loved ones, and with enhanced respect
            We also approach the task of recommendations with humility. We have made a limited
                this process with strong opinions about what would work. All of us have had to
~~~
As shown above, `grep` displays lines including the word "within" in addition to the given string "with".

Now for the same command with the option `-w` included:
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:229$ grep -w  "with" */*/preface.txt
            We have come together with a unity of purpose because our nation demands it.
                can with the American people. To that end, we held 19 days of hearings and took
            We learned that the institutions charged with protecting our borders, civil aviation,
                officials, past and present, who were generous with their time and provided us with
                fine work helped us get started. We thank the City of New York for assistance with
                whose persistence and dedication helped create the Commission. They have been with
                preparing to respond if it becomes necessary. We emerge from this investigation with
                enormous sympathy for the victims and their loved ones, and with enhanced respect
            We also approach the task of recommendations with humility. We have made a limited
                this process with strong opinions about what would work. All of us have had to
~~~
With the `-w` option, all instances of the word "within" are removed from the display result. This is very useful when searching for a specific whole word and filtering out all other results. Especially if the word is a common root in other words, and the display results would be bloated otherwise.

`grep -c -w  "product" */*/journal.pbio.0020068.txt` \
For this example, we will pair the `-w` option with `-c`, which simply returns the number of lines the given string appears in. Here is the command run without `-w` :
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:233$ grep -c "product" */*/journal.pbio.0020068.txt
10
~~~
And here is the command run with `-w` :
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:234$ grep -c -w  "product" */*/journal.pbio.0020068.txt
0
~~~
When searching for the string "product" without matching the whole word using `-w`, the result of `-c` was 10 appearances. 

After including `-w` to match the whole word, we can see that "product" on its own does not even appear in the file.

This is because the initial command found 10 instances of "production" in the file. `-w` option was useful in this example by creating more strict parameters to search for a given word by. Without the option, the results were skewed.

`grep -c -w "1)" */*/1471-213X-1-15.txt`
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:240$ grep -c -w "1)" */*/1471-213X-1-15.txt
25
~~~
Below is the same command run without `-w` option:
~~~
[cs15lfa22ay@ieng6-203]:skill-demo1:241$ grep -c "1)" */*/1471-213X-1-15.txt
32
~~~
The outputs are 25 with `-w` versus 32 without.

 As with the previous example, the exclusion of `-w` will open up the output to additional lines that do not contain the whole word, producing a more generalized result.

 The given string "1)" appears several times in the file as a header, and the increase in results without `-w` comes from lines that do not contain that header. Therefore, `-w` is useful for making sure no unwanted results are included in the display.

### That's it for this lab report, I hope this is helpful. 

### - Nathan

>[Return to homepage](index.md)

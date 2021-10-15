I testify with my own experience that after I ran a Shell script for over 2 days
with thousands of test cases, `valgrind` rewarded me no bugs. So, if you are a
student struggling to finish a class project the night before deadline, use not
`valgrind` if not required.

What, then, is the substitute? The answer is `flawfinder`! Within a minute of run
on the same software project, it spit out 778 potential bugs. Obviously, this tool
has a high false positivity rate. But it is extremely time-saving and provides
critical information for you to decide the severity of the bugs.

Find the official website [here](http://dwheeler.com/flawfinder/). To download and
install on MacBook, simply run

```
pip install flawfinder
```

To analyze a project, execute

```
flawfinder <directory/to/project>
```

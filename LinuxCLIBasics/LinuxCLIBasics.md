# Linux CLI Basics

> In this walkthrough I had to complete a few assignments regarding CLI usage in Linux.

## Here is how I managed to finish this stage

For the question where there was only needed to copy and paste the command given into
the terminal I did as requested. But then I was provoked to find a new file in the
home directory.

```console
ubuntu@tryhackme:/etc$ find ~ -name day1_report.txt
/home/ubuntu/.logs/archive/day1_report.txt
```

Sometimes my genius is almost frightening! I have found the file location. Now let's preview its content.

```console
ubuntu@tryhackme:/etc$ cd ~/.logs/archive/
ubuntu@tryhackme:~/.logs/archive$ cat day1_report.txt 
Well done! You've completed all tasks for today.

You're starting to get comfortable with the terminal � keep practicing.
Your next set of challenges will build on what you learned here.

FLAG: ....
```


# Lab Report 3 - Labs Done Quick

In this blog post, I will be going over the steps in order to complete the Labs Done Quick Challenge in Week 7.

## Step 4 - ssh
First, I needed to log into the ieng6 remote server. Since I had previously set up my ssh key, my computer remembers the remote and does not require the password to be inputted. Thus, I ran the command: 
`$ ssh cs15lwi23arq@ieng6.ucsd.edu`

And received the following result, successfully logging into my remote:
![step4res](/assets/report4/step4res.png)

## Step 5 - clone
Next, I needed to clone my fork of the lab7 repository. I had previously set up my github ssh key, so all I needed to do was copy/paste the clone url after git clone
`$ git clone git@github.com:spencerho777/lab7.git`

On success, this yields the following output and lab7 is now on my remote:
![step5res](/assets/report4/step5res.png)

## Step 6 - run the tests
Now that I have lab7 on the remote, I can compile and run the. java files. 
First, I had to navigate into the lab7 directory, so I used
`$ cd lab7`

Then, I copied the following javac command from Week 3 with \<cmd\> + \<c\>.
`javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java`
I put this command into the terminal with \<cmd\> + \<v\> This compiles all the java files and links the junit library to the file.

After, I went back to week 3 and copied the java command (again with \<cmd\> + \<c\> and \<cmd\> + \<v\> respectively:
`java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore`
And added the class name of `ListExamplesTests` to the end. In all, this step produces the following result.

![step6res](/assets/report4/step6res.png)

The final key presses are as follows:
*“cd lab7”, \<enter\>, \<click on chrome window\>, \<drag mouse over javac command\>, \<cmd\> + \<c\>, \<click on terminal window\>, \<cmd\> + \<v\>, \<enter\>, \<click on chrome window\>, \<drag mouse over java command\>, \<cmd\> + \<c\>, \<click on terminal window\>, \<cmd\> + \<v\>, “ListExamplesTests”, \<enter\>*

## Step 7 - fix
Now, we need to fix the bug in the code. In this case, the problem is that on line 43, inside the while loop, the wrong variable is incremented. The program increments index1 instead of index 2.

We open up the file with `nano ListExamples.java`

Then in order to quickly navigate to the incorrect line, we do *\<ctrl\> + \<-\>*, then type in *43, 13*, then *\<enter\>*.
This is what it should look like:
![step7res](/assets/report4/step7res.png)

To change the error, we just need to change the 1 to a 2, so do *\<backspace\>, \<2\>*
Then, we need to save and exit the editor with \<ctrl\> + \<o\>, \<enter\>, \<ctrl\> + \<x\>

## Step 8 - pass the tests
Now, we need to rerun the tests. To do this, we can use the up arrow key to reuse our previous commands.

Keypresses: *\<up\>, \<up\>, \<up\>, \<enter\>* which goes up 3 commands in history and runs the javac command

Keypresses: *\<up\>, \<up\>, \<up\>, \<enter\>* which goes up 3 commands in history and runs the java command

This should produce the following result:
![step8res](/assets/report4/step8res.png)

## Step 9 - commit and push
After passing the tests, the last thing we need to do is push this change to our forked repo. This can be done with three commands.
```
$ git add .
$ git commit -m “fix”
$ git push origin main
```

`git add .` adds all our changed files to our commit

`git commit -m “fix”` creates a commit with the message of “fix”

`git push origin main` pushes our commit

If everything was done right, you should see:
![step9res](/assets/report4/step9res.png)

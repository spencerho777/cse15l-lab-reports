

** # Lab Report 1 - VSCode, Remote Connecting, CMD Line**

In this blog post, I will describe how to install VSCode, connect remotely to a computer, and run some commands on that computer.

## Installing VSCode
***
Navigate to the VSCode website and find the [download page](https://code.visualstudio.com/download) You should be presented with a screen like this
[Image]

Once the zip file downloads, open it, and finish the installation of VSCode by following the instructions of the setup wizard. When you open the application, open up the terminal in VSCode by clicking the icon marked by the red arrow or type Ctrl + J for Windows / Cmd + J for MacOS
[Image]

If you already have a password for your cs15l account, skip this next step

## Resetting your account password
***
Now, we need to reset the password of your cs15l account. Go to the following [link](https://sdacs.ucsd.edu/~icc/index.php) and look up your account with your username and student id. Click the reset password button and follow the instructions to create a new password. Wait 15 minutes before continuing to ensure your password has been reset.

##Remotely Connecting
***
Find your account username from the account look up page (circled in red) and remember the last 3 digits of the username. Then, in the terminal on VSCode, type in the following command:

`ssh cs15lwi23(last 3 digits go here)@ieng6.ucsd.edu`

You will be then prompted to enter in your password for the account. You should then be presented with the following screen.
[Image]
Congratulations! You have successfully remotely connected to a computer at UCSD.

##Running Commands
***
Now that you are remotely connected to a computer, it’s time to run some commands. Here are a few commands to try out:

`cd ~` navigates back to the home directory
`cd <directory>` will bring you that directory
`ls -a` lists all files in the current directory
`cp /home/linux/ieng6/cs15lwi23/public/hello.txt ~/` copies the hello.txt file into the home directory
`cat /home/linux/ieng6/cs15lwi23/public/hello.txt` reads the hello.txt file

Here are some sample inputs and outputs
[Image]

And that’s it! You have now successfully installed VSCode, connected remotely to a computer, and ran some commands on that computer.

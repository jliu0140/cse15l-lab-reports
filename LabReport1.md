## CSE15L Account
We will first start by finding your CSE 15L account.
Go to this link: [https://sdacs.ucsd.edu/~icc/index.php](https://sdacs.ucsd.edu/~icc/index.php)

Sign in with your UCSD username and PID. The account name should be cs15lwi23zzz where zzz will be three characters unique to you.

![15L account.PNG](https://github.com/jliu0140/cse15l-lab-reports/blob/main/15L%20account.PNG?raw=true)

Click on your account name and look for a prompt to change your password. When creating a password, make sure it includes uppercase letters, lowercase letters, symbols, and numbers. Some characters such as spaces will not be allowed. When you have your password, make sure to mark no for "Change my TritonLink password. After, stay in the confirm password box and press enter. Do not click "Check Password."

![Image](https://github.com/jliu0140/cse15l-lab-reports/blob/main/password%20change.PNG)

If everything goes well, a "Success!" prompt will show up.
## Visual Code Studio
Next, we will need to download Visual Studio Code at this link: [https://code.visualstudio.com/](https://code.visualstudio.com/)

Make sure to install the correct version for your operating system and follow the instructions for installation. Once done, it should look something like this.

![Image](https://github.com/jliu0140/cse15l-lab-reports/blob/main/vs%20code.PNG)
## Connecting Remotely
To remotely connect, one of the first things to do is install `git` if you are on Windows. Install from this link: [https://gitforwindows.org/](https://gitforwindows.org/)

Next, we will setup git bash as the default terminal. First open up the terminal by pressing Ctrl + ` or open it from the top menu.

![Image](https://github.com/jliu0140/cse15l-lab-reports/blob/main/open%20terminal.PNG)

Next, press Ctrl + Shift + P and enter Select Default Profile. Select Git Bash.

![Image](https://github.com/jliu0140/cse15l-lab-reports/blob/main/git%20bash.PNG)

Once git bash is setup as the default terminal, enter `ssh ACCOUNTNAME@ieng6.ucsd.edu` into the terminal, where your account name is the cs15lwi23zzz that you found earlier. Enter yes for the first prompt and then enter your new password. Note, when entering your password, no corresponding text will show up in the terminal. Once done, the terminal should look like this.

![Image](https://github.com/jliu0140/cse15l-lab-reports/blob/main/terminal.PNG)
## Trying Commands
Once you are connected, you can try using some commands in the terminal. Some useful commands to know are `cd`, `ls`, `pwd`, `mkdir`, `cp`, and `cat`. Since you are remotely connected, the files are not local and neither is the path. Be sure to use the directory that you are connected to.

![Image](https://github.com/jliu0140/cse15l-lab-reports/blob/main/commands.PNG)

When you are finished, you can exit the terminal by entering `exit`.

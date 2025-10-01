# PRACTICING PIPING

## REDIRECTING OUTPUT
### FLAG: pwn.college{Y_hZA9y5I5WqseiO7DNmFioFjUa.dRjN1QDLycTN0czW}
### APPROACH USED
````
echo PWN > COLLEGE
````
This redirects the ourput of the command `echo PWN` to the file **COLLEGE**. Therefore, if COLLEGE is read then it will print the word PWN.

## REDIRECTING MORE OUTPUT
### FLAG: pwn.college{gQOiQV_1Yi_WSvXnZrx60B17NTE.dVjN1QDLycTN0czW}
### APPROACH USED: 
````
/challenge/run > myflag
cat myflag
````
This redirects the ourput of the command `/challenge/run` into a file called **myfile**. When the contents of the file are read using the command `cat`, it outputs the flag.

## APPENDING OUTPUT
### FLAG: pwn.college{A-u8mEVnD3ASKXisQouXL8ueUKY.ddDM5QDLycTN0czW}
### APPROACH USED
````
/challenge/run >> /home/hacker/the-flag
cat ~/the-flag
````
This allows me to first append the output of the command `/challenge/run` to the file `/home/hacker/the-flag`. Since I used append(>>) instead of truncation(>), the second half of my flag was appended to the first and I got the correct flag.

## REDIRECTING ERRORS
### FLAG: pwn.college{woAl3L8byo4SqyZ2SjTR-YPrrFb.ddjN1QDLycTN0czW}
### APPROACH USED
````
hacker@piping~redirecting-errors:~$ /challenge/run 1> myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{woAl3L8byo4SqyZ2SjTR-YPrrFb.ddjN1QDLycTN0czW}

hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
````

I used the command `/challenge/run 1> myflag 2> instructions` to redirect the output to the file `myflag` and the instructions (in this case, that is the error) to the file 'instructions`.

## REDIRECTING INPUT 
### FLAG: pwn.college{MfX6Pqo1CXLljWapRFGdF0XLaat.dBzN1QDLycTN0czW}
### APPROACH USED
````
echo COLLEGE > PWN
/challenge/run < PWN
````
In this, the command `eco COLLEGE > PWN` puts the value **COLLEGE** in the file *PWN*. After that the file PWN is redirected to /challenge/run using input redirection.

## GREPPING STORED RESULTS
### FLAG: pwn.college{8lOtpwmlW1P66z7K21rEnbG8FnY.dhTM4QDLycTN0czW}
### APPROACH USED
````
 /challenge/run > /tmp/data.txt
 grep pwn.college /tmp/data.txt
````
In this, the commad `/challenge/run > /tmp/data.txt` redirects the output of `/challenge/run` to the file `/tmp/data.txt`. Then since all flags start with **"pwn.college"**, we can use `grep pwn.college /tmp/data.txt` to search through the file and find the flag.

## GREPPING LIVE OUTPUT
### FLAG: pwn.college{44LpFXidxgyqi1bTx2O8cABMHi_.dlTM4QDLycTN0czW}
### APPROACH USED 
````
/challenge/run | grep pwn.college
````
This command basically gets the ouput of the command `/challenge/run`. At the same time, it automatically greps the flag from that output using `grep pwn.college`

## GREPPING ERRORS
### FLAG: pwn.college{wdWU4ijmhVqKyUVEDAQn1zV_avC.dVDM5QDLycTN0czW}
#### APPROACH USED
````
/challenge/run 2>&1 | grep pwn.college
````
This command used the >& operator which redirects a file desriptor to another. Therefore `2>&1` redirects the **fd 2 (standard error)** to **fd 1** and then uses the **pipe(|)** operator to also use the `grep pwn.college` command to get the flag from the error.

## DUPLICATING PIPED DATA WITH TEE
### FLAG: pwn.college{QSmAFw8YVWFrhlnsNI7hygidFHo.dFjM5QDLycTN0czW}
### APPROACH USED
````
/challenge/pwn | tee pwn | /challenge/college
cat pwn
/challenge/pwn --secret QSmAFw8Y | /challenge/college
````
In this, the output from `challenge/pwn` is intercepted by the `tee pwn` commmand. With this, by running `cat pwn`, we can get the secret code and syntax to properly properly pipe /challenge/pwn to /challenge/college

## WRITING TO MULTIPLE PROGRAMS
### FLAG: pwn.college{8vTCMypwR6qz1i6755Is_X5YASZ.dBDO0UDLycTN0czW}
### APPROACH USED
````
/challenge/hack | tee >(/challenge/the) >(/challenge/planet)
````
In this, the output of the command `/challenge/hack/` is used as input for both `/challenge/the` and `/challenge/planet`

## SPLIT-PPIPING STDERR AND STDOUT
### FLAG: pwn.college{wPk12mihqrVaJNNYT2v8pgksIcj.dFDNwYDLycTN0czW}
### APPROACH USED 
````
/challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
````
In this challenge, We know that `x | y` is equivalent to `x > >(y)` from the previous problem.   
I had to first redirect the stdout of `/challenge/hack` to `/challenge/planet`. This could be done by `/challenge/hack > >( /challenge/planet )`.   
Secondly, I had to redirect sterror of `/challenge/hack` to `/challenge/the`. This could be done by `/challenge/hack 2> >(/challenge/the)`.  
Combining these two commands we get, `/challenge/hack > >(/challenge/planet) 2> >(/challenge/the)`
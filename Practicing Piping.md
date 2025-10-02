# PRACTICING PIPING

## REDIRECTING OUTPUT
### FLAG: pwn.college{Y_hZA9y5I5WqseiO7DNmFioFjUa.dRjN1QDLycTN0czW}
### APPROACH USED
````
echo PWN > COLLEGE
````
The `>` operator redirects standard output to a file. This command redirects the output of `echo PWN` to the file **COLLEGE**. Therefore, if COLLEGE is read then it will print the word PWN.

## REDIRECTING MORE OUTPUT
### FLAG: pwn.college{gQOiQV_1Yi_WSvXnZrx60B17NTE.dVjN1QDLycTN0czW}
### APPROACH USED: 
````
/challenge/run > myflag
cat myflag
````
Output redirection using `>` can capture command results into files. This redirects the output of the command `/challenge/run` into a file called **myflag**. When the contents of the file are read using the command `cat`, it outputs the flag.

## APPENDING OUTPUT
### FLAG: pwn.college{A-u8mEVnD3ASKXisQouXL8ueUKY.ddDM5QDLycTN0czW}
### APPROACH USED
````
/challenge/run >> /home/hacker/the-flag
cat ~/the-flag
````
The `>>` operator appends output to a file instead of overwriting it like `>` does. This allows me to first append the output of the command `/challenge/run` to the file `/home/hacker/the-flag`. Since I used append(`>>`) instead of truncation(`>`), the second half of my flag was appended to the first and I got the correct flag.

## REDIRECTING ERRORS
### FLAG: pwn.college{woAl3L8byo4SqyZ2SjTR-YPrrFb.ddjN1QDLycTN0czW}
### APPROACH USED
````
/challenge/run 1> myflag 2> instructions
cat myflag
cat instructions
````
File descriptors can be explicitly specified: `1>` redirects stdout (standard output) and `2>` redirects stderr (standard error). I used the command `/challenge/run 1> myflag 2> instructions` to redirect the output to the file `myflag` and the error messages to the file `instructions`.

## REDIRECTING INPUT 
### FLAG: pwn.college{MfX6Pqo1CXLljWapRFGdF0XLaat.dBzN1QDLycTN0czW}
### APPROACH USED
````
echo COLLEGE > PWN
/challenge/run < PWN
````
The `<` operator redirects input from a file to a command. In this, the command `echo COLLEGE > PWN` puts the value **COLLEGE** in the file **PWN**. After that the file PWN is redirected to `/challenge/run` using input redirection.

## GREPPING STORED RESULTS
### FLAG: pwn.college{8lOtpwmlW1P66z7K21rEnbG8FnY.dhTM4QDLycTN0czW}
### APPROACH USED
````
/challenge/run > /tmp/data.txt
grep pwn.college /tmp/data.txt
````
Combining redirection with `grep` allows efficient searching through command output. In this, the command `/challenge/run > /tmp/data.txt` redirects the output of `/challenge/run` to the file `/tmp/data.txt`. Then since all flags start with **"pwn.college"**, we can use `grep pwn.college /tmp/data.txt` to search through the file and find the flag.

## GREPPING LIVE OUTPUT
### FLAG: pwn.college{44LpFXidxgyqi1bTx2O8cABMHi_.dlTM4QDLycTN0czW}
### APPROACH USED 
````
/challenge/run | grep pwn.college
````
The pipe operator `|` sends the output of one command directly to another without creating intermediate files. This command gets the output of the command `/challenge/run` and automatically greps the flag from that output using `grep pwn.college`.

## GREPPING ERRORS
### FLAG: pwn.college{wdWU4ijmhVqKyUVEDAQn1zV_avC.dVDM5QDLycTN0czW}
### APPROACH USED
````
/challenge/run 2>&1 | grep pwn.college
````
The `2>&1` operator redirects stderr (fd 2) to stdout (fd 1), allowing error messages to be piped. This command uses the `>&` operator which redirects a file descriptor to another. Therefore `2>&1` redirects **fd 2 (standard error)** to **fd 1 (standard output)** and then uses the **pipe(`|`)** operator to also use the `grep pwn.college` command to get the flag from the error output.

## FILTERING WITH GREP -V
### FLAG: pwn.college{INZugK_39oBlklibtlmh1YqjbjC.QX4ETM3EDLycTN0czW}
### APPROACH USED:
```
/challenge/run | grep -v DECOY
```
The `grep -v` flag inverts the match, showing only lines that don't contain the specified pattern. This filters out all lines containing "DECOY" from the output, leaving only the real flag.

## DUPLICATING PIPED DATA WITH TEE
### FLAG: pwn.college{QSmAFw8YVWFrhlnsNI7hygidFHo.dFjM5QDLycTN0czW}
### APPROACH USED
````
/challenge/pwn | tee pwn | /challenge/college
cat pwn
/challenge/pwn --secret QSmAFw8Y | /challenge/college
````
The `tee` command reads from stdin and writes to both stdout and a file simultaneously, allowing data inspection mid-pipeline. In this, the output from `/challenge/pwn` is intercepted by the `tee pwn` command. With this, by running `cat pwn`, we can get the secret code and syntax to properly pipe `/challenge/pwn` to `/challenge/college`.

## PROCESS SUBSTITUTION FOR INPUT
### FLAG: pwn.college{0FI99JBkQfGmJ-AW8RjY0HNFSLc.QX2AzM4EDLycTN0czW}
### APPROACH USED:
```
diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
```
Process substitution `<(command)` creates temporary named pipes that can be used as file arguments. Bash runs the command and provides its output through a file descriptor like `/dev/fd/63`. This allows `diff` to compare the outputs of two commands directly without creating intermediate files.

## WRITING TO MULTIPLE PROGRAMS
### FLAG: pwn.college{8vTCMypwR6qz1i6755Is_X5YASZ.dBDO0UDLycTN0czW}
### APPROACH USED
````
/challenge/hack | tee >(/challenge/the) >(/challenge/planet)
````
Combining `tee` with process substitution allows sending output to multiple programs simultaneously. In this, the output of the command `/challenge/hack` is used as input for both `/challenge/the` and `/challenge/planet` using process substitution syntax `>(command)`.

## SPLIT-PIPING STDERR AND STDOUT
### FLAG: pwn.college{wPk12mihqrVaJNNYT2v8pgksIcj.dFDNwYDLycTN0czW}
### APPROACH USED 
````
/challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
````
Process substitution can be combined with file descriptor redirection to route stdout and stderr to different destinations. In this challenge, we know that `x | y` is equivalent to `x > >(y)` from the previous problem. I had to first redirect the stdout of `/challenge/hack` to `/challenge/planet` using `> >(/challenge/planet)`. Secondly, I had to redirect stderr of `/challenge/hack` to `/challenge/the` using `2> >(/challenge/the)`. Combining these two commands we get the final solution.

## NAMED PIPES
### FLAG: pwn.college{0IUj-ixv9fUlHrq6bnKkLlsCYJA.QXzMzM4EDLycTN0czW}
### APPROACH USED:
```
mkfifo /tmp/flag_fifo
/challenge/run > /tmp/flag_fifo
cat /tmp/flag_fifo
```
Named pipes (FIFOs) are persistent pipe files created with `mkfifo` that enable inter-process communication. Unlike regular files, FIFOs pass data directly in memory and block operations until both reader and writer are ready. This requires two terminals: one to write to the FIFO (`/challenge/run > /tmp/flag_fifo`) and another to read from it (`cat /tmp/flag_fifo`). The blocking behavior provides automatic synchronization between processes.

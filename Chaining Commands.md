# CHAINING COMMANDS

## CHAINING WITH SEMICOLONS
### FLAG: pwn.college{s0vFH8qhQtDTGRwa69bYUJUdE75.dVTN4QDLycTN0czW}
### APPROACH USED:
````
/challenge/pwn ; /challenge/college
````

## YOUR FIRST SHELL SCRIP
### FLAG: pwn.college{osNMxWfnT2KAcm4RTvERsZ-rMYB.dFzN4QDLycTN0czW}
### APPROACH USED:
````
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{osNMxWfnT2KAcm4RTvERsZ-rMYB.dFzN4QDLycTN0czW}
````
We create a file called `x.sh`. In this, we can have the commands `/challenge/pwn` and `challenge/college`. When we bash this file, the commands inside the file are executed and we get the flag.

## REDIRETINF SCRIPT COMMAND
### FLAG: pwn.college{IGhSuGFxCraHh3fxhXTJAGvebUI.dhTM5QDLycTN0czW}
### APPROACH USED:
````
hacker@chaining~redirecting-script-output:~$ touch script.sh
hacker@chaining~redirecting-script-output:~$ nano script.sh
hacker@chaining~redirecting-script-output:~$ bash script.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{IGhSuGFxCraHh3fxhXTJAGvebUI.dhTM5QDLycTN0czW}
````
We create a file called `script.sh`. In this, we can have the commands `/challenge/pwn` and `challenge/college`. When we bash this file, the commands inside the file are executed. The output of the file is then piped into the `/challenge/solve` program using the `|` operator and we get the flag.

## EXECUTABLE SHELL SCRIPTS
### FLAG: pwn.college{ocPV9sbcbTDBNtSaUFPNRbNvgxf.dRzNyUDLycTN0czW}
### APPROACH USED:
````
hacker@chaining~executable-shell-scripts:~$ touch exec.sh
hacker@chaining~executable-shell-scripts:~$ nano exec.sh
hacker@chaining~executable-shell-scripts:~$ chmod ugo+x exec.sh
hacker@chaining~executable-shell-scripts:~$ ./exec.sh
Congratulations on your shell script execution! Your flag:
pwn.college{ocPV9sbcbTDBNtSaUFPNRbNvgxf.dRzNyUDLycTN0czW}
````
We create a file called `exec.sh`. In this, we can have the commands `/challenge/solve`. We can make this file executable by the `chmod ugo+x exec.sh` command. When we try to execute the program with `./exec.sh` from our home directory, we get the flag
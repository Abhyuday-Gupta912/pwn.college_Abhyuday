# PONDERING PATHS 
## THE ROOT 
### FLAG: pwn.college{wNnRd4y69Kr82ndtd9S25Oemtnn.dhzN5QDLycTN0czW}
### APPROACH USED 
typed `/pwn`  
This is the absolute path of the pwn program where **/** is the root of the filesystem.

## PROGRAM AND ABSOLUTE PATHS 
### FLAG: pwn.college{g4YAg3tXJk5I8dNibtekL415Gil.dVDN1QDLycTN0czW}
### APPROACH USED 
`/challenge/run`   
This makes us access the run proram which is in the challenge directory which is in turn in the root directory (**/**)

## POSITION THY SELF 
### FLAG: pwn.college{8pQAIIlMI_Q-mxLa9wTeXgeTG-f.dZDN1QDLycTN0czW}
### APPROACH USED 
````
/challenge/run
cd /home
/challenge/run
````
the first /challenge/run command told me that the directory i had to cd to was /home. After that cding to the home directory, i ran the command to run.

## POSITION ELSEWHERE
### FLAG: pwn.college{EXf-2WQEwBOVzpP0FomybTgqFYy.ddDN1QDLycTN0czW}
### APPROACH USED 
````
/challenge/run
cd /tmp
/challenge/run
````
the first /challenge/run command told me that the directory i had to cd to was /tmp. After that cding to the home directory, i ran the command to run.

## POSITION YET ELSEWHERE
### FLAG: pwn.college{YPiU0nZR20n4CXKq_chLVk6j3ln.dhDN1QDLycTN0czW}
### APPROACH USED 
````
/challenge/run
cd /home
/challenge/run
````
the first /challenge/run command told me that the directory i had to cd to was /home. After that cding to the home directory, i ran the command to run.

## IMPLICIT RELATIVE PATHS, FROM /
### FLAG: pwn.college{YqA1AmtEIc4dArSTjC-Goig71Bi.dlDN1QDLycTN0czW}
````
cd /
challenge/run
````
`cd /` put me in the root directory. There using `challenge/run` i ran the run program in the challenge directory

## EXPLICIT RELATIVE PATHS, FROM /
### FLAG: pwn.college{YJAs8sMELPkGYQXuYWYVnl3YwlT.dBTN1QDLycTN0czW}
````
cd /
./challenge/run
````
`cd /` put me in the root directory. There using `challenge/run` i ran the run program in the challenge directory

## IMPLICIT RELATIVE PATH
### FLAG: pwn.college{gN14p1tH1qGtaB_Y5VZaQsPnRD2.dFTN1QDLycTN0czW}
### APPROACH USED:
````
cd challenge
./run
````
I get into the diretory challeng, then run the program **run** in the directory.

## HOME SWEET HOME 
### FLAG: pwn.college{IDixvfzLhHJKNhrLxvPEsLg6B-e.dNzM4QDLycTN0czW}
### APPROACH USED 
````
/challenge/run ~/A
````
Considering the constraints given
1. Your argument must be an absolute path.
2. The path must be inside your home directory.
3. Before expansion, your argument must be three characters or less.

The argument I used was `~/A` which satisfied all these conditions.

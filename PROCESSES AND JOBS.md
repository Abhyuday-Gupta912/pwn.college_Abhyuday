# PROCESSES AND JOBS

## LISTING PROCESSES
### FLAG: pwn.college{knVtVAjt65DDAAqaMGCvQjyCDZE.dhzM4QDLycTN0czW}
### APPROACH USED:
````
ps aux
/challenge/4696-run-2237
````
The command `ps aux` listed out all the processes runnning at the time. From the list, we got to know that the command to get the flag was `/challenge/4696-run-2237`

## KILLING PROCESSES
### FLAG: pwn.college{s-KZzJxvk0vXh_3WtQp6fO1c1Pr.dJDN4QDLycTN0czW}
### APPROACH USED:
````
ps aux
kill 73
/challenge/run
````
In this, I first listed out all the processes using the `ps aux` command. Then from the list outputed. I found that the PID of the `/challenge/dont_run` was 73. Therefore, `kill 73` terminated that process which allowed me to run `/challenge/run` and get the flag.

## INTERRUPTING PROCESSES
### FLAG: pwn.college{UcjvxRr8GAJWvVJvZDXj7idS_8p.dNDN4QDLycTN0czW}
### APPROACH USED:
````
/challenge/run
````
after running `/challenge/run` once, we can interrupt it by pressing "ctrl+C" in order to force exit and reveal the flag.

## SUSPENDING PROCESSES
### FLAG: pwn.college{wvlR7eKkWatmLwWZiYBhwkSE_sQ.dVDN4QDLycTN0czW}
### APPROACH USED:
````
/challenge/run
    (*/ctrl+z/*)
/challenge/run
````
This allowed me to first start the run program and then suspend it by pressing 'ctrl+z'. Running a copy of the program again while it suspended in the background revealed the flag.

## RESUMING PROCESSES
### FLAG: pwn.college{ImU-IUZ7NYp3iAfR8ucbtbMJO6O.dZDN4QDLycTN0czW}
### APPROACH USED:
````
/challenge/run
    (ctrl+z)
fg
````
This allowed me to first start the run program and then suspend it by pressing 'ctrl+z'. The command `fg` allows us to resume the suspended process

## BACKGROUNDING PPROCESSES
### FLAG: pwn.college{Qe1szBw2JEJK8LBNU-Rf5Z8S7Y2.ddDN4QDLycTN0czW}
### APPROACH USED:
````
/challenge/run
    (ctrl+z)
bg
/challenge/run
````

## FOREGROUNDING PROCESSES
### FLAG: pwn.college{4ZPCkd4eUmjhlzr7ZpH3zIRiHk2.dhDN4QDLycTN0czW}
### APPROACH USED:
````
/challenge/run
bg
fg
````

## STARTING BACKGROUND PROCESSES
### FLAG: pwn.college{0853jrt4muA-oiPoz1sbWPdZiKd.dlDN4QDLycTN0czW}
### APPROACH USED: 
````
/challenge/run &
````

## PROCESS EXIT CODES
### FLAG: pwn.college{4qTUbmYWTh4MIkHkFT9Qktfj-JV.dljN4UDLycTN0czW}
### APPROACH USED:
````
/challenge/get-code
echo $?
/challenge/submit-code 246
````

# SHELL VARIABLES

## Printing Variables
### FLAG: pwn.college{41PfDAvpvzMXyE2dOwnnfq2rih6.ddTN1QDLycTN0czW}
### APPROACH USED:
````
echo $FLAG
````
prepending **FLAG** with a "$" sign made allows us to print the conttents of the vairable named FLAG

## SETTING VARIABLES
### FLAG: pwn.college{g2o70Wlv_Wv7m0Ip0bDQlhCvfDH.dlTN1QDLycTN0czW}
### APPROACH USED:
````
PWN=COLLEGE
````

## MULTI-WORD VARIABLES
### FLAG: pwn.college{kC48jxG118gGoiyaNkWqr-JOiWz.dBjN1QDLycTN0czW}
### APPROACG USED:
````
PWN="COLLEGE YEAH"
````

## EXPORTING VARIABLES
### FLAG: pwn.college{4e0vAqo83jXLRijJqm81qqXiWQN.dJjN1QDLycTN0czW}
### APPROACH USED:
````
COLLEGE='PWN'
export PWN=COLLEGE
sh
/challenge/run $PWN
````
Here, I first assigned the value **PWN** to the variable **COLLEGE** then created another variable **PWN** which had the value of the college variable and needed to be exportd. Then I ran `sh` command after which i ran the `/challenge/run` command to get the flag

## PRINTING EXPORTED VARIABLES
### FLAG:
### APPROACH USED:
````
env
````
This command gave me a list of al the variables and their values. Due to this I was able to locate the flag from the listed variables. 

## STORING COMMAND OUTPUT
### FLAG: pwn.college{YtwzGgp2gwu1a5tRilfWtaODrQ5.dVzN0UDLycTN0czW}
### APPROACH USED:
````
PWN=$(/challenge/run)
echo $PWN
````
`PWN=$(/challenge/run)` allows us to store the output of the command `/challenge/run` in the variable **FLAG**. Printing the value gives us the flag.

## READING INPUT
### FLAG: pwn.college{IPB1PFPY2AEpE_SYo8_tXAMtxFU.dhzN1QDLycTN0czW}
### APPROACH USED: 
````
read -p "INPUT: " PWN
````

## READIND FILE
### FLAG: pwn.college{A8_o6n_tSSxbe2dvpO3XyzOooq5.dBjM4QDLycTN0czW}
### APPROACH USED: 
````
read PWN < /challenge/read_me
````
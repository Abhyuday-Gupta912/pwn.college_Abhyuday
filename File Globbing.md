# FILE GLOBBING

## MATCHING WITH *
### FLAG: pwn.college{8bs4Ul-JW0BcvPK_-WURWk-WtpY.dFjM4QDLycTN0czW}
### APPROACH USED 
````
cd /ch
/challenge/run
````
Since we have to get into the directory `/challenge` and we can only use 4 characters in our `cd` statement. Therefore the argument to pass is `cd /ch*`

## MATCHING WITH ?
### FLAG: pwn.college{ABLNnVgZaFpVB6ya-VCrBgFOt4J.dJjM4QDLycTN0czW}
### APPROACH USED
````
cd /?ha??enge
/challenge/run
````
Since we have to get into the directory `/challenge` and we replace c and l by **?** characters in our `cd` statement. Therefore the argument to pass is `cd /?ha??enge`

## MATCHING WIH []
### FLAG: pwn.college{gYtfgouey4IhUJiZctTHrdSqyTX.dNjM4QDLycTN0czW}
### APPROACH USED:
````
cd /challenge/files
/challenge/run file_[bash]
````

## MATCHING PATHS WITH []
### FLAG: pwn.college{YlqpyI-UL3DEaBDnam-iiWVwL8N.dRjM4QDLycTN0czW}
### APPORACH USED:
````
/challenge/run /challenge/files/file_[bash]
````

## MIXING GLOBS
### FLAG: pwn.college{0-Y2eJW9QnCT3zsxYd27ss4ReH4.dVjM4QDLycTN0czW}
### APPORACH USED:
````
cd /challenge/files
/challenge/run [cep]*
````
In this I had to first get into the `/challenge/files` directory using the `cd` command. After that I listed all the files in the directory to see any patterns that are common in **"challenging", "educational", and "pwning"** but not in the other files.  
After analyzing the different files, I came to the conclusion that `[cep]*` would be the appropriate glob to be used

## EXCLUSIONARY GLOBBING
### FLAG: pwn.college{ABaASSkp9mtdgT7WzAy1r6Aq-Pc.dZjM4QDLycTN0czW}
### APPROACH USED 
````
cd /challege/files
/challenge/run [^pwn]*
````
In this I had to first get into the `/challenge/files` directory using the `cd` command. After that, I ran the glob `[^pwn]*`. The ^ makes it so that the files do not start with **"p","w","n"** and the * finds the rest of the string 
# COMPREHENDING COMMANDS

## CAT, NOT THE PET, BUT THE COMMAND!
### FLAG: pwn.college{4D24qgVrIofBRm7zCxiHnS6bPPO.dFzN1QDLycTN0czW}
### APPROACH USED 
````
cat flag
````
reads the file flag in the home directory

## CATTING ABSOLUTE PATHS
### FLAG: pwn.college{8ddLfLg5fVMQGuo9-hqb4hU3Zmf.dlTM5QDLycTN0czW}
### APPROACH USED 
````
cat /flag
```` 
This uses the absolute path of the file **flag** present in the root directory to read the file.

## MORE CATTING PRACTICE 
### FLAG: pwn.college{siVdV0CXNZtqczlfeWm9O85YCs3.dBjM5QDLycTN0czW}
### APPROACH USED
````
cat /usr/share/tcltk/flag

````
This uses the absolute path of the file **flag** given to us to read the file.

## GREPPING FOR A NEEDLE IN A HAYSTACK
### FLAG: pwn.college{sOSkW8dl9Au4pcy3t8p7ElRdKEs.ddTM4QDLycTN0czW}
### APPROACH USED
````
grep pwn.college /challenge/data.txt
````
Since all flags start with **pwn.college**; If we look for that in the occurence of that text in the file data.txt present in the challenge directory, we can find the flag.

## LISTING FILES 
### FLAG: pwn.college{IPeFwdBNrSXL_vFQ57ZuwEoFX4d.dhjM4QDLycTN0czW}
### APPROACH USED 
````
ls /challenge
/challenge/12787-renamed-run-23253
````
Listing all the files in the directory challenge, we see the program 12787-renamed-run-23253. This is the renamed run program.

## TOUCHING FILES 
### FLAG: pwn.college{IBYI7dxp4opOaG-fX-8eINAmRUC.dBzM4QDLycTN0czW}
### APPROACH USED
````
cd /
touch pwn
touch college 
/challenge/run
````
First i get into the root directory using the cd command. Then touch(create) the two required files. Then run the command.

## REMOVING FILES 
### FLAG: pwn.college{0kBh2d9jRMZrkJO99eCGLi5n0LS.dZTOwUDLycTN0czW}
### APPROACH USED 
````
rm delete_me
/challenge/check
````
First i delete the file, then use the command to check in order to recieve the flag

## HIDDEN FILES 
### FLAG: pwn.college{kmDiXO-tub2_sJOoao0Rvi0cgFi.dBTN4QDLycTN0czW}
### APPROACH USED 
````
ls / -a
cat .flag-32364580120922
````
Listing all the elements of the root directory, i found the flag file. Then, I read the elements of the file to get the flag

## AN EPIC FILESYSTEM QUEST
### FLAG: pwn.college{06jNSaazZtrq_MGm7NAlZB-N5CJ.dljM4QDLycTN0czW}
### APPROACH USED 
````
cd /
ls
ls /usr/share/icons/ubuntu-mono-light/places/24
cat /usr/share/icons/ubuntu-mono-light/places/24/TRACE-TRAPPED
ls /usr/share/X11/locale/vi_VN.tcvn
cat /usr/share/X11/locale/vi_VN.tcvn/TEASER
ls /usr/lib/x86_64-linux-gnu/perl-base/unicore/lib/Dt -a
cat /usr/lib/x86_64-linux-gnu/perl-base/unicore/lib/Dt/.WHISPER
ls /usr/local/lib/python3.8/dist-packages/jsonschema/benchmarks/issue232
cat /usr/local/lib/python3.8/dist-packages/jsonschema/benchmarks/issue232/LEAD
ls /usr/lib/debug/.build-id/56
cat /usr/lib/debug/.build-id/56/REVELATION
ls /usr/share/locale/af/LC_MESSAGES
cat /usr/share/locale/af/LC_MESSAGES/SPOILER-TRAPPED
ls /usr/lib/python3/dist-packages/sympy/solvers/benchmarks
cat /usr/lib/python3/dist-packages/sympy/solvers/benchmarks/DOSSIER
cd /usr/share/doc/libsensors5
ls
cat README
````
This process of first listing elements in a directory and then opening different files in order to get clues led me to get the flag.

## MAKING DIRECTORIES
### FLAG: pwn.college{wzZH1U5eFgb93bmUHcy_KjDuZY_.dFzM4QDLycTN0czW}
### APPROACH USED 
````
mkdir /tmp/pwn
touch /tmp/pwn/college
````
This makes a directory pwn in the directory tmp. Then I add a file college to the newly created directory.

## FINDING FILES 
### FLAG: pwn.college{IqJbjhLSy8y9bU0tKoOjpXpsbkk.dJzM4QDLycTN0czW}
### APPROACH USED 
````
find / -name flag
cat /usr/local/lib/python3.8/dist-packages/angr/engines/vex/claripy/__pycache__/flag
````
The first command allowed to search the root directory and all the directories within it for a file or directory named file and listed it out. After that, through trial and error, I found the file with the flag in it.

## LINKING FILES 
### FLAG: pwn.college{Ql5jtxqnKxtSgblWMO10KlsUwKw.dlTM1UDLycTN0czW}
### APPROACH USED 
````
ln -s /flag ~/not-the-flag
/challenge/catflag
````
I use symbbolic link to link the file `~/not-the-flag` with the source `/flag`. Due to this when I use the command `/challenge/catflag`, the contents of the flag file was used.
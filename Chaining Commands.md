# CHAINING COMMANDS

## CHAINING WITH SEMICOLONS
### FLAG: pwn.college{s0vFH8qhQtDTGRwa69bYUJUdE75.dVTN4QDLycTN0czW}
### APPROACH USED:
````
/challenge/pwn ; /challenge/college
````
The semicolon `;` operator allows chaining multiple commands sequentially. Each command runs regardless of whether the previous command succeeded or failed. This is useful for executing a series of independent commands in one line.

## BUILDING ON SUCCESS
### FLAG: pwn.college{EDhw4bAHyxght7hXq8fRvpINe8w.QXyQzM4EDLycTN0czW}
### APPROACH USED:
```
/challenge/first-success
/challenge/second
/challenge/first-success && /challenge/second
```
The `&&` operator (logical AND) chains commands conditionally - the second command only runs if the first succeeds (returns exit code 0). This is useful for ensuring dependent operations only execute when prerequisites are met.

## HANDLING FAILURE
### FLAG: pwn.college{Eh9RZyZ_-qA_S-1eGIHhJOUO5po.QXzQzM4EDLycTN0czW}
### APPROACH USED:
```
/challenge/first-failure || /challenge/second
```
The `||` operator (logical OR) executes the second command only if the first command fails (returns non-zero exit code). This is useful for fallback operations or error handling scenarios.

## YOUR FIRST SHELL SCRIPT
### FLAG: pwn.college{osNMxWfnT2KAcm4RTvERsZ-rMYB.dFzN4QDLycTN0czW}
### APPROACH USED:
````
touch x.sh
nano x.sh
bash x.sh
````
Shell scripts are files containing sequences of bash commands that can be executed together. We create a file called `x.sh` containing the commands `/challenge/pwn` and `/challenge/college`. When we run `bash x.sh`, the commands inside the file are executed sequentially and we get the flag.

## REDIRECTING SCRIPT OUTPUT
### FLAG: pwn.college{IGhSuGFxCraHh3fxhXTJAGvebUI.dhTM5QDLycTN0czW}
### APPROACH USED:
````
touch script.sh
nano script.sh
bash script.sh | /challenge/solve
````
Shell script output can be redirected or piped just like any command. We create a file called `script.sh` containing the commands `/challenge/pwn` and `/challenge/college`. When we bash this file, the commands inside are executed and the combined output is piped into the `/challenge/solve` program using the `|` operator.

## EXECUTABLE SHELL SCRIPTS
### FLAG: pwn.college{ocPV9sbcbTDBNtSaUFPNRbNvgxf.dRzNyUDLycTN0czW}
### APPROACH USED:
````
touch exec.sh
nano exec.sh
chmod ugo+x exec.sh
./exec.sh
````
Shell scripts can be made directly executable using `chmod` to set execute permissions. We create a file called `exec.sh` containing the command `/challenge/solve`. The `chmod ugo+x exec.sh` command makes this file executable by all users. When we execute the program with `./exec.sh` from our home directory, we get the flag without needing to prefix it with `bash`.

## UNDERSTANDING SHEBANGS
### FLAG: pwn.college{8u4hr_gGwEgWeEoE6moC7hl0Qqi.QX5MzM4EDLycTN0czW}
### APPROACH USED:
```
echo '#!/bin/bash' > /home/hacker/solve.sh
echo 'echo "hack the planet"' >> /home/hacker/solve.sh
chmod a+x /home/hacker/solve.sh
/challenge/run
```
The shebang `#!/bin/bash` is the first line in a script that tells the system which interpreter to use. When a script starts with `#!/bin/bash`, the system knows to execute it using the bash shell. This allows the script to run as `./script.sh` instead of requiring `bash script.sh`.

## SCRIPTING WITH ARGUMENTS
### FLAG: pwn.college{cPAcBCjvCa-1LS0hcMx3JjFQGsy.QX1MzM4EDLycTN0czW}
### APPROACH USED:
```
cat > /home/hacker/solve.sh << 'EOF'
#!/bin/bash
echo "$2 $1"
EOF
chmod a+x /home/hacker/solve.sh
/challenge/run
```
Shell scripts can access command-line arguments using positional parameters: `$1` for the first argument, `$2` for the second, and so on. `$0` contains the script name itself. This script reverses two arguments by printing `$2` before `$1`.

## SCRIPTING WITH CONDITIONALS
### FLAG: pwn.college{siE2ODRCsYFcXg6Ue4B0fW7u0-N.QX2MzM4EDLycTN0czW}
### APPROACH USED:
```
cat > /home/hacker/solve.sh << 'EOF'
#!/bin/bash
if [ "$1" == "pwn" ]
then
    echo "college"
fi
EOF
chmod a+x /home/hacker/solve.sh
/challenge/run
```
Bash conditionals use `if [ condition ]; then ... fi` syntax for decision-making. The `[ ]` brackets perform test operations, and `==` checks string equality. The condition must be followed by `then` and closed with `fi`. This allows scripts to execute different code based on input or conditions.

## SCRIPTING WITH DEFAULT CASES
### FLAG: pwn.college{c0rOAoClk_XyX80VpSwlBJJwL_7.QX3MzM4EDLycTN0czW}
### APPROACH USED:
```
cat > /home/hacker/solve.sh << 'EOF'
#!/bin/bash
if [ "$1" == "pwn" ]
then
    echo "college"
else
    echo "nope"
fi
EOF
chmod a+x /home/hacker/solve.sh
/challenge/run
```
The `else` clause provides a default action when the `if` condition is false. This creates a binary decision structure: if the condition matches, execute the `then` block; otherwise, execute the `else` block. This is essential for handling unexpected or invalid inputs.

## SCRIPTING WITH MULTIPLE CONDITIONS
### FLAG: pwn.college{I7a9g4NrL3VG8fQUU-p2oNkiLT2.QX4MzM4EDLycTN0czW}
### APPROACH USED:
```
cat > /home/hacker/solve.sh << 'EOF'
#!/bin/bash
if [ "$1" == "hack" ]
then
    echo "the planet"
elif [ "$1" == "pwn" ]
then
    echo "college"
elif [ "$1" == "learn" ]
then
    echo "linux"
else
    echo "unknown"
fi
EOF
chmod a+x /home/hacker/solve.sh
/challenge/run
```
The `elif` (else-if) clause allows checking multiple conditions sequentially. Bash evaluates each condition in order until one matches or reaches the `else` block. This creates a multi-way decision structure without nesting multiple `if` statements.

## READING SHELL SCRIPTS
### FLAG: pwn.college{YBEOalF1DfJ96OKhPP6OeFBJhn7.QXyADO4EDLycTN0czW}
### APPROACH USED:
```
cat /challenge/run
/challenge/run
hack the PLANET
```
Understanding how to read and analyze shell scripts is crucial for debugging and reverse-engineering challenges. By examining `/challenge/run`, I discovered it uses the `read` command to get user input and compares it against "hack the PLANET". The `read GUESS` command stores user input in the variable `GUESS`, which is then checked in the conditional statement.

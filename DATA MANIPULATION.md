# DATA MANIPULATION

## TRANSLATING CHARACTERS
### FLAG: pwn.college{QM8nsWFuNDxn7EJkuV_XTnNIwyb.QXzETM3EDLycTN0czW}
### APPROACH USED
```
challenge/run | tr abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz
```
The `tr` command performs character-by-character translation using one-to-one mapping. In this case, it swaps the case of all alphabetic characters - converting lowercase letters to uppercase and vice versa.

## DELETING CHARACTERS
### FLAG: pwn.college{8qafLxnSR3nYjRP7P4HE12C-og9.QX0ETM3EDLycTN0czW}
### APPROACH USED
```
/challenge/run | tr -d ^%
```
The `-d` flag in `tr` removes specified characters from the input stream. Here, it deletes all occurrences of `^` and `%` characters from the output.

## DELETING NEWLINES
### FLAG: pwn.college{0zFQK3HaY2CV_6vlMSb1dPZDxBX.QX1ETM3EDLycTN0czW}
### APPROACH USED
```
/challenge/run | tr -d "\n"
```
The newline character `\n` can be targeted by `tr` for deletion. This command removes all line breaks, joining the entire output into a single continuous line.

## EXTRACTING THE FIRST LINES WITH HEAD
### FLAG: pwn.college{8Wfv1fKytiuhZjHEd_is68p8MxN.QX2ETM3EDLycTN0czW}
### APPROACH USED
```
/challenge/pwn | head -n 7 | /challenge/college
```
The `head` command extracts lines from the beginning of input. Using the `-n` flag followed by a number specifies exactly how many initial lines to retrieve. In this pipeline, the first 7 lines are extracted and passed to the next command.

## EXTRACTING SPECIFIC SECTIONS OF TEXT
### FLAG: pwn.college{o7a8hh2NrUpez_p7mTEwflBC4PK.QX3ETM3EDLycTN0czW}
### APPROACH USED
```
echo $(/challenge/run)
/challenge/run | cut -d ' ' -f2,4,6,8,10,12,14,16,18,20 | tr -d "\n"
```
The `cut` command extracts specific columns from delimited text. The `-d` flag sets the delimiter (space in this case), while `-f` specifies which field numbers to keep. By selecting only the even-numbered fields and removing newlines, the flag is reconstructed.

## SORTING DATA
### FLAG: pwn.college{gxnncL6ALQ3X4033F2zF8bhILrX.QXwQzM4EDLycTN0czW}
### APPROACH USED
```
sort /challenge/flags.txt
```
The `sort` command arranges lines in alphabetical order by default. Additional options include `-r` for reverse order, `-n` for numerical sorting, `-u` for unique lines only, and `-R` for random ordering. The flag appeared at the end of the sorted output.

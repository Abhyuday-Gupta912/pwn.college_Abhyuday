# UNTANGLING USERS

## BECOMING ROOT WITH SE
### FLAG: pwn.college{URVXGu5iRmRt0IiKsYcarSYAJYY.dVTN0UDLycTN0czW}
### APPROACH USED: 
````
su
hack-the-planet
ls -l
cat not-the-flag
````

## OTHER USERS WITH SU
### FLAG: pwn.college{UKJm0wEFGRMpCuhMmT2MV-N7vW8.dZTN0UDLycTN0czW}
### APPROACH USED:
````
su zardus
dont-hack-me
/challenge/run
````

## CRACKING PASSWORDS
### FLAG: pwn.college{cpp60qi81dENjAYJshQajM7yRZE.ddTN0UDLycTN0czW}
### APPROACH USED:
````
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:08 76% 1/3 0g/s 251.3p/s 251.3c/s 251.3C/s 9999945..Z9999932
aardvark         (zardus)
1g 0:00:00:22 100% 2/3 0.04393g/s 255.8p/s 255.8c/s 255.8C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{cpp60qi81dENjAYJshQajM7yRZE.ddTN0UDLycTN0czW}
````

## USING SUDO
### FLAG: pwn.college{Qjkgh01Fr3vw62ZZsJuDv_GC7P_.dhTN0UDLycTN0czW}
### APPROACH USED:
````
sudo cat /flag
````
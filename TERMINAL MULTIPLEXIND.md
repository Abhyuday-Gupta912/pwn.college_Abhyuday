# TERMINAL MULTIPLEXING

## LAUNCHING SCREEN
### FLAG: pwn.college{4QmRqXTlagQA2wtRl7kKpl3C0da.QX1gjM4EDLycTN0czW}
### APPROACH USED:
```
screen
pressing ctrl+A then D
```
The `screen` command launches a terminal multiplexer that allows multiple virtual terminals within a single session. The key combination `Ctrl+A` followed by `D` detaches from the screen session while keeping it running in the background.

## DETACHING AND ATTACHING
### FLAG: pwn.college{8bmUJ8yk465utHIFikMZMdzXbkK.QX2gjM4EDLycTN0czW}
### APPROACH USED:
```
screen
pressing ctrl+A then D
screen -r
```
After detaching from a screen session using `Ctrl+A` then `D`, the `screen -r` command reattaches to the most recently detached session. This allows you to resume work exactly where you left off, with all programs still running.

## FINDING SESSIONS
### FLAG: pwn.college{8w9XE0EWO2mTbewHdmBdDP-zVN_.QX3gjM4EDLycTN0czW}
### APPROACH USED:
```
screen -ls
screen -r 155
ctrl+a then d
```
The `screen -ls` command lists all active screen sessions with their session IDs. To reattach to a specific session when multiple exist, use `screen -r` followed by the session ID number. This is essential when managing multiple concurrent screen sessions.

## SWITCHING WINDOWS
### FLAG: pwn.college{oHOnpfWLsInHFNu57VoQc6IC4Qf.QX4gjM4EDLycTN0czW}
### APPROACH USED: 
```
screen -r
ctrl+A then 0
```
Within a screen session, multiple windows can be created and switched between. The key combination `Ctrl+A` followed by a window number (like `0`) switches to that specific window, allowing multitasking within a single screen session.

## DETACHING AND ATTACHING (TMUX)
### FLAG: pwn.college{8lFd1xJ4-fk_JbtIZ44jvyqozYB.QX5gjM4EDLycTN0czW}
### APPROACH USED:
```
tmux
ctrl+B then d
tmux a
```
`tmux` is an alternative terminal multiplexer with similar functionality to screen. The `Ctrl+B` then `D` combination detaches from a tmux session, while `tmux a` (short for `tmux attach`) reattaches to the most recent session. Note that tmux uses `Ctrl+B` as its prefix key instead of screen's `Ctrl+A`.

## SWITCHING WINDOWS (TMUX)
### FLAG: pwn.college{0-O1pLuVYDMYl0Gc04Zg30pw_JT.QXwkjM4EDLycTN0czW}
### APPROACH USED:
```
tmux a
ctrl+b then 0
```
Similar to screen, tmux supports multiple windows within a session. The key combination `Ctrl+B` followed by a window number switches between windows. Window 0 is typically the first window created in a tmux session.

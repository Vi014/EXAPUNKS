# 3: Deadlock's Domain (Deadlock)

<div align="center"><img src="EXAPUNKS - Deadlock's Domain (deadlock, 2023-10-08-00-00-50).gif" /></div>

## Instructions
> To win this battle you must grab files as they spawn in the central hosts and bring them back to your host. 
> 
> Reading the #FILE register will tell you the ID of the most recently created file currently in that host.
> 
>      Gain one point for every file you bring back to your host.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
MARK ASDF
REPL J0
REPL J1
REPL J2
JUMP ASDF
MARK J0
LINK 800
GRAB #FILE
LINK -1
LINK -1
HALT
MARK J1
LINK 801
GRAB #FILE
LINK -1
LINK -1
HALT
MARK J2
LINK 802
GRAB #FILE
LINK -1
LINK -1
HALT
```


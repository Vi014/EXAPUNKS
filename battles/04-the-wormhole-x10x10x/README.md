# 4: The Wormhole (X10X10X)

<div align="center"><img src="EXAPUNKS - The Wormhole (x10x10x, 2023-10-08-00-05-27).gif" /></div>

## Instructions
> To win this battle you must fill the network's hosts with as many of your EXAs as you can. Note that each pair of test runs has its own unique network layout, with bi-directional links between hosts that use the prime numbers between 2 and 13 as link IDs (2, 3, 5, 7, 11, and 13).
> 
>      Gain one point for every EXA you control in the network at the end of the battle.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
REPL L2
REPL L3
REPL L5
REPL L7
REPL L11
REPL L13
JUMP L0
MARK L2
LINK 2
;REPL L2
REPL L3
REPL L5
REPL L7
REPL L11
REPL L13
JUMP L0
MARK L3
LINK 3
REPL L2
;REPL L3
REPL L5
REPL L7
REPL L11
REPL L13
JUMP L0
MARK L5
LINK 5
REPL L2
REPL L3
;REPL L5
REPL L7
REPL L11
REPL L13
JUMP L0
MARK L7
LINK 7
REPL L2
REPL L3
REPL L5
;REPL L7
REPL L11
REPL L13
JUMP L0
MARK L11
LINK 11
REPL L2
REPL L3
REPL L5
REPL L7
;REPL L11
REPL L13
JUMP L0
MARK L13
LINK 13
REPL L2
REPL L3
REPL L5
REPL L7
REPL L11
;REPL L13
JUMP L0
MARK L0
REPL L0
JUMP L0
```


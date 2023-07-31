# 5: Aberdeen (selenium_wolf)

<div align="center"><img src="EXAPUNKS - Aberdeen (selenium _wolf, 2023-07-31-12-30-31).gif" /></div>

## Instructions
> To win this battle you must occupy a majority of the hosts for as long as possible. You occupy a host if you have more EXAs in it than your opponent.
> 
>      Gain one point every cycle you occupy more hosts than your opponent.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> Writing any value to the #NUKE register will destroy all EXAs in that host, including the EXA that triggered it.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
LINK 801
LINK 799
TEST M = 1
```

### [XC](XC.exa) (global)
```asm
LINK 800
LINK 802
LINK 800
LINK 799
TEST M = 1
```

### [XB](XB.exa) (global)
```asm
LINK 800
MARK REP
REPL NUKE
JUMP REP
MARK NUKE
LINK 800
COPY 1 #NUKE
```

### [XD](XD.exa) (global)
```asm
LINK 800
LINK 802
TEST M = 1
```

### [XE](XE.exa) (global)
```asm
LINK 800
LINK 802
TEST M = 1
```

### [XF](XF.exa) (global)
```asm
LINK 800
LINK 801
LINK 800
TEST M = 1
```

### [XG](XG.exa) (global)
```asm
LINK 800
LINK 801
LINK 800
TEST M = 1
```

### [XH](XH.exa) (global)
```asm
LINK 800
LINK 801
TEST M = 1
```

### [XI](XI.exa) (global)
```asm
LINK 800
LINK 802
LINK 800
TEST M = 1
```


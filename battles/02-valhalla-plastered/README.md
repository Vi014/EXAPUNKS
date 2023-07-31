# 2: Valhalla (=Plastered)

<div align="center"><img src="EXAPUNKS - Valhalla (=plastered, 2023-07-31-12-21-54).gif" /></div>

## Instructions
> To win this battle you must control a majority of the hosts for as long as possible. 
> 
> To take control of a host, write any value to its #CTRL register. Reading from a #CTRL register will tell if you (1) or your opponent (-1) controls the host.
> 
>      Gain one point every cycle you control more hosts than your opponent.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
LINK -1
MARK ASDF
COPY 1 #CTRL
JUMP ASDF
```

### [XB](XB.exa) (global)
```asm
LINK 800
MARK ASDF
COPY 1 #CTRL
JUMP ASDF
```

### [XC](XC.exa) (global)
```asm
LINK 800
LINK -1
MARK ASDF
COPY 1 #CTRL
JUMP ASDF
```

### [XD](XD.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
MARK ASDF
COPY 1 #CTRL
JUMP ASDF
```

### [XE](XE.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
LINK 800
MARK ASDF
COPY 1 #CTRL
JUMP ASDF
```

### [XF](XF.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
MARK ASDF
COPY 1 #CTRL
JUMP ASDF
```

### [XG](XG.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
MARK ASDF
COPY 1 #CTRL
JUMP ASDF
```

### [XH](XH.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
MARK ASDF
COPY 1 #CTRL
JUMP ASDF
```

### [XI](XI.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
LINK 800
MARK ASDF
COPY 1 #CTRL
JUMP ASDF
```


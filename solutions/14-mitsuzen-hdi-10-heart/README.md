# 14: Mitsuzen HDI-10 (Heart)

<div align="center"><img src="EXAPUNKS - KGOG-TV (mutex8021, 2023-05-19-15-05-38).gif" /></div>

## Instructions
> Read a value from the nerve connected to your central nervous system (CNS) and make your heart beat by writing a sequence of values to your sinoatrial (SA-N) and atrioventricular (AV-N) nodes as indicated in the HDI-10 I/O log when holding the "SHOW GOAL" button. The length of each sequence of values should be equal to the value from the CNS divided by -10. Repeat _ad infinitum_.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [C](C.exa) (global)
```asm
LINK 800
MARK LOOP
DIVI #NERV -10 X
COPY X M
COPY X M
JUMP LOOP
```

### [S](S.exa) (global)
```asm
LINK 800
LINK 1
LINK 1
MARK LOOP
COPY M T
COPY 40 #NERV
SUBI T 1 T
FJMP LOOP
MARK LOOP2
COPY -70 #NERV
SUBI T 1 T
TJMP LOOP2
JUMP LOOP
```

### [A](A.exa) (global)
```asm
LINK 800
LINK 3
LINK 3
MARK LOOP
COPY M T
COPY -70 #NERV
SUBI T 1 T
FJMP LOOP
COPY 40 #NERV
SUBI T 1 T
FJMP LOOP
MARK LOOP2
COPY -70 #NERV
SUBI T 1 T
TJMP LOOP2
JUMP LOOP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 107    | 35   | 7        |

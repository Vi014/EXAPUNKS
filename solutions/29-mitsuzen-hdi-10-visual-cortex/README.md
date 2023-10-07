# 29: Mitsuzen HDI-10 (Visual Cortex)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (402, 63, 12, 2023-10-08-00-08-13).gif" /></div>

## Instructions
> Read a value from each of the optic nerves present and write the correct value to the nerve that runs deeper into your visual cortex (V-CTX). To determine the value that should be written, count the number of values read that are greater than -55, multiply that count by 5, and then subtract 75. Repeat _ad infinitum_.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
REPL R0
REPL R1
JUMP LOOP
MARK R0
LINK 1
REPL R2
REPL R3
JUMP LOOP
MARK R1
LINK -3
REPL R4
JUMP LOOP
MARK R2
LINK 1
REPL R5
JUMP LOOP
MARK R3
LINK -3
JUMP LOOP
MARK R4
LINK -3
REPL R6
JUMP LOOP
MARK R5
LINK -3
REPL R7
JUMP LOOP
MARK R6
LINK 1
JUMP LOOP
MARK R7
LINK -3
JUMP LOOP
MARK LOOP
COPY 3 T
MARK WAIT
SUBI T 1 T
TJMP WAIT
MARK LOOP2
TEST #NERV > -55
MULI T 5 M
COPY 4 T
MARK WAIT2
SUBI T 1 T
TJMP WAIT2
JUMP LOOP2
```

### [XB](XB.exa) (global)
```asm
LINK 800
LINK 1
LINK 3
MARK LOOP
@REP 9
ADDI X M X
@END
SUBI X 75 #NERV
COPY 0 X
JUMP LOOP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 402    | 63   | 12       |

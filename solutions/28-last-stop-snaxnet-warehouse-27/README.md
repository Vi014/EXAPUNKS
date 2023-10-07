# 28: Last Stop Snaxnet (Warehouse 27)

<div align="center"><img src="EXAPUNKS - Last Stop SNAXNET (421, 98, 26, 2023-10-08-00-07-54).gif" /></div>

## Instructions
> An array of five Zippe-type gas centrifuges, ZGC0 through ZGC4, are connected in a cascade configuration.
> 
> Read each of the #ZGCX registers and determine which centrifuge currently has the highest pressure. Then disable that centrifuge's regulator by writing a value of 0 to its #POWR register. Repeat this process until all five regulators have been disabled.

## Solution

### [XA](XA.exa) (local)
```asm
LINK 800
LINK 799
MARK START
@REP 5
TEST #ZGC@{0,1} = 0
FJMP NOTYET
@END
COPY -1 M
COPY -1 M
HALT
MARK NOTYET
MAKE
@REP 5
COPY @{1,1} F
COPY #ZGC@{0,1} F
@END
SEEK -9999
COPY F M
SEEK -1
COPY F M
COPY F X
MARK FIND
TEST EOF
TJMP SMTH
SEEK 1
TEST F > X
TJMP COPY
JUMP FIND
MARK COPY
SEEK -2
COPY F M
SEEK -1
COPY F M
COPY F X
JUMP FIND
MARK SMTH
COPY 0 M
COPY 0 M
SEEK -9999
MARK REM
SEEK 1
TEST F = X
FJMP REM
SEEK -2
VOID F
VOID F
WIPE
JUMP START
MARK ALLDONE
```

### [XB](XB.exa) (local)
```asm
LINK 800
LINK 799
MARK LOOP
TEST M < 1
TJMP NEXT
COPY M X
JUMP LOOP
MARK NEXT
TEST M = -1
MODE
TJMP END
COPY X M
MODE
JUMP LOOP
MARK END
COPY 0 M
```

### [XC](XC.exa) (global)
```asm
LINK 800
LINK 798
MARK WAIT
COPY M X
TEST X = 0
TJMP END
SUBI X 1 T
MARK FIND
FJMP DISABLE
LINK 800
SUBI T 1 T
JUMP FIND
MARK DISABLE
COPY 0 #POWR
SUBI X 1 T
MARK BACK
FJMP WAIT
LINK -1
SUBI T 1 T
JUMP BACK
MARK END
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 421    | 98   | 26       |

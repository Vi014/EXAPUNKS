# 16: TEC Redshift (Development Kit)

<div align="center"><img src="EXAPUNKS - TEC Redshift™ (11902, 37, 4, 2023-07-31-12-15-14).gif" /></div>

## Instructions
> There is an unknown three-digit code (such as 4-7-3) that, when entered one digit at a time into #PASS, will unlock the link between *debug* and *secret*. Find the three-digit code and create a file in your host that contains the code as a sequence of three values, followed by the development kit's RDK ID.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
MAKE
COPY 0 X
MARK LOOP1
COPY 10 T
MARK LOOP2
SUBI T 1 T
@REP 10
WIPE
MAKE
COPY X #PASS
COPY T #PASS
COPY @{0,1} F
COPY T F
COPY @{0,1} #PASS
TEST MRD
TJMP WRITE
SEEK -1
COPY F T
@END
TJMP LOOP2
ADDI X 1 X
TEST X > 9
FJMP LOOP1
MARK WRITE
VOID M
COPY X M
SEEK -1
COPY F M
SEEK -2
COPY F M
WIPE
HALT
```

### [XB](XB.exa) (global)
```asm
LINK 800
MARK TRYLINK
NOOP
TEST MRD
TJMP END
REPL TRYLINK
LINK 800
COPY 1 M
GRAB 199
@REP 12 
NOOP
@END
COPY F M
MARK END
HALT
```

### [XC](XC.exa) (global)
```asm
MAKE
MARK ASDF
TEST MRD
FJMP ASDF
@REP 14
NOOP
@END
COPY M F
COPY M F
SUBI M 1 X
TEST X = -1
TJMP OOPS
COPY X F
MARK UNOOPS
COPY M F
HALT
MARK OOPS
SEEK -1
COPY F X
TEST X = 9
TJMP OOPS2
SEEK -1
ADDI X 1 F
COPY 9 F
JUMP UNOOPS
MARK OOPS2
SEEK -2
COPY F X
SEEK -1
SUBI X 1 F
COPY 0 F
COPY 9 F
JUMP UNOOPS
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 11162  | 198  | 3        |

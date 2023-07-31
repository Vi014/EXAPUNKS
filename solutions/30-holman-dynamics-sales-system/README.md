# 30: Holman Dynamics (Sales System)

<div align="center"><img src="EXAPUNKS - UNKNOWN NETWORK 2 (429, 32, 56, 2023-05-19-15-38-04).gif" /></div>

## Instructions
> Create a file in your host containing the contiguous 16-value sequence from the garbage file (file 199) that is a valid credit card number. There will be exactly one such sequence.
> 
> For more information see "How to Validate Credit Card Numbers" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
LINK 802
LINK 799
GRAB 199

VOID M

MARK INIT1
SEEK -15
MARK INIT2
COPY 0 X

MARK LOOP
TEST F = -9999
TJMP INIT2
ADDI X 1 X
TEST X = 16
FJMP LOOP

SEEK -16

COPY 16 T
MARK LOOP2
COPY F M
SUBI T 1 T
TJMP LOOP2

TEST M = -1
TJMP INIT1
SEEK -16
COPY 16 T
MARK LOOP3
COPY F M
SUBI T 1 T
TJMP LOOP3
```

### [XB](XB.exa) (global)
```asm
MAKE

MARK START
WIPE
MAKE
COPY -1 M
COPY 16 T

MARK LOOP
COPY M F
SUBI T 1 T
TJMP LOOP

SEEK -9999

MARK LOOP2
MULI F 2 X
TEST X > 9
TJMP SUBT
MARK BACK
SEEK -1
COPY X F
SEEK 1
TEST EOF
FJMP LOOP2

COPY 0 X
SEEK -9999

MARK LOOP3
ADDI X F X
TEST EOF
FJMP LOOP3

SWIZ X 1 X
TEST X = 0
FJMP START
COPY 1 M
COPY 16 T
WIPE
MAKE
MARK LOOP4
COPY M F
SUBI T 1 T
TJMP LOOP4
HALT

MARK SUBT
SUBI X 9 X
JUMP BACK
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 12837  | 71   | 3        |

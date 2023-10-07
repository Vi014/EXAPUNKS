# 31: US Government (Fema Genetic Database)

<div align="center"><img src="EXAPUNKS - UNKNOWN NETWORK 2 (429, 32, 56, 2023-10-08-00-12-19).gif" /></div>

## Instructions
> ﻿Overwrite the genetic sequence of ‗SEN WALKER CAINE JR‗ with the genetic sequence of ‗PRES WALKER CAINE‗ so that it looks like the younger politician is actually a clone of the older politician.
> 
> The names of these two politicians are available in file 300.
> 
> Note that you may need to overwrite a data chunk with another data chunk from the same file.
> 
> For more information see "Accessing Data in Legacy Storage Systems" in the first issue of the zine.

## Solution

### [XA](XA.exa) (local)
```asm
GRAB 300
COPY F X
DROP
LINK 800



MARK START
LINK 801
GRAB 200
TEST F = X
TJMP GETCHUNK
MARK FIND
SEEK 10
TEST F = X
FJMP FIND
MARK GETCHUNK
COPY M X
ADDI X 1 M
TEST X = 10
TJMP NEXT
SEEK X
COPY F X

MODE
DROP
LINK -1
SWIZ X 3 T
ADDI T 800 T
LINK T
SWIZ X 2 T
ADDI T 200 T
GRAB T
SWIZ X 1 T
MULI T 10 T
SEEK T

COPY 10 T
MARK LOOP
COPY F M
SUBI T 1 T
TJMP LOOP

DROP
LINK -1
GRAB 300
COPY F X
DROP
MODE
JUMP START



MARK NEXT
MODE
COPY 0 M
MODE
DROP
LINK -1
GRAB 300
SEEK 1
COPY F X
DROP



MARK START2
LINK 801
GRAB 200
TEST F = X
TJMP GETCHUNK2
MARK FIND2
SEEK 10
TEST F = X
FJMP FIND2
MARK GETCHUNK2
COPY M X
ADDI X 1 M
TEST X = 10
TJMP END
SEEK X
COPY F X

MODE
DROP
LINK -1
SWIZ X 3 T
ADDI T 800 T
LINK T
SWIZ X 2 T
ADDI T 200 T
GRAB T
SWIZ X 1 T
MULI T 10 T
SEEK T

COPY 10 T
MARK LOOP2
COPY M F
SUBI T 1 T
TJMP LOOP2

DROP
LINK -1
GRAB 300
SEEK 1
COPY F X
DROP
MODE
JUMP START2

MARK END
DROP
LINK -1
GRAB 300
WIPE
```

### [XB](XB.exa) (local)
```asm
NOOP
NOOP
GRAB 300
LINK 800
DROP
LINK 801
MARK LOOP
COPY X M
COPY M X
TEST X = 11
FJMP LOOP
COPY 0 X
REPL LOOP2
HALT
MARK LOOP2
COPY X M
COPY M X
TEST X = 11
FJMP LOOP2
```

### [XC](XC.exa) (global)
```asm
MAKE
MARK GET
COPY M X
TEST X = 0
TJMP GIVE
COPY X F
JUMP GET

MARK GIVE
SEEK -9999
MARK LOOP
COPY F M
TEST EOF
FJMP LOOP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 2042   | 132  | 87       |

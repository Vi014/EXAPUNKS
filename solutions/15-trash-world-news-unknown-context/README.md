# 15: Trash World News (Unknown Context)

<div align="center"><img src="EXAPUNKS - TRASH WORLD NEWS (1920, 47, 4, 2023-07-31-12-14-43).gif" /></div>

## Instructions
> ﻿Find and replace the keywords in the target message (file 212) as directed by EMBER-2.
> 
> A list of keyword pairs indicating which words should be found and what they should be replaced with is available in file 300. For example, the keyword ‗AI‗ should be replaced with the keyword ‗COLLECTIVE‗. Each keyword will only occur once, but may occur in any order.
> 
> Also, move file 200 to the *outbox*.

## Solution

### [XB](XB.exa) (global)
```asm
LINK 800
LINK 799
GRAB 212
COPY M X

MARK READFILE
TEST F = X
FJMP TESTEND

COPY 1 M
SEEK -1
COPY M F
COPY M X
TEST EOF
TJMP NEXTWORD
FJMP READFILE

MARK TESTEND
TEST EOF
TJMP NEXTWORD
FJMP READFILE

MARK NEXTWORD
COPY 2 M
COPY M X
SEEK -9999
TEST X = 1
FJMP READFILE

HALT
```

### [XC](XC.exa) (global)
```asm
LINK 800
GRAB 200
LINK 800
HALT
```

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F M

MARK WAIT
TEST M = 1
FJMP GETNEWWORD

COPY F M
SEEK -2
COPY F M
JUMP WAIT

MARK GETNEWWORD
SEEK 1
TEST EOF
TJMP END

COPY F M
JUMP WAIT

MARK END
COPY 1 M
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 1920   | 47   | 4        |

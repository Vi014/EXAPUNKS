# 11: UC Berkeley (EECS Department)

<div align="center"><img src="EXAPUNKS - UC Berkeley (424, 36, 7, 2023-10-07-23-43-32).gif" /></div>

## Instructions
> ﻿Locate the specified host (either *tape-1*, *tape-2*, or *tape-3*), and then locate the specified entry (‗ПАСЬЯНС‗) in the tape backup file in that host (file 200). Create a file in your host containing the entry's data.
> 
> The names of the target host and entry are available in file 300.
> 
> For more information see "Accessing Data in Legacy Storage Systems" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F X
MARK SEARCH
LINK 800
HOST T
TEST T = X
FJMP SEARCH
COPY F X
WIPE
GRAB 200
MARK SEARCH2
TEST F = X
FJMP SEARCH2
COPY F T
COPY F X
SEEK -9999
SEEK T
COPY 1 M
MARK TRANS_SV
COPY F M
SUBI X 1 X
TEST X = 0
FJMP TRANS_SV
COPY -1 M
DROP
HALT
```

### [XB](XB.exa) (global)
```asm
MAKE
TEST M = 1
MARK TRANS_HM
COPY M X
TEST X = -1
FJMP COPY
HALT
MARK COPY
COPY X F
JUMP TRANS_HM

```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 424    | 36   | 7        |

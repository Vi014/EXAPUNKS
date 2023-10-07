# 26: Equity First Bank (San Francisco - ATMs Offline)

<div align="center"><img src="EXAPUNKS - Equity First Bank (446, 70, 6, 2023-10-08-00-05-00).gif" /></div>

## Instructions
> ﻿Move EMBER-2's new account (file 300) into *checking*. Then iterate over the checking accounts listed in the directory (file 199) and, in that order, transfer $1.00 from each target account to EMBER-2's account. Finally, add the file ID of EMBER-2's account file to the end of the directory.
> 
> The keywords ‗CREDIT‗ and ‗DEBIT‗ are available in file 301.
> 
> For more information see "Network Exploration: Equity First Bank" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
LINK 800
```

### [XB](XB.exa) (global)
```asm
GRAB 301
LINK 800
LINK 800
DROP
MARK WAIT
COPY M X
TEST X = -1
TJMP END
COPY X M
JUMP WAIT
MARK END
GRAB 301
WIPE
```

### [XC](XC.exa) (global)
```asm
LINK 800
LINK 800
MARK LIST
GRAB 199
SEEK X
TEST EOF
TJMP END
COPY F T
DROP
GRAB T
COPY F T
DROP
GRAB 300
SEEK 9999
COPY T F
DROP
GRAB 301
COPY F T
DROP
GRAB 300
SEEK 9999
COPY T F
COPY 1 F
COPY 0 F
SEEK -9999
COPY F T
DROP
GRAB 199
SEEK X
COPY F M
DROP
GRAB M
SEEK 9999
COPY T F
DROP
GRAB 301
SEEK 1
COPY F T
DROP
GRAB 199
SEEK X
COPY F M
DROP
GRAB M
SEEK 9999
COPY T F
COPY 1 F
COPY 0 F
DROP
ADDI X 1 X
JUMP LIST
MARK END
COPY 300 F
COPY -1 M
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 446    | 70   | 6        |

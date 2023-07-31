# 26: Equity First Bank (San Francisco (ATMs Offline)

<div align="center"><img src="EXAPUNKS - TEC EXA-Blaster� Modem (2877, 57, 18, 2023-05-19-15-24-17).gif" /></div>

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
MARK WAIT
COPY M X
TEST X = 1
TJMP DEBIT
NOOP
JUMP WAIT
MARK DEBIT
SEEK 9999
COPY M F
@REP 3
COPY 2 M
@END
COPY M F
COPY 1 F
COPY 0 F
SEEK -9999
@REP 3
COPY 3 M
@END
@REP 3
COPY F M
SEEK -1
@END
JUMP WAIT
```

### [XB](XB.exa) (global)
```asm
LINK 800
LINK 800
GRAB 199
MARK FILE
TEST EOF
TJMP ITSJOEVER
@REP 3
COPY 0 M
@END
@REP 3
COPY F M
SEEK -1
@END
MARK WAIT
COPY M X
TEST X = 5
TJMP FILE
JUMP WAIT
MARK ITSJOEVER
```

### [XC](XC.exa) (global)
```asm
LINK 800
LINK 800
MARK WAIT
COPY M X
TEST X = 0
TJMP GRAB
TEST X = 3
TJMP CREDIT
JUMP WAIT
MARK GRAB
GRAB M
@REP 3
COPY 1 M
@END
@REP 3
COPY F M
SEEK -1
@END
JUMP WAIT
MARK CREDIT
SEEK 9999
COPY M F
@REP 3
COPY 4 M
@END
COPY M F
COPY 1 F
COPY 0 F
DROP
@REP 3
COPY 5 M
@END
JUMP WAIT
```

### [XD](XD.exa) (global)
```asm
GRAB 301
MARK WAIT
COPY M X
TEST X = 2
TJMP DEBIT
TEST X = 4
TJMP CREDIT
JUMP WAIT
MARK DEBIT
SEEK 1
@REP 3
COPY F M
SEEK -1
@END
SEEK -1
JUMP WAIT
MARK CREDIT
@REP 3
COPY F M
SEEK -1
@END
JUMP WAIT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 0      | 0    | 0        |

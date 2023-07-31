# 24: King's Ransom Online (US West Realm)

<div align="center"><img src="EXAPUNKS - King's Ransom Online (335, 38, 25, 2023-07-31-12-25-57).gif" /></div>

## Instructions
> ﻿Reset the ownership of all castles and sub-buildings to ‗P00000‗ (file 300), the player ID for unowned buildings.
> 
> To ensure that there are no witnesses you must first disconnect all connected players. Terminate every EXA in every host before changing any castle or sub-building files anywhere in the network. If you leave an EXA alive in one host while changing a file in another you will fail the task.
> 
> For more information see "Network Exploration: King's Ransom Online" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F X
WIPE
LINK 800

COPY 5 T
MARK REPL0
REPL CON
SUBI T 1 T
TJMP REPL0

MARK CON
ADDI T 800 T
LINK T
KILL
KILL
KILL

COPY 2 T
MARK NOOP
SUBI T 1 T
TJMP NOOP

COPY 99 T
MARK REPL1
REPL GRAB
SUBI T 1 T
TJMP REPL1
GRAB 200
SEEK 2
COPY X F
MARK END
LINK -1
LINK -1
HALT

MARK GRAB
ADDI T 200 T
GRAB T
SEEK 5
TEST EOF
FJMP END
SEEK -9999
SEEK 2
COPY X F
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 0      | 0    | 0        |

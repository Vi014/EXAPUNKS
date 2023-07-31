# 22: Alliance Power and Light (Streetsmarts GIS Database)

<div align="center"><img src="EXAPUNKS - Alliance Power and Light (36, 50, 20, 2023-07-31-12-23-47).gif" /></div>

## Instructions
> Locate the two hosts with the specified hostnames (file 300), which correspond to the target power grid substations. When you've found them, cut the power by writing a value of 0 to #POWR.
> 
> For more information see "Network Exploration: Geographic Information Systems" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F X
COPY F T
DROP
LINK 800
MARK REPL
REPL NORTH
REPL SOUTH
REPL HERE
LINK 801
JUMP REPL
MARK NORTH
LINK 800
REPL NORTH
MAKE
HOST F
SEEK -1
TEST T = F
TJMP BLACKOUT
SEEK -1
TEST X = F
TJMP BLACKOUT
WIPE
HALT
MARK SOUTH
LINK 802
REPL SOUTH
MAKE
HOST F
SEEK -1
TEST T = F
TJMP BLACKOUT
SEEK -1
TEST X = F
TJMP BLACKOUT
WIPE
HALT
MARK HERE
MAKE
HOST F
SEEK -1
TEST T = F
TJMP BLACKOUT
SEEK -1
TEST X = F
TJMP BLACKOUT
WIPE
HALT
MARK BLACKOUT
COPY 0 #POWR
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 36     | 50   | 20       |

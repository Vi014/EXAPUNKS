# 13: Equity First Bank (San Fancisco)

<div align="center"><img src="EXAPUNKS - Equity First Bank (4007, 34, 10, 2023-07-31-12-14-23).gif" /></div>

## Instructions
> Dispense all available cash from all connected ATMs.
> 
> For more information see "Network Exploration: Equity First Bank" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
REPL L801
REPL L802
REPL L803
REPL L804
REPL L805
REPL L806
LINK 800
JUMP TROLL
MARK L801
LINK 801
JUMP TROLL
MARK L802
LINK 802
JUMP TROLL
MARK L803
LINK 803
JUMP TROLL
MARK L804
LINK 804
JUMP TROLL
MARK L805
LINK 805
JUMP TROLL
MARK L806
LINK 806
MARK TROLL
COPY 20 #DISP
SUBI #CASH 1 #CASH
TEST #CASH = 0
FJMP TROLL
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 4007   | 34   | 10       |

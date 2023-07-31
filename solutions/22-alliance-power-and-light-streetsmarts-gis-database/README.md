# 22: Alliance Power and Light (Streetsmarts GIS Database)

<div align="center"><img src="EXAPUNKS - Alliance Power and Light (36, 50, 20, 2023-07-31-12-23-47).gif" /></div>

## Instructions
> Locate the two hosts with the specified hostnames (file 300), which correspond to the target power grid substations. When you've found them, cut the power by writing a value of 0 to #POWR.
> 
> For more information see "Network Exploration: Geographic Information Systems" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
MARK EXPL
COPY 5 T
REPL ASDF
NOOP
NOOP
COPY 0 #POWR
MARK ASDF
SUBI T 1 T
FJMP AMOGUS
LINK 802
REPL ASDF
NOOP
NOOP
COPY 0 #POWR
MARK AMOGUS
LINK 801
COPY 5 T
REPL ASDF2
NOOP
NOOP
COPY 0 #POWR
MARK ASDF2
SUBI T 1 T
FJMP AMOGUS2
LINK 800
REPL ASDF2
NOOP
NOOP
COPY 0 #POWR
MARK AMOGUS2
LINK 801
JUMP EXPL
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 0      | 0    | 0        |

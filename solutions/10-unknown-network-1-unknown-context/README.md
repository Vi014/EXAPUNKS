# 10: Unknown Network 1 (Unknown Context)

<div align="center"><img src="EXAPUNKS - UNKNOWN NETWORK 1 (29, 23, 27, 2023-10-07-23-43-22).gif" /></div>

## Instructions
> Find file 276 in the network and bring it back to your host.
> 
> Note that an EXA cannot grab a file that is being held by another EXA.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
MARK REPLICATE
ADDI X 1 X
REPL M800
REPL M801
HALT
MARK M800
LINK 800
JUMP TEST
MARK M801
LINK 801
MARK TEST
TEST X = 3
TJMP GRAB
FJMP REPLICATE
MARK GRAB
KILL
GRAB 276
LINK -1
LINK -1
LINK -1
LINK -1
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 29     | 23   | 27       |

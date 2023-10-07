# 4: US Department of Defense (USAF Secure Facility)

<div align="center"><img src="EXAPUNKS - NETronics NET40 Modem (96093, 95, 187, 2023-10-08-00-55-39).gif" /></div>

## Instructions
> ﻿Find the unredacted version of the ‗PROJECT OGRE‗ report (file 300), make a copy of it, and bring the copy back to your host. The target file will be behind one or more locks, which each require a three-digit code.
> 
> Since this task takes place inside a network run by the military it includes additional security features not found in other networks. You may not have more than one EXA in the network at a time, and you may not use the M register to communicate between an EXA in the network and an EXA in your host.

## Solution

### [XA](XA.exa) (global)
```asm
MARK LOOP
LINK 800
COPY X #LOCK
ADDI X 1 X
LINK -1
GRAB 300
COPY F T
DROP
REPL TEST
COPY 2 T
MARK WAIT
SUBI T 1 T
TJMP WAIT
TEST MRD
FJMP LOOP
VOID M
HALT

MARK TEST
LINK 800
LINK 800
LINK -1
LINK -1
COPY 1 M
MARK TESTSHARED
LINK 800
LINK 800
COPY T X
@REP 4
LINK 80@{1,1}
GRAB 200
TEST F = X
TJMP COPY@{1,1}
DROP
LINK -1
@END

COPY 0 X
LINK -1
LINK -1
MARK LOOP2
LINK 800
LINK 800
COPY X #LOCK
ADDI X 1 X
LINK -1
LINK -1
GRAB 300
COPY F T
DROP
REPL TEST2
COPY 3 T
MARK WAIT2
SUBI T 1 T
TJMP WAIT2
TEST MRD
FJMP LOOP2
VOID M
HALT

MARK TEST2
LINK 800
LINK 800
LINK 800
LINK -1
LINK -1
LINK -1
COPY 1 M
LINK 800
JUMP TESTSHARED

@REP 4
MARK COPY@{1,1}
DROP
LINK -1
MAKE
COPY 80@{1,1} F
JUMP COPY
@END
MARK COPY
DROP
COPY 44 T
MAKE
DROP
MARK STEAL
GRAB 400
COPY F X
DROP
LINK X
SUBI 44 T X
GRAB 200
SEEK X
COPY F X
DROP
LINK -1
GRAB 401
SEEK 9999
COPY X F
DROP
SUBI T 1 T
TJMP STEAL
GRAB 400
WIPE
GRAB 401
LINK -1
LINK -1
LINK -1
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 32928  | 135  | 8689     |

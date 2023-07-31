# 32: Unknown Network 2 (Unknown Context)

<div align="center"><img src="EXAPUNKS - UNKNOWN NETWORK 2 (429, 32, 56, 2023-07-31-12-53-38).gif" /></div>

## Instructions
> Terminate all other EXAs and bring any files they were holding back to your host. Only EXAs in the central host will be holding files, and their file IDs will always be between 200 and 299, inclusive.
> 
> Note that some links may become non-traversable as a result of your actions.

## Solution

### [XA](XA.exa) (global)
```asm
@REP 5
LINK 800
@END
@REP 6
KILL
@END
COPY 200 X
MARK LOOP
REPL GRAB
ADDI X 1 X
TEST X = 300
FJMP LOOP

COPY 4 T
MARK LOOP2
LINK -1
REPL LOOP2
KILL
KILL
SUBI T 1 T
TJMP LOOP2

MARK GRAB
GRAB X
@REP 5
LINK -1
@END
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 429    | 32   | 56       |

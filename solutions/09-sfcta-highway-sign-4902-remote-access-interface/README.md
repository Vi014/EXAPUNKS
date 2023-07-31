# 9: SFCTA Highway Sign #4902 (Remote Access Interface)

<div align="center"><img src="EXAPUNKS - UNKNOWN NETWORK 1 (29, 23, 27, 2023-05-19-15-03-02).gif" /></div>

## Instructions
> Write EMBER-2's message (file 300) to the highway sign. The file contains one character value for each position on the sign from left to right, top to bottom.
> 
> For more information see "Hardware Hacks: Electronic Highway Signs" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
MARK LOOP0
COPY 0 #DATA
COPY X #DATA
COPY F #DATA
ADDI X 1 X
TEST X < 9
TJMP LOOP0
COPY 0 X
MARK LOOP1
COPY 1 #DATA
COPY X #DATA
COPY F #DATA
ADDI X 1 X
TEST X < 9
TJMP LOOP1
COPY 0 X
MARK LOOP2
COPY 2 #DATA
COPY X #DATA
COPY F #DATA
ADDI X 1 X
TEST X < 9
TJMP LOOP2
WIPE
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 168    | 26   | 1        |

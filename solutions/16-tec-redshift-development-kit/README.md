# 16: TEC Redshift (Development Kit)

<div align="center"><img src="EXAPUNKS - TEC Redshift™ (11902, 37, 4, 2023-07-31-12-15-14).gif" /></div>

## Instructions
> There is an unknown three-digit code (such as 4-7-3) that, when entered one digit at a time into #PASS, will unlock the link between *debug* and *secret*. Find the three-digit code and create a file in your host that contains the code as a sequence of three values, followed by the development kit's RDK ID.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
COPY -1 X
MARK LOOP
MODE
ADDI X 1 X
SWIZ X 3 #PASS
SWIZ X 2 #PASS
SWIZ X 1 #PASS
COPY 1 M
NOOP
NOOP
MODE
TEST MRD
FJMP LOOP
MAKE
SWIZ X 3 F
SWIZ X 2 F
SWIZ X 1 F
COPY M F
LINK -1
```

### [XB](XB.exa) (local)
```asm
LINK 800
MARK LOOP
MODE
NOOP
TEST MRD
TJMP END
MODE
TEST M = 1
REPL LOOP
LINK 800
MODE
COPY 1 M
GRAB 199
COPY F M
HALT
MARK END
VOID M
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 11902  | 37   | 4        |

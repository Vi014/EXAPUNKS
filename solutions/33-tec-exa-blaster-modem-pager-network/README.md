# 33: TEC EXA-Blaster Modem (Pager Network)

<div align="center"><img src="EXAPUNKS - TEC EXA-Blaster™ Modem (970, 58, 26, 2023-07-31-12-54-09).gif" /></div>

## Instructions
> Connect to each pager and copy EMBER-2's message (file 300) to the screen (#DATA). Then activate all of the pagers at exactly the same time by writing a value to each #PAGE register in the same cycle.
> 
> A list of phone numbers for the pagers is available in file 301.
> 
> For more information see "Hacker Skills: Modem Control at the Direct Level" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 301
LINK 800
MARK DIAL
COPY -1 #DIAL
COPY 11 T
MARK LOOP
COPY F #DIAL
SUBI T 1 T
TJMP LOOP
COPY 1 M
TEST M = 1
TEST EOF
FJMP DIAL

COPY 2 M
SEEK -9999

MARK DIAL2
COPY -1 #DIAL
COPY 11 T
MARK LOOP2
COPY F #DIAL
SUBI T 1 T
TJMP LOOP2
NOOP
COPY 1 M
TEST EOF
FJMP DIAL2
WIPE
```

### [XB](XB.exa) (global)
```asm
GRAB 300
LINK 800
MARK WRITE
TEST M = 1
FJMP END
LINK 800
MARK LOOP
COPY F #DATA
TEST EOF
FJMP LOOP
LINK -1
COPY 1 M
SEEK -9999
JUMP WRITE

MARK END
WIPE
COPY 141 X
MARK REPL
TEST M = 1
REPL ACTIV
SUBI X 20 X
TEST X = -19
FJMP REPL
HALT

MARK ACTIV
;SUBI X 1 T
COPY X T
;DIVI X 19 X
LINK 800
MARK WAIT
SUBI T 1 T
;ADDI T 1 T
TJMP WAIT
COPY 1 #PAGE
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 970    | 58   | 26       |

# 23: Xtreme League Baseball (Player Database)

<div align="center"><img src="EXAPUNKS - Xtreme League Baseball (3916, 53, 1, 2023-07-31-12-24-27).gif" /></div>

## Instructions
> The hosts *active* and *penalty* contain files that correspond to extreme baseball players (files 200-299), along with a directory file that contains a list of those files' IDs (file 199). Each player file contains their name and the following statistics in this order: BA, ZA, APB, WRT, OI, OD, PC, and PS.
> 
> Create a file in your host with the name of the player with the highest score using EMBER-2's algorithm:
> 
> SCORE = (BA + ZA + APB) / 3 + ( WRT \* OI ) / OD + (PC - PS) \* 20
> 
> Players in the *penalty* host should be ignored, as they are currently banned from the game.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
COPY 200 X
MARK LOOP
REPL READ
ADDI X 1 X
COPY 17 T
MARK WAIT
SUBI T 1 T
TJMP WAIT
TEST X > 299
FJMP LOOP
COPY -1 M
HALT
MARK READ
GRAB X
MARK TRANSF
COPY F M
TEST EOF
FJMP TRANSF
```

### [XB](XB.exa) (global)
```asm
MAKE
COPY 0 F
COPY 0 F

MARK CALC
COPY M X
TEST X = -1
TJMP END
COPY X F
SEEK -2

COPY M X
ADDI X M X
ADDI X M X
DIVI X 3 X

COPY M T
MULI T M T
DIVI T M T

ADDI X T X

COPY M T
SUBI T M T
MULI T 20 T

ADDI X T X

TEST X > F
TJMP REPLACE
JUMP CALC

MARK REPLACE
COPY F T
SEEK -3
COPY T F
COPY X F
JUMP CALC

MARK END
SEEK -1
VOID F
VOID F
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 3916   | 53   | 1        |

# 34: Mitsuzen HDI-10 (Cerebral Cortex)

<div align="center"><img src="EXAPUNKS - Bloodlust Online (397, 122, 26, 2023-10-08-00-15-00).gif" /></div>

## Instructions
> Create a file in your host containing the hostname and hardware register value of each neuron exactly once, sorted as pairs from lowest to highest hostname.
> 
> Note that each test run has its own unique network layout.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
REPL L3
REPL L03
REPL L1
MARK OP
COPY #NERV X
COPY M X
ADDI X 1 X
COPY X M
COPY 39 T
MARK WAIT
SUBI T 1 T
TJMP WAIT
HOST M
COPY 14 T
MARK WAITB
SUBI T 1 T
TJMP WAITB
COPY #NERV M
HALT

MARK L3
LINK 3
REPL L3
REPL L1
REPL L01
JUMP OP

MARK L03
LINK -3
REPL L03
REPL L1
REPL L01
JUMP OP

MARK L1
LINK 1
REPL L3
REPL L03
REPL L1
JUMP OP

MARK L01
LINK -1
REPL L3
REPL L03
REPL L01
JUMP OP
```

### [XB](XB.exa) (global)
```asm
MAKE
COPY 0 M
COPY 38 T
MARK WAIT
SUBI T 1 T
TJMP WAIT
COPY M X
MULI X 2 T
MARK COPY
COPY M F
SUBI T 1 T
TJMP COPY
MODE
COPY 1 M
SEEK -9999
SUBI X 1 T
SUBI X 2 X
MARK LOOP
COPY F M
SEEK X
COPY F M
MULI X -1 X
SEEK X
SEEK -1
SUBI T 1 T
MULI X -1 X
TJMP LOOP
SEEK 9999
SEEK -2
COPY F M
COPY F M
COPY -1 M

COPY 1 X
MARK HELPER
COPY M T
MULI X T X
TEST T = -1
TJMP RETURN
COPY M T
JUMP HELPER
MARK RETURN
COPY X M
COPY M X
TEST X = -2
TJMP END
JUMP HELPER
MARK END
```

### [XC](XC.exa) (local)
```asm
TEST M = 1
MAKE
MARK LOOP
COPY M X
TEST X = -1
COPY X F
FJMP LOOP
SEEK -1
VOID F
MARK PRESORT
SEEK -9999
COPY 1 M
COPY 1 M
MARK SORT
COPY F T
SEEK 1
TEST T > F
TJMP SWAP
SEEK 1
MARK BACK
TEST EOF
TJMP FILE
SEEK -2
JUMP SORT
MARK SWAP
SEEK -1
COPY F X
SEEK -3
COPY F T
SEEK -1
COPY X F
SEEK 1
COPY T F
COPY F X
SEEK -3
COPY F T
SEEK -1
COPY X F
SEEK 1
COPY T F
COPY 0 M
COPY 0 M
JUMP BACK
MARK FILE
COPY -1 M
COPY M X
TEST X = 0
FJMP END
COPY 1 M
JUMP PRESORT
MARK END
COPY -2 M
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 2229   | 143  | 16       |

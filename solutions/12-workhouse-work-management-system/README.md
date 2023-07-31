# 12: Workhouse (Work Management System)

<div align="center"><img src="EXAPUNKS - WorkHouse (516, 29, 2, 2023-07-31-12-14-00).gif" /></div>

## Instructions
> Locate EMBER-2's user file in the *users* host and overwrite it so that the sum of the values is the same but no individual value exceeds $75. All values, except for the last, must be the maximum value ($75). You will need to add additional values to accomplish this.
> 
> EMBER-2's username is available in file 300.
> 
> Note that the sum of the values in EMBER-2's account will always be less than $10,000.
> 
> For more information see "Network Exploration: Workhouse" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F X
DROP
LINK 800
GRAB 199
MARK IDSEARCH
TEST F = X
FJMP IDSEARCH
SEEK 1
COPY F X
DROP
LINK 799
GRAB X
SEEK 2
COPY 0 X
MARK REWRITE
ADDI X F X
SUBI X 75 X
SEEK -1
COPY 75 F
TEST EOF
FJMP REWRITE
MARK WRITE
COPY 75 F
SUBI X 75 X
TEST X < 75
FJMP WRITE
COPY X F
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 516    | 29   | 2        |

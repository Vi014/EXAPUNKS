# 19: Emerson's Guide (Streetsmarts GIS Database)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (274, 51, 601, 2023-05-19-15-14-32).gif" /></div>

## Instructions
> Each host contains a list of restaurants and their ratings, from one to five stars (file 200). Locate the entry that corresponds to the Last Stop on Eddy Street and change its rating from one to five stars.
> 
> The name of the target restaurant and its location within the GIS grid is available in file 300. The first coordinate is the number of times to move east, while the second coordinate is the number of times to move north (positive) or south (negative).
> 
> For more information see "Network Exploration: Geographic Information Systems" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
SEEK 1
COPY F X
MARK LONGITUDE
TEST X = 0
TJMP LATITUDE
LINK 801
SUBI X 1 X
JUMP LONGITUDE
MARK LATITUDE
COPY F X
TEST X < 0
TJMP NEG
MARK POS
TEST X = 0
TJMP END
LINK 800
SUBI X 1 X
JUMP POS
MARK NEG
TEST X = 0
TJMP END
LINK 802
ADDI X 1 X
JUMP NEG
MARK END
SEEK -3
COPY F X
WIPE
GRAB 200
MARK FIND
TEST F = X
TJMP REPL
SEEK 5
JUMP FIND
MARK REPL
COPY F X
COPY X F
COPY X F
COPY X F
COPY X F
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 52     | 42   | 6        |

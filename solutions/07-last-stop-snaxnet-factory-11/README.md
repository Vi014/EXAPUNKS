# 7: Last Stop Snaxnet (Factory 11)

<div align="center"><img src="EXAPUNKS - Last Stop SNAXNET (33, 13, 2, 2023-07-31-12-13-08).gif" /></div>

## Instructions
> ﻿Remove the keyword ‗PEANUTS‗ (file 300) from the Peanut Blast recipe (file 237).
> 
> Note that the target keyword will appear in a different position in each of the 100 test runs. To view and debug each of the different test runs, click the arrow buttons next to the "TEST RUN" display above.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F X
DROP
LINK 800
LINK 800
GRAB 237
MARK TEST
TEST F = X
FJMP TEST
SEEK -1
VOID F
DROP
WIPE
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 33     | 13   | 2        |

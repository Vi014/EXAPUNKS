# 8: Zebros Copies (Point-Of-Sale System)

<div align="center"><img src="EXAPUNKS - Zebros Copies (102, 34, 4, 2023-07-31-12-13-14).gif" /></div>

## Instructions
> Erase Ghast's debt to the copy shop by zeroing out his balance in the customer database (file 200) and appending a payment to the payment log (file 201) with today's date and the exact amount of his prior balance.
> 
> Ghast's customer ID is available in file 300.
> 
> For more information see "Network Exploration: Digicash Point-of-Sale Systems" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F M
SEEK -1
COPY F M
WIPE
```

### [XB](XB.exa) (global)
```asm
LINK 800
GRAB 200
COPY M X
MARK LOOP
TEST F = X
FJMP LOOP
COPY F X
COPY F T
SEEK -2
COPY 0 F
COPY 0 F
DROP
GRAB 201
SEEK 9999
COPY X F
COPY T F
DROP
WIPE
```

### [XC](XC.exa) (global)
```asm
LINK 800
LINK 801
COPY #DATE X
COPY M T
LINK -1
GRAB 201
SEEK 9999
COPY X F
COPY T F
DROP
WIPE
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 102    | 34   | 4        |

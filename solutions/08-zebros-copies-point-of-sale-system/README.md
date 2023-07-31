# 8: Zebros Copies (Point-Of-Sale System)

<div align="center"><img src="EXAPUNKS - SFCTA Highway Sign #4902 (168, 26, 1, 2023-05-19-15-02-51).gif" /></div>

## Instructions
> Erase Ghast's debt to the copy shop by zeroing out his balance in the customer database (file 200) and appending a payment to the payment log (file 201) with today's date and the exact amount of his prior balance.
> 
> Ghast's customer ID is available in file 300.
> 
> For more information see "Network Exploration: Digicash Point-of-Sale Systems" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
MARK LOOP
COPY 1 #COPY
JUMP LOOP
```

### [XB](XB.exa) (global)
```asm
LINK 800
LINK 800
LINK 801
MARK LOOP
COPY 1 #COPY
JUMP LOOP
```

### [XC](XC.exa) (global)
```asm
LINK 800
LINK 800
LINK 802
MARK LOOP
COPY 1 #COPY
JUMP LOOP
```

### [XD](XD.exa) (global)
```asm
LINK 800
LINK 800
LINK 803
MARK LOOP
COPY 1 #COPY
JUMP LOOP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 0      | 0    | 0        |

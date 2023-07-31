# 5: Euclid's Pizza (Order System)

<div align="center"><img src="EXAPUNKS - Euclid's Pizza (25, 16, 1, 2023-07-31-12-12-45).gif" /></div>

## Instructions
> Append your order (file 300) to the end of the order list (file 200).
> 
> Note that all orders, including yours, will consist of exactly five keywords.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
GRAB 200
SEEK 9999
COPY 5 X
MARK LOOP
COPY M F
SUBI X 1 X
TEST X = 0
FJMP LOOP
HALT
```

### [XB](XB.exa) (global)
```asm
GRAB 300
MARK LOOP
COPY F M
TEST EOF
FJMP LOOP
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 25     | 16   | 1        |

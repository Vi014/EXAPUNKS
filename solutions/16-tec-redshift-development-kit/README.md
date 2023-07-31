# 16: TEC Redshift (Development Kit)

<div align="center"><img src="EXAPUNKS - TEC Redshift™ (11902, 37, 4, 2023-07-31-12-15-14).gif" /></div>

## Instructions
> There is an unknown three-digit code (such as 4-7-3) that, when entered one digit at a time into #PASS, will unlock the link between *debug* and *secret*. Find the three-digit code and create a file in your host that contains the code as a sequence of three values, followed by the development kit's RDK ID.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
COPY 4 #PASS
COPY 7 #PASS
COPY 3 #PASS
LINK 800
GRAB 220
SEEK 31
COPY F X
SEEK 1
COPY X F
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 0      | 0    | 0        |

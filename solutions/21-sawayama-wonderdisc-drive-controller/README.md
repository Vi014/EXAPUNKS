# 21: Sawayama Wonderdisc (Drive Controller)

<div align="center"><img src="EXAPUNKS - Sawayama WonderDisc (7320, 53, 63, 2023-10-07-23-59-14).gif" /></div>

## Instructions
> Modify your WonderDisc, which normally only plays SSEA region games, to play games from any region.
> 
> The SSEA region code is available in file 300.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Hardware Hacks: Sawayama WonderDisc" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
COPY 8 #AUTH
COPY 0 #AUTH
COPY 3 #AUTH
COPY 2 #AUTH
COPY 7 #AUTH
COPY 1 #AUTH
COPY 0 #AUTH
COPY 4 #AUTH
COPY 9 #AUTH
COPY 5 #AUTH
COPY 1 #AUTH
COPY 2 #AUTH
COPY 5 #AUTH
COPY 2 #AUTH
COPY 6 #AUTH
COPY 1 M
MARK READTRAK
COPY #TRAK M
MAKE
MARK WRITE
COPY M X
TEST X = 1
TJMP MOVE
COPY X F
JUMP WRITE
MARK MOVE
LINK 800
DROP
LINK -1
JUMP READTRAK
```

### [XB](XB.exa) (global)
```asm
GRAB 300
COPY F X
DROP
LINK 800
TEST M = 1
LINK 801
MARK GETFILE
GRAB M
MARK READFILE
TEST F > 0
FJMP BYPASS
SEEK -1
COPY F M
MARK TEST
TEST EOF
FJMP READFILE
COPY 1 M
DROP
TJMP GETFILE
MARK BYPASS
COPY X M
JUMP TEST
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 7320   | 53   | 63       |

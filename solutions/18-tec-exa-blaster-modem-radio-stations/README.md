# 18: TEC EXA-Blaster Modem (Radio Stations)

<div align="center"><img src="EXAPUNKS - TEC EXA-Blaster™ Modem (1513, 68, 17, 2023-10-07-23-56-17).gif" /></div>

## Instructions
> ﻿Connect to each radio station and replace every song in the playlist (file 200) with ‗CAN'T (NOT) GET OVER YOU‗ by ‗ME2U‗ (file 300). Each song in a playlist consists of two keywords: the song name and the artist name.
> 
> A list of phone numbers for the radio stations is available in file 301.
> 
> Note that EXAs in global mode can only communicate if there is a path of links connecting them.
> 
> For more information see "Hacker Skills: Modem Control at the Direct Level" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
MARK DIAL
COPY M X
TEST X = -1
TJMP STATION
TEST X = -2
TJMP END
COPY X #DIAL
JUMP DIAL
MARK STATION
LINK 800
GRAB 200
MARK REPLACE
TEST EOF
TJMP ELSEWHERE
COPY 1 M
COPY M F
COPY M F
JUMP REPLACE
MARK ELSEWHERE
COPY -1 M
DROP
LINK -1
COPY -1 #DIAL
JUMP DIAL
MARK END
```

### [XB](XB.exa) (global)
```asm
MARK READLINE
GRAB 301
MODE
COPY 1 M
COPY M X
MODE
MULI X 11 X
SEEK X
TEST EOF
TJMP END
COPY 11 T
MARK READNM
COPY F M
SUBI T 1 T
TJMP READNM
COPY -1 M
DROP
GRAB 300
MARK READSONG
TEST M = 1
FJMP GOBACK
COPY F M
COPY F M 
SEEK -2
JUMP READSONG
MARK GOBACK
DROP
JUMP READLINE
MARK END
COPY -2 M
MODE
COPY 2 M
HALT
```

### [XC](XC.exa) (local)
```asm
COPY 0 X
MARK ASDF
TEST M = 1
FJMP END
COPY X M
ADDI X 1 X
JUMP ASDF
MARK END
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 1513   | 68   | 17       |

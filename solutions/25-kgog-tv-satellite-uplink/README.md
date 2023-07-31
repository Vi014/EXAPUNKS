# 25: KGOG-TV (Satellite Uplink)

<div align="center"><img src="EXAPUNKS - The Wormhole (x10x10x, 2023-05-19-15-23-46).gif" /></div>

## Instructions
> Align the satellite dish with the target satellite by setting the azimuth, elevation, and frequency. Then transmit the data from EMBER-2's video (file 301) after encrypting it using the TV station's encryption key (file 199).
> 
> The azimuth, elevation, and frequency of the target satellite are available in file 300.
> 
> Note that you must align the satellite dish before transmitting any data.
> 
> For more information see "Look to the Stars with Satellite Uplink Systems" in the second issue of the zine.

## Solution

### [XA](XA.exa) (local)
```asm
GRAB 300

LINK 800
LINK 799
SEEK 5
COPY F #FREQ



SEEK -3
LINK 801
MARK HIGHER_E
TEST #ELEV > F
FJMP LOWER_E1
SEEK -1
COPY -1 #MOTR
SUBI #ELEV 1 #ELEV
JUMP HIGHER_E
MARK LOWER_E1
SEEK -1
MARK LOWER_E
TEST #ELEV < F
FJMP AZIM
SEEK -1
COPY 1 #MOTR
ADDI #ELEV 1 #ELEV
JUMP LOWER_E

MARK AZIM
SEEK -3
LINK -1
LINK 800
MARK HIGHER_A
TEST #AZIM > F
FJMP LOWER_A1
SEEK -1
COPY -1 #MOTR
SUBI #AZIM 1 #AZIM
JUMP HIGHER_A
MARK LOWER_A1
SEEK -1
MARK LOWER_A
TEST #AZIM < F
FJMP END
SEEK -1
COPY 1 #MOTR
ADDI #AZIM 1 #AZIM
JUMP LOWER_A



MARK END
LINK -1
COPY 1 M
MODE
COPY 1 M
WIPE
```

### [XB](XB.exa) (local)
```asm
GRAB 301
SEEK 1
LINK 800
LINK 799
TEST M = 1
MODE
NOOP

MARK TRANSFER
COPY F M
TEST M = -1
TJMP RETRANSFER
MARK BACK
COPY M #DATA
TEST EOF
TJMP END
COPY 0 M
FJMP TRANSFER

MARK RETRANSFER
SEEK -1
COPY F M
JUMP BACK

MARK END
COPY -1 M
WIPE
```

### [XC](XC.exa) (global)
```asm
LINK 800
GRAB 199
TEST M = 1

MARK ENCRYPT
COPY M X
ADDI X F X
TEST X = 9999
TJMP WRAP
COPY 0 M
COPY X M
MARK AROUND
TEST M = -1
TJMP END
TEST EOF
FJMP ENCRYPT
SEEK -9999
JUMP ENCRYPT

MARK WRAP
COPY -1 M
SEEK -1
COPY M X
SUBI X 9999 X
SUBI X 1 X
ADDI X F X
COPY X M
JUMP AROUND

MARK END
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 742    | 100  | 9        |

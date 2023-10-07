# 1: Bloodlust Online (US East Realm)

<div align="center"><img src="EXAPUNKS - Motor Vehicle Administration (653, 80, 7, 2023-10-08-00-15-20).gif" /></div>

## Instructions
> Each host contains an item listing (file 200) that lists all of the items in that location (ID, type, and state).
> 
> First, locate mutex8021's hideout by finding the ‗TALISMAN‗ (file 300). Then find the ‗MAP‗ in the hideout and use it to locate the target host: the secret vampire lair. Next, travel to the target host, disconnect the vampire players by terminating their EXAs, set the ‗DOOR‗ to be ‗UNLOCKED‗, and copy the ‗SAFE‗ combination to the ‗CLOCK‗ so that mutex8021 can read it and empty the safe.
> 
> Note that the door to mutex8021's hideout will always be ‗UNLOCKED‗.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
COPY F X
SEEK 9999
COPY 799 F
SEEK -9999
MARK FIND
SEEK 5
ADDI F 1 F
SEEK -2
VOID F
LINK F
DROP
GRAB 200
MARK LOOP
SEEK 1
TEST F = X
TJMP OUTSIDE
SEEK 1
TEST EOF
FJMP LOOP
DROP
GRAB 300
LINK -1
JUMP FIND
MARK OUTSIDE
DROP
GRAB 300
SEEK 2
COPY F X
SEEK 2
VOID F

DROP
GRAB 200
MARK DOOR
SEEK 1
TEST F = X
SEEK 1
FJMP DOOR

SEEK -1
COPY F X
DROP
GRAB 300
SEEK 9999
COPY X F
SEEK -5
COPY F X

DROP
GRAB 200
MARK MAP
SEEK 1
TEST F = X
SEEK 1
FJMP MAP

SEEK -1
COPY F X
DROP
GRAB 300
SEEK 9999
COPY 799 F

MARK FIND2
LINK -1
SEEK -1
ADDI F 1 F
SEEK -2
VOID F
LINK F
HOST T
TEST T = X
FJMP FIND2

@REP 4
KILL
@END
SEEK -5
COPY F X
DROP
REPL HELPER1
GRAB 200
MARK DOOR2
SEEK 1
TEST F = X
SEEK 1
FJMP DOOR2
SEEK -1
COPY M F

DROP
GRAB 300
SEEK 3
COPY F X
DROP
REPL HELPER2
GRAB 200
MARK SAFE
SEEK 1
TEST F = X
SEEK 1
FJMP SAFE
SEEK -1
COPY F M
COPY M X
SEEK -9999
MARK CLOCK
SEEK 1
TEST F = X
SEEK 1
FJMP CLOCK
SEEK -1
COPY M F
HALT



MARK HELPER1
GRAB 300
SEEK 5
COPY F M
HALT
MARK HELPER2
GRAB 300
COPY M X
SEEK 4
COPY F M
WIPE
COPY X M
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 397    | 122  | 26       |

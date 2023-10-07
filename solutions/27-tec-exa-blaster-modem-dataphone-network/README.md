# 27: TEC EXA-Blaster Modem (Dataphone Network)

<div align="center"><img src="EXAPUNKS - TEC EXA-Blaster™ Modem (2877, 57, 18, 2023-10-08-00-06-04).gif" /></div>

## Instructions
> Using your modem, connect to each dataphone so that EMBER-2 will have a list of valid phone numbers.
> 
> Each dataphone contains a list of the owner's contacts (file 200). The phone number of one of these dataphones is in your host (file 300), while the rest are in the contact list of another dataphone.
> 
> Note that each dataphone (aside from the first) will appear in exactly one other dataphone's contact list, in such a way that you can find them all without getting stuck in a loop.
> 
> For more information see "Hacker Skills: Modem Control at the Direct Level" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
MARK DIAL
MODE
COPY -1 #DIAL
SEEK -9999
SEEK X
ADDI X 11 X
TEST EOF
TJMP END
COPY 11 T
MARK LOOP
COPY F #DIAL
SUBI T 1 T
TJMP LOOP
COPY 1 M
MODE
SEEK 9999
NOOP
NOOP
TEST MRD
FJMP DIAL
VOID M
MARK COPY
TEST M = -1
TJMP DIAL
COPY M F
JUMP COPY
MARK END
COPY -1 M
WIPE
```

### [XB](XB.exa) (local)
```asm
LINK 800
MARK WAIT
TEST M = 1
FJMP FIN
REPL WAIT
MODE
LINK 800
COPY 1 M
GRAB 200
MARK COPY
SEEK 1
TEST EOF
TJMP END
COPY 11 T
MARK LOOP
COPY F M
SEEK -1
COPY F M
SUBI T 1 T
TJMP LOOP
JUMP COPY
MARK END
COPY -1 M
DROP
LINK -1
MARK FIN
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 2877   | 57   | 18       |

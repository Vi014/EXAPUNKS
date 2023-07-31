# 3: Trash World News (Tutorial 3)

<div align="center"><img src="EXAPUNKS - TRASH WORLD NEWS (9, 12, 4, 2023-07-31-12-12-30).gif" /></div>

## Instructions
> File 199 contains exactly two values: a keyword and a number. Create a new file in the *outbox* and copy those two values to it, swapping their order so that the number is first. When you are finished, delete file 199.
> 
> For help completing this task see "Ghast Walks U Thru It" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
LINK 799
GRAB 199
COPY F M
COPY F M
WIPE
; HALT
```

### [XB](XB.exa) (global)
```asm
MAKE
LINK 800
LINK 800
COPY M X
COPY M F
COPY X F
; DROP
; HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 9      | 12   | 4        |

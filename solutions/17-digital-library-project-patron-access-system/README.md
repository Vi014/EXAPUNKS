# 17: Digital Library Project (Patron Access System)

<div align="center"><img src="EXAPUNKS - Digital Library Project (1312, 50, 74, 2023-10-07-23-52-45).gif" /></div>

## Instructions
> Books are stored in the host corresponding to the first digit of their call number, while a book's file ID is 200 plus the last two digits of the call number. For example, book 512 would be stored in the host *500-599* as file 212.
> 
> Duplicate each of the books requested by EMBER-2 and bring them back to your host.
> 
> The call numbers for the books EMBER-2 wants are available in file 300.
> 
> Note that EMBER-2 will never request more than one book from the same host.

## Solution

### [XA](XA.exa) (global)
```asm
MARK START
GRAB 300
SEEK M
TEST EOF
TJMP END
COPY 0 M
COPY F X
DROP
SWIZ X 003 T
LINK 800
MARK GO
LINK 800
SUBI T 1 T
TJMP GO
SWIZ X 021 T
ADDI T 200 T
GRAB T
MARK COPYBOOK
COPY F M
TEST EOF
FJMP COPYBOOK
DROP
COPY 0 M
SWIZ X 003 T
MARK RETURN
LINK -1
SUBI T 1 T
TJMP RETURN
LINK -1
JUMP START
MARK END
COPY 1 M
HALT
```

### [XB](XB.exa) (global)
```asm
COPY 0 X
MARK START
COPY X M
TEST M = 1
TJMP END
MAKE
MARK FILECOPY
COPY M T
FJMP COPY
COPY T F
TJMP FILECOPY
MARK COPY
DROP
ADDI X 1 X
JUMP START
MARK END
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 1312   | 50   | 74       |

# 2: Motor Vehicle Administration (Scheduling System)

<div align="center"><img src="EXAPUNKS - Cybermyth Studios (827, 235, 19, 2023-10-08-00-15-49).gif" /></div>

## Instructions
> There is a list of appointments (file 200) in *storage* that contains an appointment for NthDimension (file 300) to take his driving test. Remove the appointment from the list of appointments, change the date to today's date (#DATE register), and insert it between today's appointments and tomorrow's appointments.
> 
> To gain access to the *storage* host you will need to unlock it by writing the lowest ticket number to the #NEXT register. Each EXA in *public* is holding a ticket; terminate them all to find the ticket of the next EXA to be served.
> 
> Note that writing an incorrect ticket number to the #NEXT register will fail the _leave no trace_ requirement.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
@REP 5
KILL
@END
COPY 200 X
MARK LOOP
REPL GRAB
ADDI X 1 X
TEST MRD
FJMP LOOP

VOID M
NOOP
LINK 800
COPY #DATE X
COPY F X
DROP
GRAB 200
MARK FIND
SEEK 1
TEST F = X
SEEK 1
FJMP FIND
SEEK -3
COPY 1 F
COPY 1 F
COPY F X
SEEK -1
COPY 1 F
MARK MOVE
SEEK -5
COPY F T
SEEK 2
TEST F = T
TJMP ALT
SEEK -5
TEST F = #DATE
TJMP END
SEEK -1
@REP 3
COPY F T
SEEK 2
COPY T F
SEEK -3
@END
JUMP MOVE

MARK ALT
SEEK -9999
JUMP END2

MARK END
SEEK 2
MARK END2
COPY #DATE F
COPY 1 F
COPY X F
DROP
GRAB 300
COPY F X
WIPE
GRAB 200
MARK LOOP2
SEEK 1
TEST F = 1
SEEK 1
FJMP LOOP2
SEEK -2
COPY X F
HALT



MARK GRAB
GRAB X
COPY 1 M
COPY F #NEXT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 653    | 80   | 7        |

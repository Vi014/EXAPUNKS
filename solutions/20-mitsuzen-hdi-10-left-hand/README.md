# 20: Mitsuzen HDI-10 (Left Hand)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (274, 51, 601, 2023-07-31-12-22-26).gif" /></div>

## Instructions
> There are three nerve signals that need to be relayed: muscle control (M), which runs from your central nervous system (CNS) to your hand (HND), and heat (H) and pressure (P), which run the other direction.
> 
> For each signal, read a value from the input nerve and relay it to the output nerve. Repeat _ad infinitum_.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [MC](MC.exa) (global)
```asm
LINK 800
LINK -3
LINK -3
MARK LOOP
COPY #NERV M
NOOP
NOOP
NOOP
NOOP
JUMP LOOP
```

### [HC](HC.exa) (global)
```asm
LINK 800
LINK -3
LINK -3
LINK -3
NOOP
MARK LOOP
NOOP
COPY M #NERV
NOOP
NOOP
NOOP
JUMP LOOP
```

### [PC](PC.exa) (global)
```asm
LINK 800
LINK -3
LINK -3
LINK -3
LINK -3
NOOP
MARK LOOP
NOOP
NOOP
NOOP
COPY M #NERV
JUMP LOOP
```

### [MH](MH.exa) (global)
```asm
LINK 800
LINK 3
LINK 3
MARK LOOP
COPY M #NERV
NOOP
NOOP
NOOP
NOOP
JUMP LOOP
```

### [HH](HH.exa) (global)
```asm
LINK 800
LINK 3
LINK 3
LINK 3
@REP 4
NOOP
@END
MARK LOOP
NOOP
COPY #NERV M
NOOP
NOOP
NOOP
JUMP LOOP
```

### [PH](PH.exa) (global)
```asm
LINK 800
LINK 3
LINK 3
LINK 3
LINK 3
@REP 2
NOOP
@END
MARK LOOP
NOOP
NOOP
NOOP
COPY #NERV M
JUMP LOOP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 0      | 0    | 0        |

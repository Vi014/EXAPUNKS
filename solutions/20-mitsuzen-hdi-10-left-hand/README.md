# 20: Mitsuzen HDI-10 (Left Hand)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (274, 51, 601, 2023-10-07-23-58-09).gif" /></div>

## Instructions
> There are three nerve signals that need to be relayed: muscle control (M), which runs from your central nervous system (CNS) to your hand (HND), and heat (H) and pressure (P), which run the other direction.
> 
> For each signal, read a value from the input nerve and relay it to the output nerve. Repeat _ad infinitum_.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
MARK ASDF
@REP 2
LINK -3
@END
COPY #NERV X
@REP 4
LINK 3
@END
COPY X #NERV
@REP 2
LINK -3
@END
JUMP ASDF
```

### [XB](XB.exa) (global)
```asm
LINK 800
MARK ASDF
@REP 4
LINK 3
@END
COPY #NERV X
@REP 8
LINK -3
@END
COPY X #NERV
@REP 4
LINK 3
@END
JUMP ASDF
```

### [XC](XC.exa) (global)
```asm
LINK 800
MARK ASDF
@REP 3
LINK 3
@END
COPY #NERV X
@REP 6
LINK -3
@END
COPY X #NERV
@REP 3
LINK 3
@END
JUMP ASDF
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 274    | 51   | 601      |

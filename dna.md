# DNA Synthesis

Simulates DNA existance and synthesis in the Cell.

## Components

| Component |   |
|-----------|---|
| self      | DNA |
| consume   | consumed when DNA is produced |

## Parameters

| Parameter | Type | Description |
|-----------|------|---|
| consume[] | metabolite | component |
| k         | numeric | rate of synthesis |

## Properties

`mu` is the population size

| Property    | Equation | Description |
|-------------|----------|---|
| n_dna       | k * dna  | |
| v_synth     | min(n_dna * self) * min(n_dna * consume) | speed of synthesis |
| dilution    | self * mu | dilutation of self because of cell division |

## Equations

```
self        = self + v_synth - dilution
consume     = consume - v_synth
```



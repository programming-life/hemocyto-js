# Protein Synthesis

Simulates protein synthesization.

## Components

| Component |   |
|-----------|---|
| self      | protein |
| produce   | produced when sythesis occurs (usually the protein itself) |
| consume   | consumed when protein is produced |

## Parameters

| Parameter | Type | Description |
|-----------|------|---|
| produce[] | metabolite | component |
| consume[] | metabolite | component |
| k         | numeric | rate of synthesis |
| k_d       | numeric | rate of degration |

## Properties

`mu` is the population size

| Property    | Equation | Description |
|-------------|----------|---|
| n_dna       | k * dna  | |
| v_synth     | min(n_dna * produce) * min(n_dna * consume) | speed of synthesis |
| degradation | self * k_d | degradation count of self |
| dilution    | self * mu | dilutation of self because of cell division |

## Equations

```
self        = self + v_synth - degradation - dilution
consume     = consume - v_synth
```



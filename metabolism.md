# Metabolism

Simulates cell metabolism. Converts substrate into product.

## Components

| Component |   |
|-----------|---|
| self      | the metabolite causing the metabolism (usually an enzyme) |
| input     | input when metabolism occurs |
| output    | output when metabolism occurred |
| consume   | consumed when enzyme grows |

## Parameters

| Parameter | Type | Description |
|-----------|------|---|
| input[]   | metabolite | component |
| ouput[]   | metabolite | component |
| consume[] | metabolite | component |
| k         | numeric | rate of synthesis |
| k_d       | numeric | rate of degration |
| k_m       | numeric | MM kinetics constant |
| v         | numeric | v max for metabolism |

## Properties

`mu` is the population size

| Property     | Equation | Description |
|--------------|----------|---|
| n_dna        | k * dna  | |
| v_metabolism | self * v * ( input / ( input + k_m )) | speed of synthesis |
| v_synth      | self * n_dna |
| degradation  | self * k_d | degradation count of self |
| dilution     | self * mu | dilutation of self because of cell division |

## Equations

```
self    = self + v_synth - degradation - dilution
consume = consume - v_synth
input   = input - v_metabolism
output  = output + v_metabolism
```

## Context

### Rate of Metabolism

The max speed constant v_max called v
The enzyme itself
The compound to convert
The Mihaelis-Mentin kinetics with constant k_m

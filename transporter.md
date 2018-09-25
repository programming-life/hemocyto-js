# Transporter

Simulates cell boundary crossings

## Components

| Component |   |
|-----------|---|
| self      | the metabolite causing the transport (usually a transporter) |
| input     | input when transport occurs |
| output    | output when transport occurred (usually the same as input) |
| consume   | required for transport synthesis |

## Parameters

| Parameter | Type | Description |
|-----------|------|---|
| input[]   | metabolite | component |
| ouput[]   | metabolite | component |
| consume[] | metabolite | component |
| k         | numeric | rate of synthesis |
| k_tr      | numeric | rate of transport |
| k_m       | numeric | MM kinetics constant |
| v         | numeric | v max for metabolism |
| is_active | boolean | true if it is, false otherwise|

## Properties

| Property      | Equation | Description |
|---------------|----------|---|
| n_dna         | k * dna  | |
| v_transport   | is_active ? v_transport_a : v_transport_p | speed of transport |
| v_transport_a | self * k_tr * ( input / ( input + k_m ) ) * cell |
| v_transport_p | self * k_tr * input * cell |
| v_synth       | self * n_dna * consume |
| dilution      | self * mu | dilutation of self because of cell division |

## Equations

```
self    = self + v_synth - dilution
consume = consume - v_synth
input   = input - v_transport
output  = output + v_transport
```

## Context

### Rate of Metabolism

#### Passive
The Transport constant k_tr
The Transporter itself
The Compound to transport
The Diffussion kinetics

#### Active
The Transport constant k_tr
The Transporter itself
The Compound to transport
The Mihaelis-Mentin kinetics with constant k_m

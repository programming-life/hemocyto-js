# Population growth

Simulates Cell Growth / Population size

## Components

| Component |   |
|-----------|---|
| self      | metabolite |
| infrastructure | metabolite components |
| metabolites | metabolite |

## Parameters

| Parameter | Type | Description |
|-----------|------|---|
| supply    | numeric | rate of supply |

## Properties

| Property    | Equation | Description |
|-------------|----------|---|
| mu | infrastructure * metabolites | population growth based on infrastructure |


## Equations

```
self = self * mu
```



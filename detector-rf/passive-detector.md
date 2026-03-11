# Detector RF Pasivo – Arduino

Versión simple y estable.

## Componentes
- Arduino UNO
- Protoboard
- Loop de cobre (~6 cm)
- 1N4148
- 100nF (104)
- 100k

## Circuito

loop ----|>|---- VDET ---- A0
       1N4148
                |
               100nF
                |
               GND

VDET ----100k---- GND

## Notas
- la rayita del diodo apunta a VDET
- un lado del loop va a GND
- el otro lado del loop va al diodo

## Uso
Sirve para:
- comparar antenas
- ver irradiación relativa
- ubicar mejor posición/orientación
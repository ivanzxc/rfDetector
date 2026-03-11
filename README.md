# RF Lab

Laboratorio personal de RF.

## Contenido
- `detector-rf/`: detector RF con Arduino
- `antennas/`: notas de antenas
- `docs/`: inventario y documentación general

## Equipos
- Baofeng UV-R5
- Baofeng 888
- Motorola EM400
- Motorola GM300
- Arduino UNO

## Bandas
- 144 MHz
- 465 MHz

# Arduino RF Lab – Guía simple

Esto es para recordar **cómo instalar, conectar y probar** el detector RF.

Repo:


arduino-rf-lab


---

# 1. Qué hace el proyecto

Detector RF muy simple para:

- comparar antenas
- ver si un transmisor irradia
- ubicar zonas de mayor campo RF

Usa:


loop → diodo → filtro → Arduino A0


---

# 2. Componentes

Necesitás:

- Arduino UNO
- protoboard
- loop de cobre (~6 cm)
- diodo **1N4148**
- capacitor **100nF (104)**
- resistencia **100k**

Opcional:

- capacitor **1uF**

---

# 3. Circuito


loop ----|>|---- VDET ---- A0
1N4148
|
100nF
|
GND

VDET ----100k---- GND


IMPORTANTE:

- la **rayita del diodo** apunta hacia **VDET**
- un lado del loop va a **GND**

---

# 4. Conexiones Arduino

Arduino pin | conexión
---|---
A0 | VDET
GND | GND del circuito

No hace falta conectar 5V.

---

# 5. Código Arduino

Archivo:


detector-rf/passive-detector.ino


```cpp
const int PIN_RF = A0;

int suavizado = 0;

void setup() {
  Serial.begin(115200);
}

void loop() {
  int raw = analogRead(PIN_RF);
  suavizado = (suavizado * 8 + raw * 2) / 10;

  Serial.println(suavizado);

  delay(20);
}
6. Cómo probar

abrir Serial Monitor

velocidad:

115200
sin transmisión

valor bajo o cerca de 0

transmitiendo con el Baofeng cerca

el valor sube

7. Uso correcto

Para comparar antenas:

misma radio

misma potencia

misma distancia

misma orientación del loop

8. Estructura de la repo
arduino-rf-lab
│
├─ detector-rf
│  ├─ passive-detector.ino
│  └─ passive-detector.md
│
├─ antennas
│  └─ notes.md
│
└─ docs
   └─ inventory.md
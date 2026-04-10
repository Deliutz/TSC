# InkTime Smartwatch Project

Proiect hardware pentru realizarea unui smartwatch open-source low-cost, bazat pe microcontrollerul **Nordic nRF52840**, proiectat în **Autodesk Fusion 360 Electronics**.

---

# Diagramă bloc
```text
Baterie LiPo → BQ25180 Charger → RT6160 Buck-Boost → Rail 3.3V
                                           ↓
                                     nRF52840 MCU
                        ↙              ↓              ↘
                   BMA423 IMU     E-Paper Display    DRV2605 Haptic
                        ↓                               ↓
                 MAX17048 Fuel Gauge             Motor vibrații
                        ↓
                    USB-C + ESD
```

---

# Bill of Materials (BOM)

| Componentă | Cod | Rol | Interfață |
|---|---|---|---|
| nRF52840 | U1 | Microcontroller principal + BLE | SPI / I2C / GPIO |
| BQ25180YBGR | IC1 | Încărcare baterie LiPo | Power |
| RT6160AWSC | IC9 | Convertor buck-boost 3.3V | Power |
| BMA423 | IC3 | Accelerometru / IMU | I2C |
| DRV2605YZFR | IC2 | Driver feedback haptic | I2C / GPIO |
| MAX17048G+T10 | U3 | Fuel gauge baterie | I2C |
| KH-TYPE-C-16P | J4 | Conector USB-C | USB |
| USBLC6-2SC6Y | D3 | Protecție ESD USB | USB |
| 503480-2400 | J2 | Conector display e-paper | SPI |
| 2450AT18B100E | ANT1 | Antenă 2.4 GHz BLE | RF |
| TC2030-IDC | J1 | Conector debugging SWD | SWD |
| Butoane | SW_UP, SW_ENT, SW_DN | Input utilizator | GPIO |

---

# Funcționalitate hardware
Designul este construit în jurul microcontrollerului **nRF52840**, responsabil de:
- comunicația Bluetooth Low Energy;
- citirea senzorilor;
- controlul display-ului e-paper;
- gestionarea butoanelor;
- controlul feedback-ului haptic;
- monitorizarea bateriei.

## Alimentare
- **BQ25180** gestionează încărcarea bateriei LiPo;
- **RT6160** generează tensiunea stabilă de **3.3V**;
- **MAX17048** monitorizează nivelul bateriei.

## Senzori și periferice
- **BMA423** este conectat prin **I2C**;
- display-ul e-paper este conectat prin conectorul FPC;
- **DRV2605** comandă motorul de vibrații;
- USB-C este folosit pentru alimentare și debugging.

---

# Utilizarea pinilor nRF52840
## Magistrală I2C
- SDA → IMU + Fuel Gauge
- SCL → IMU + Fuel Gauge

## SWD
- SWDIO
- SWDCLK
- SWO
- RESET

## GPIO
- Buton UP
- Buton ENTER
- Buton DOWN
- semnale control display
- semnal driver haptic

## SPI
- semnale rutate către conectorul display-ului e-paper

---

# Proces de proiectare

## 1. Schematic
În prima etapă am realizat schema electrică pornind de la modelul oferit pe OCW și folosind exclusiv biblioteca pusă la dispoziție.

Am implementat blocurile:
- LiPo Charger
- DC/DC
- IMU
- SWD
- E-Paper Driver
- Fuel Gauge
- Haptic Driver
- Buttons
- USB-C + ESD

În timpul realizării schemei:
- am modificat valorile componentelor pasive;
- am adăugat condensatoare de decuplare;
- am etichetat semnalele importante;
- am separat schematicul pe blocuri funcționale.

---

## 2. PCB Design
PCB-ul a fost realizat pe baza dimensiunilor mecanice recomandate.

Etapele principale:
- placement TOP pentru componentele critice;
- amplasarea componentelor pasive lângă pinii de alimentare;
- rutare pe mai multe straturi;
- plane dedicate de GND;
- păstrarea zonei antenei liberă;
- alinierea USB-C și a butoanelor cu carcasa.

La final am rulat DRC și am corectat erorile principale.

---

## 3. Model 3D
Modelul 3D include:
- PCB
- baterie
- display
- carcasă

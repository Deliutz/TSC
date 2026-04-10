Poți copia tot blocul exact cum este.

# ⌚ InkTime Smartwatch Project

Open-source low-cost smartwatch hardware project built around **Nordic nRF52840**, designed in **Autodesk Fusion 360 Electronics**.

---

# 📐 Block Diagram
```text
Battery → BQ25180 Charger → RT6160 Buck-Boost → 3V3 Rail
                                      ↓
                                nRF52840 MCU
                     ↙          ↓           ↘
                BMA423 IMU   E-Paper      DRV2605 Haptic
                     ↓       Display           ↓
                MAX17048 Fuel Gauge       Vibration Motor
                     ↓
                  USB-C + ESD
```

---

# 🔩 Bill of Materials (BOM)

| Component | Code | Function |
|---|---|---|
| nRF52840 | U1 | Main MCU + BLE |
| BQ25180YBGR | IC1 | LiPo battery charger |
| RT6160AWSC | IC9 | Buck-boost 3.3V regulator |
| BMA423 | IC3 | IMU accelerometer |
| DRV2605YZFR | IC2 | Haptic driver |
| MAX17048G+T10 | U3 | Fuel gauge |
| KH-TYPE-C-16P | J4 | USB-C connector |
| 503480-2400 | J2 | E-paper display connector |
| 2450AT18B100E | ANT1 | 2.4 GHz BLE antenna |
| USBLC6-2SC6Y | D3 | USB ESD protection |

---

# ⚙️ Hardware Functionality

The smartwatch is centered around the **nRF52840**, used for:
- BLE communication
- sensor data acquisition
- display driving
- button input
- haptic notifications
- battery monitoring

## 🔋 Power Path
- **BQ25180** handles LiPo charging
- **RT6160** generates stable **3.3V**
- **MAX17048** monitors battery percentage

## 📡 Sensors & Peripherals
- **BMA423** connected over **I2C**
- **E-Paper Display** connected through FPC connector
- **DRV2605** controls vibration motor
- **USB-C** used for charging and debugging

---

# 🔌 nRF52840 Pin Usage

## I2C
- SDA → IMU + Fuel Gauge
- SCL → IMU + Fuel Gauge

## SWD
- SWDIO
- SWDCLK
- SWO
- RESET

## GPIO
- Button UP
- Button ENTER
- Button DOWN

## SPI / Display
- SPI routed to E-paper connector
- control lines for display driver

---

# 🛠️ Design Process

## 1️⃣ Schematic
The schematic was built based on the OCW reference design using only the provided libraries.

Implemented functional blocks:
- LiPo Charger
- DC/DC
- IMU
- SWD
- E-Paper Driver
- Fuel Gauge
- Haptic Driver
- Buttons
- USB-C + ESD

During implementation:
- passive values were adjusted
- decoupling capacitors were added
- net labels were created
- power and signal lines were grouped by function

---

## 2️⃣ PCB Design
The PCB was designed using the provided mechanical outline.

Main steps:
- TOP placement of all critical components
- passive components placed close to IC power pins
- routing on multiple layers
- dedicated GND planes
- antenna clearance preserved
- USB-C and buttons aligned with enclosure

DRC was run and the main errors were corrected before export.

---

## 3️⃣ 3D Model
The full 3D assembly includes:
- PCB
- battery
- display
- enclosure

The final STEP model was used to verify:
- mechanical fit
- USB-C alignment
- button placement
- internal clearance

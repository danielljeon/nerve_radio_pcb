# nerve_radio_pcb

![kibot](https://github.com/danielljeon/nerve_radio_pcb/actions/workflows/kibot.yaml/badge.svg)

Radio and power supply module
to [`nerve_pcb`](https://github.com/danielljeon/nerve_pcb).

---

<details markdown="1">
  <summary>Table of Contents</summary>

<!-- TOC -->
* [nerve_radio_pcb](#nerve_radio_pcb)
  * [1 Overview](#1-overview)
  * [2 Board Specifications](#2-board-specifications)
    * [2.1 Connectors](#21-connectors)
    * [2.2 Switching Buck Regulator](#22-switching-buck-regulator)
  * [3 Release Notes](#3-release-notes)
    * [3.1 v0.1.0-alpha](#31-v010-alpha)
    * [3.2 v1.0.0 (WIP)](#32-v100-wip)
<!-- TOC -->

</details>

---

## 1 Overview

|                           Top                            |                             Bottom                             |
|:--------------------------------------------------------:|:--------------------------------------------------------------:|
| ![nerve_radio_pcb-top.png](docs/nerve_radio_pcb-top.png) | ![nerve_radio_pcb-bottom.png](docs/nerve_radio_pcb-bottom.png) |

---

## 2 Board Specifications

### 2.1 Connectors

Connectors fixed by hardware (PCB traces or the connector itself).

| Connector                       | Ref | Description                                                                  |
|---------------------------------|:---:|------------------------------------------------------------------------------|
| LMR51430 buck (5 V) regulator   | J1  | Pin 1: Ground, Pin 2: VIN supply (> 5 V, <= 36 V)                            |
| Bottom side 2x10 board-to-board | J2  | See schematic/layout for details                                             |
| 5 V GPIO/PWM breakout           | J3  | Pin 1: 5 V, Pin 2-3: GPIO/PWM 1-2 (5 V), Pin 5: Ground                       |
| SPI breakout                    | J4  | Pin 1: 3.3 V, Pin 2: MISO, Pin 3: MOSI, Pin 4: CLK, Pin 5: CS, Pin 6: Ground |

### 2.2 Switching Buck Regulator

The `LMR51430` is used for the 5 V (3 A) supply from a 4.5 V to 36 V input.

Also chosen based on previous experience and testing from a previous
project, [robotic_hand_pcb](https://github.com/danielljeon/robotic_hand_pcb).
See documentation
at [robotic_hand_pcb/blob/main/README.md#5-switching-buck-regulator](https://github.com/danielljeon/robotic_hand_pcb/blob/main/README.md#5-switching-buck-regulator).

---

## 3 Release Notes

### 3.1 v0.1.0-alpha

- Pre-release 4-layer board variant.
    - Short-term pre-release board bring-up/testing release.
- Order date: 2025/01/13.

### 3.2 v1.0.0 (WIP)

- Incremented major version since `v0.1.0-alpha` pre-release due to partial
  redesign including full component changes.
    - Buck converter redesign (TPSM843x20 -> LMR51430), reasoning:
        - Potential supply chain risks and cost.
        - Improved compatibility in common buck converter IC footprints.
        - Reduced restrictions on space allocated for power supply circuits.
        - Improved input voltage range (> 5 V, <= 36 V) -> (> 5 V, <= 17 V).
        - Easier to test due to exposed switch node.

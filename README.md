Forked from: https://github.com/gczgcz2015/zmk-config

# ZMK config starter

This repository is a ZMK config repo for a Pro Micro form factor nRF52840
split keyboard compatible with the upstream `nice_nano_v2` board definition.

It currently builds:

- a normal `dactyl-6x5-left` central firmware target for the left half
- a normal `dactyl-6x5-right` firmware target for the right half
- a safe `settings-reset` firmware image for clearing persistent settings

# Hardware

The custom shield uses the upstream `nice_nano_v2` board target plus a local
split shield named `dactyl_6x5`. The matrix is wired like the
reference QMK `handwired/dactyl_manuform/5x7` layout, with each half using
six rows and seven columns.

- diode direction: `col2row`
- left side is the split central
- only one host Bluetooth profile is configured on the central side
- idle timeout is 30 seconds and deep sleep timeout is 1 hour

```
NRF52840 nice_nano_v2
___________________
| Bat- |USB| Bat+ |
| -             - |
| -           GND |
| GND         RST |
| GND           - |
| C5    / \     - |
| C4   /   \   R4 |
| C3  / MCU \  R3 |
| C2  \     /  R2 |
| C1   \   /   R1 |
| C0    \ /    R0 |
| -             - |
-------------------

Keyboard logical layout
       Left(central)                                  Right
       | C5 | C4 | C3 | C2 | C1 | C0 |                | C0 | C1 | C2 | C3 | C4 | C5 |
    R0 | X  | X  | X  | X  | X  | X  |             R0 |  X |  X |  X |  X |  X |  X |
    R1 | X  | X  | X  | X  | X  | X  |             R1 |  X |  X |  X |  X |  X |  X |
    R2 | X  | X  | X  | X  | X  | X  |             R2 |  X |  X |  X |  X |  X |  X |
    R3 | X  | X  | X  | X  | X  | X  |             R3 |  X |  X |  X |  X |  X |  X |
    R4 |    | X  | X  | X  | X  | X  |             R4 |  X |  X |  X |  X |  X |    |

Keyboard physical layout (RC)
      Left(central)                                  Right
      | 05 | 04 | 03 | 02 | 01 | 00 |                | 00 | 01 | 02 | 03 | 04 | 05 |
      | 15 | 14 | 13 | 12 | 11 | 10 |                | 10 | 11 | 12 | 13 | 14 | 15 |
      | 25 | 24 | 23 | 22 | 21 | 20 |                | 20 | 21 | 22 | 23 | 24 | 25 |
      | 35 | 34 | 33 | 32 | 31 | 30 |                | 30 | 31 | 32 | 33 | 34 | 35 |
      |    |    |    | 43 | 42 | 41 |                | 41 | 42 | 43 |    |    |    |
      |    |    |    |    | 44 | 40 |                | 40 | 44 |    |    |    |    |

```

![zmk-studio-layout](https://github.com/stephan-razin/zmk-config-dactyl-6x5/raw/main/img/zmk-studio-layout.png)
Bluetooth reset: `` ` `` + `` \ ``

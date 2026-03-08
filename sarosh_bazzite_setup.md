# Sarosh's Bazzite System — Setup Complete ✅
**Generated March 2026 | VLSI/DFT + Embedded Systems Workstation**
**Last verified: March 7, 2026 — all tools confirmed working**

---

## System Info

| Attribute | Detail |
|-----------|--------|
| OS | Bazzite GNOME NVIDIA `43.20260303` |
| GPU | NVIDIA (drivers loaded: nvidia, nvidia_modeset, nvidia_drm, nvidia_uvm) |
| Image | `ghcr.io/ublue-os/bazzite-gnome-nvidia:stable` |
| Shell | bash |
| Home | `/var/home/Jihadi_Pandit` |

---

## EDA Tools

| Tool | Version | Method | Notes |
|------|---------|--------|-------|
| Yosys | system | rpm-ostree | Synthesis + DFT scan insertion |
| iverilog | system | rpm-ostree | Verilog simulation |
| OpenROAD | via container | Podman | Run via `openroad` alias |
| OpenLane2 | 2.3.9 | Podman | Full PD flow container |
| KLayout | 0.30.6 | pip | Layout viewer |
| GTKWave | 3.3.125 | rpm-ostree | Waveform viewer for iverilog simulations |

### Aliases (in `~/.bashrc`)
```bash
alias openroad="podman run --rm -it -v $(pwd):/work -w /work ghcr.io/efabless/openlane2:2.3.9 openroad"
alias openlane="podman run --rm -it -v $(pwd):/work -w /work ghcr.io/efabless/openlane2:2.3.9 openlane"
alias openroad-gui="podman run --rm -it -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -v $(pwd):/work -w /work ghcr.io/efabless/openlane2:2.3.9 openroad -gui"
```

---

## Embedded Tools

| Tool | Version | Method | Notes |
|------|---------|--------|-------|
| avr-gcc | system | rpm-ostree | Arduino bare-metal C |
| avr-libc | system | rpm-ostree | AVR C standard library |
| avrdude | system | rpm-ostree | Flash AVR chips |
| ESP-IDF | v6.1-dev | git install | ESP32 native toolchain |
| esptool | 5.2.0 | pip | ESP32 flashing utility |
| pyserial | 3.5 | pip | UART communication |
| minicom | 2.10 | rpm-ostree | Serial terminal for AVR/ESP32 UART testing |

### ESP-IDF Path (in `~/.bashrc`)
```bash
export IDF_PATH="$HOME/esp/esp-idf"
. "$IDF_PATH/export.sh"
```

---

## Python Stack

| Package | Purpose | Phase |
|---------|---------|-------|
| flask | Web server (RPi dashboard capstone) | Week 4 + Phase 2 |
| streamlit | EDA metrics dashboard | Phase 4 |
| plotly | Interactive charts | Phase 4 |
| pandas | Report parsing, data analysis | Phase 2+ |
| matplotlib | Plotting | Phase 2+ |
| scikit-learn | ML timing predictor | Phase 4 |
| xgboost | ML timing predictor | Phase 4 |
| jupyter | Notebook development | Phase 4 |
| pyserial | UART comms | Week 3+ |
| esptool | ESP32 tooling | Week 2+ |
| klayout | Layout viewing | Phase 2+ |

---

## VS Code Extensions

| Extension | Purpose |
|-----------|---------|
| ms-vscode.cpptools | C/C++ — AVR + ESP32 |
| ms-python.python | Python + Pylance |
| mshr-h.veriloghdl | Verilog HDL — DFT work |
| espressif.esp-idf-extension | ESP32 native toolchain |
| platformio.platformio-ide | Arduino bare-metal |
| ms-toolsai.jupyter | Jupyter notebooks |
| github.vscode-pull-request-github | GitHub integration |
| sleutho.tcl | Tcl — OpenROAD/EDA automation |

---

## Git Configuration

```
user.name  = SaroshGabriel
user.email = saroshjibreel@gmail.com
defaultBranch = main
protocol = HTTPS
GitHub = authenticated via gh CLI
```

---

## Project Structure

```
~/Projects/
├── DFT/
│   ├── yosys-scan        ← Week 2: scan insertion project
│   ├── atpg-scripts      ← Week 4 + Phase 3: ATPG scripting
│   └── verilog-practice  ← Week 2-3: LFSR, BSR cell
├── Embedded/
│   ├── avr-baremetal     ← Week 2: bare-metal AVR in C
│   ├── esp32-idf         ← Week 2+: ESP-IDF projects
│   └── rpi-linux         ← Week 4+: RPi C programs + systemd
├── EDA/
│   ├── openroad-flow     ← Phase 2: automated PD flow (P1)
│   ├── report-parser     ← Phase 4: EDA report dashboard (P2)
│   └── ml-timing         ← Phase 4: ML timing predictor (P4)
└── Capstone/
    └── esp32-rpi-dashboard ← Week 4: ESP32+RPi+Flask capstone
```

---

## GitHub Repos

| Repo | URL | Status |
|------|-----|--------|
| march-learning-log | https://github.com/SaroshGabriel/march-learning-log | ✅ Live |

---

## Daily Git Workflow

```bash
# After each work session
cd ~/Projects/<relevant-folder>
git add .
git commit -m "Brief description of what was done"
git push
```

**Rule:** Every project committed the same day it works.  
The commit timestamp is proof of work against the employment gap.

---

## March Schedule — Quick Reference

| Week | DFT Track | Embedded Track | Key Output |
|------|-----------|----------------|------------|
| 1 (Mar 3-9) | Fault models, NPTEL L1-L6 | Yosys install + hello-world | C basics, scan chain theory |
| 2 (Mar 10-16) | Scan insertion, JTAG TAP | AVR bare-metal, ESP-IDF blink | First Yosys scan project |
| 3 (Mar 17-23) | BIST, LFSR, BSR cell Verilog | UART/I2C/SPI protocols | Verilog BSR cell simulated |
| 4 (Mar 24-31) | Full DFT flow document | ESP32 FreeRTOS + RPi systemd | Capstone project live |

---

## 12-Month Roadmap — Overview

| Phase | Timeline | Focus | Key Deliverable |
|-------|----------|-------|-----------------|
| 1 | M1-2 | Toolchain + C + DFT theory | Yosys running, C basics solid |
| 2 | M3-4 | PD automation portfolio | OpenROAD full flow on ibex (P1) |
| 3 | M5-6 | DFT depth + scan project | Scan insertion + fault coverage tool (P3) |
| 4 | M7-9 | ML-enhanced EDA tools | Timing predictor + dashboard (P2, P4) |
| 5 | M10-12 | Job readiness + launch | OpenROAD contribution, offer-ready |

---

## Key Commands Reference

```bash
# Verify tools
which yosys iverilog avr-gcc avrdude gcc make git idf.py

# Run OpenROAD
cd ~/Projects/EDA/openroad-flow
openroad design.tcl

# Run OpenLane2
cd ~/Projects/EDA/openroad-flow
openlane config.json

# ESP32 new project
cd ~/Projects/Embedded/esp32-idf
idf.py create-project my_project
cd my_project && idf.py build

# Flash AVR
avr-gcc -mmcu=atmega328p -o blink.elf blink.c
avr-objcopy -O ihex blink.elf blink.hex
avrdude -c arduino -p m328p -P /dev/ttyUSB0 -U flash:w:blink.hex

# Yosys scan insertion
yosys -p "read_verilog design.v; synth; dfflegalize; dfflibmap -liberty cells.lib; dft_tag; write_verilog post_scan.v"

# Simulate with iverilog
iverilog -o sim testbench.v design.v && vvp sim

# View waveforms
gtkwave dump.vcd

# Serial terminal for AVR/ESP32 UART testing
minicom -D /dev/ttyUSB0 -b 115200
```

---

*Generated & verified March 7, 2026 | Bazzite GNOME NVIDIA 43.20260303 | All tools confirmed working*
*Tools: Yosys · iverilog · GTKWave · OpenROAD · ESP-IDF v6.1 · avr-gcc · minicom · Python EDA stack · Tcl*

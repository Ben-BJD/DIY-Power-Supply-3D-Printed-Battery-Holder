# DIY Power Supply: AA Battery Pack FreeCad Source, STL files, Cura Projects

**Power Your ESP32 & Arduino with Custom 3D Printed Battery Packs**

## 📖 Project Overview
A custom AA battery holder using **FreeCAD**.

Whether you need a single cell for a 1.5V circuit or a series configuration for 3.3V/5V microcontrollers (ESP32, Arduino), this repository provides the source files and print settings to manufacture your own reliable power supply.

### Key Concepts
*   **Design for Assembly (DFA):** Creating snap-fit components and managing tolerances for 3D printed parts.
*   **Electro-Mechanical Integration:** combining plastic with metal leaf springs and wiring.

---

## 📂 Repository Structure

```text

├── README.md                # Project documentation
├── /source                  
│   └── AA-Battery-Case.FCStd  # The master FreeCAD source file (editable)
├── /stls                    
│   ├── AA-Battery-Case.stl    # 1x AA Holder
│   ├── AA-Battery-Case-2up.stl# 2x AA Holder (Series)
│   └── AA-Battery-Case-3up.stl# 3x AA Holder (Series)
├── /cura_projects           
│   ├── AA-Battery-Case.3mf    # Cura project files (Model + Settings included)
│   ├── AA-Battery-Case-2up.3mf
│   └── AA-Battery-Case-3up.3mf
└── /slicer_profiles       
    └── Cura-Settings.curaprofile # Custom Cura profile for tight tolerances
```

---

## 🛠 Bill of Materials & Tools

To replicate this project, you will need the following hardware.

### Hardware
*   **Batteries:** Standard AA.
*   **Contacts:** Standard Negative Coil springs and Positive Button contacts with Solder Lug.
*   **Wiring:** Copper tape or standard stranded wire optional: JST connectors.

### Tools
*   **3D Printer**
*   **Slicer:** Ultimaker Cura.
*   **Assembly:** Soldering iron (high temp recommended for quick joints), Multimeter for continuity testing.

---

## 📐 Design & Tolerances

One of the hardest parts of **designing snap-fit battery covers in FreeCAD** is getting the tolerance right. Through multiple iterations, I settled on the following specifications for a "Snug/Friction" fit.

*   **Wall Thickness:** 2.25mm for durability.
*   **Tolerance Strategy:** Target 0.3mm to 0.4mm total clearance.
    *   *Vertical Holes:* Added extra 0.1mm clearance to account for gravity/squish.

**Measurements Used:**
*   **Battery Slot:** Height calculated to compress the negative spring but leave slack for different battery sizes.
*   **Contact Slots:** Designed for a 13.27mm x 11.2mm base plate.

---

## 🖨️ 3D Printing Guide

### Recommended Settings (Cura)
I have included a `.curaprofile` in the `slicer_profiles` folder, but here are the critical adjustments made for tight tolerances:

*   **Material:** PLA (Tested at 200°C Nozzle / 60°C Bed).
*   **Orientation:** Rotate 90° (Back of case against the bed).
*   **Ironing:** **Enabled** (Crucial for smooth top surfaces on the contact slots).
*   **Skin Overlap:** 0.12mm (increased from default 0.04mm for better wall adhesion).

### How to Print
1.  **Easiest Method:** Open the files in `cura_projects/`. These `.3mf` files contain the model positioned correctly on the build plate with all settings pre-loaded.
2.  **Manual Method:** Import an STL from `stls/`, rotate it 90°, and import the profile from `slicer_profiles/`.

> **Note:** G-code is not included in this repo as it is specific to my printer's calibration. Please slice the files for your specific machine.

---

## ⚡ Assembly & Wiring

### 1. Insert Contacts
The slots are designed for a friction fit. Slide the coil spring into the negative side and the button contact into the positive side. If the fit is too tight due to printer variation, use a small flathead screwdriver to press them in.

### 2. Wiring
You have two options for connecting the terminals:
*   **Copper Tape:** Best for low-current applications and quick prototyping.
*   **Soldering:** Required for reliable power.

### ⚠️ Soldering Safety Warning
**PLA has a low melting point.** When soldering wires to the tabs:
*   Use a high temperature on your iron.
*   Apply solder "lickety-split" (very quickly).
*   If you hold the iron on the contact too long, the heat will transfer to the plastic and deform the holder.

---

## 🔋 Testing & Results

The final designs were load tested using a multimeter and connected to various microcontroller boards.

| Configuration | Measured Voltage | Application Test |
| :--- | :--- | :--- |
| **1x Case** | ~1.6V | Basic LED circuits |
| **2x Case** | ~3.2V | Directly powering an ESP32C3 without a regulator (Running on LiFePO4 or Alkaline*) |
| **3x Case** | ~4.8V | Regulated XIAO Seed Studio ESP32 |

---

## 🚀 Future Improvements
*   **Parametric Design:** Converting the FreeCAD project to a fully parametric spreadsheet-driven model to easily adapt to AAA or 18650 cells.
*   **Recycling:** Developing a workflow to recycle the PLA scrap generated during the iteration process.

## 📄 License
This project is open-source. Feel free to fork, modify, and improve the design.


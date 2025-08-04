# Microstrip High-Pass Filter Simulation Repository

## Repository Structure

```
microstrip-hpf-hfss/
├── .gitignore
├── README.md
├── docs/
│   ├── geometry_screenshots/
│   │   ├── Microstrip-High-Pass-Model.jpg
│   │   ├── HighPass-filter-Microstrip-Analysis-1.jpg
│   │   └── EF-field-effect.jpg
│   └── animation/
│       └── efield_animation.avi
├── hfss_project/
│   ├── Microstrip_High_Pass_Filter_Divyam.aedt
│   ├── Microstrip_High_Pass_Filter_Divyam.aedt.lock
│   └── scripts/                # any supporting VBScript or Python
├── results/
│   ├── s_parameters.csv
│   ├── s11_s22_plot.png
│   └── s12_s21_plot.png
└── LICENSE
```

## README.md

# Microstrip High-Pass Filter Simulation

### Introduction to Microstrip
A **microstrip** is a type of electrical transmission line commonly used to
convey microwave-frequency signals. It consists of a conductive strip placed on top of a dielectric substrate, with a ground plane on the bottom
side. Due to its compact and planar structure, it is widely implemented in
high-frequency circuits such as Antennas, Filters, Couplers, Power Dividers, Amplifiers etc.
### Advantages of Microstrip:
- Compact and Lightweight – Suitable for PCB integration.
- Low-Cost Fabrication – Easily manufactured using standard PCB
etching methods.
- Ideal for RF/Microwave Applications – Excellent for high-frequency
performance.

### Understanding S-Parameters
Scattering parameters (S-parameters) quantify how RF energy is reflected and transmitted at network ports:
- **S11**: Input reflection coefficient (return loss at Port 1)  
- **S22**: Output reflection coefficient (return loss at Port 2)  
- **S21**: Forward transmission (gain or insertion loss from Port 1 → Port 2)  
- **S12**: Reverse transmission (Port 2 → Port 1)  

In a well-matched high-pass filter, S21 and S12 overlap and rise above a threshold in the passband, while S11 and S22 remain low, indicating minimal reflections.

### 1. Geometry Creation
![Structure](docs/geometry_screenshots/microstrip_stricture.png)
1. **Substrate**  
   - Modeled as a cuboid of Rogers RT/duroid 5880 (εr = 2.2)  
2. **Transmission Line**  
   - Main strip drawn via Rectangle tool  
3. **Resonators**  
   - Microstrip stubs attached along the line for filtering; grouped with Unite  
4. **Vias**  
   - Cylinders connecting the top strip to the bottom ground plane  


### 2. Port and Boundary Setup
- **Lumped Ports**  
  - Port 1 at the input end; Port 2 at the output end; both renormalized to 50 Ω  
- **Perfect E Boundaries**  
  - Assigned to all conductor faces to enforce ideal metallic behavior  

### 3. Simulation Environment
- **Open Region**  
  - Surrounding air region to allow free-space radiation  
- **Frequency Sweep**  
  - Linear sweep from 1 GHz to 6 GHz (101 points)  
- **Solution Setup**  
  - Driven-modal solver at 1.5 GHz, adaptive mesh with maximum ΔS = 0.02

### Results and Observations
- **S21 & S12 Overlap**  
  - Demonstrates symmetric, reciprocal filter response  
- **High-Pass Behavior**  
  - Sharp cutoff near **1.5 GHz**, matching theory  
- **Low S11 & S22 in Passband**  
  - Indicates good impedance match and minimal reflection  

| Parameter | Observation                               |
|-----------|-------------------------------------------|
| Cutoff    | ~1.5 GHz                                  |
| Insertion Loss (S21) | `results/HighPass filter Microstrip Analysis.JPG`
### E-Field Animation
An animation of the E-field distribution at 1.5 GHz illustrates field confinement and stub resonance.  
`docs/animation/efield_animation.avi`

## Getting Started

1. **Clone**  
   ```bash
   git clone https://github.com/DivyamGoyal-github/Microstrip-High-Pass-Filter-ANSYS-HFSS-Simulation.git
   cd hfss_project
   ```
2. **Open Project**  
   - Launch Ansys Electronics Desktop and open `hfss_project/Microstrip_High_Pass_Filter_Divyam.aedt`.
3. **Run Simulation**  
   - Use the provided Driven-Modal setup; results export to `results/`.
4. **View Results**  
   - Plots under `results/`, screenshots under `docs/geometry_screenshots/`, animation under `docs/animation/`.

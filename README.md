# Atomistic Modeling of Laser Cutting Process

!(laser_cutting.png)

## Overview

This project presents a **molecular dynamics simulation** of the laser cutting process on an aluminum plate using LAMMPS (Large-scale Atomic/Molecular Massively Parallel Simulator). The simulation models the thermal effects, material removal, and heat-affected zones during laser cutting operations at the atomic scale.

## Key Features

- **Realistic Material Modeling**: Uses EAM (Embedded Atom Method) potential for aluminum
- **Sequential Laser Cutting**: Simulates laser movement along a centerline with 13 discrete positions
- **Heat-Affected Zone (HAZ)**: Models the thermal gradient around the cutting region
- **Material Vaporization**: Simulates atom removal at temperatures above boiling point (4500K)
- **Thermal Management**: Includes edge thermostats to prevent boundary effects
- **Defect Analysis**: Computes centro-symmetry parameter for crystallographic defect visualization
- **Temperature Tracking**: Per-atom temperature calculation for thermal distribution analysis

## Simulation Details

### Material Properties
- **Material**: Aluminum (Al)
- **Crystal Structure**: FCC lattice
- **Lattice Parameter**: 4.05 Å
- **Melting Point**: 933 K
- **Boiling Point**: 2743 K

### Simulation Parameters
- **Plate Dimensions**: 150 × 80 × 10 lattice units
- **Kerf Width**: 4 units (cutting width)
- **Cut Length**: 130 units (X: 10-140)
- **Peak Laser Temperature**: 4500 K
- **HAZ Temperature**: 1200 K
- **Initial Temperature**: 300 K (room temperature)
- **Timestep**: 0.001 ps

### Simulation Stages
1. **Initial Equilibration** (2000 steps)
2. **Laser Cutting** (13 positions, sequential heating and material removal)
3. **Cooling Phase** (gradual cooldown: 1200K → 800K → 500K → 300K)
4. **Final Equilibration** (10000 steps)

## Output Files

The simulation generates several output files for analysis:

- `laser_cutting.lammpstrj` - Main trajectory file with kinetic energy and centro-symmetry
- `temperature_cutting.lammpstrj` - Temperature distribution over time
- `final_cut_structure.lammpstrj` - Final structure with defect analysis
- `final_laser_cut.data` - Final atomic configuration data file
- `restart.cutting` - Restart files for continuation

## Requirements

- **LAMMPS** (with EAM potential support)
- **Al99.eam.alloy** potential file
- **Visualization Tool**: OVITO, VMD, or similar molecular visualization software

## Usage

### Running the Simulation

```bash
lmp -in laser_cutting.lmp
```

### Visualization Tips

**Using OVITO:**

1. Load the trajectory file: `laser_cutting.lammpstrj`
2. **Color by Temperature**: Use `v_atom_temp` column for temperature visualization
3. **Defect Visualization**: Use `c_centro` for centro-symmetry parameter
4. **Particle Appearance**: 
   - Adjust particle radius for better visibility
   - Use color coding to highlight temperature gradients
5. **View Settings**:
   - Rotate to see the cut kerf clearly
   - Use orthographic projection for technical views
   - Apply periodic boundary wrapping if needed

**Preventing Boundary Artifacts:**
- Add "Wrap at periodic boundaries" modifier
- Adjust camera angle to avoid boundary edges
- Use clipping planes to focus on the cutting region

## Analysis Capabilities

The simulation provides data for analyzing:

- **Thermal Distribution**: Temperature field evolution during cutting
- **Crystallographic Defects**: Dislocation formation and migration
- **Material Removal**: Kerf geometry and vaporization dynamics
- **Heat-Affected Zone**: Extent and temperature profile of HAZ
- **Stress and Strain**: Through potential energy and centro-symmetry analysis
- **Cooling Dynamics**: Solidification and thermal stress development

## Physical Phenomena Captured

- **Laser-Material Interaction**: High-temperature heating and ablation
- **Thermal Conduction**: Heat transfer from cutting zone to bulk material
- **Phase Transitions**: Solid → Liquid → Vapor transitions
- **Defect Formation**: Point defects, vacancies, and dislocations
- **Residual Stress**: Thermal gradients leading to stress accumulation

## Customization

You can modify the simulation by adjusting:

- **Plate dimensions**: Change `region box` parameters
- **Laser power**: Adjust peak temperature in Langevin fixes
- **Cutting speed**: Modify number of timesteps per position
- **Kerf width**: Change cut region dimensions
- **Material**: Replace with different EAM potentials (Cu, Ni, etc.)

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/akshansh11/Atomistic-modeling-of-Laser-Cutting-process/issues).

## License

<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">
  <img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" />
</a>

This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

**You are free to:**
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material

**Under the following terms:**
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made
- **NonCommercial** — You may not use the material for commercial purposes

## Author

**Akshansh Mishra**

- GitHub: [@akshansh11](https://github.com/akshansh11)
- Project Link: [Atomistic-modeling-of-Laser-Cutting-process](https://github.com/akshansh11/Atomistic-modeling-of-Laser-Cutting-process)

## Acknowledgments

- LAMMPS development team for the molecular dynamics engine
- OVITO for excellent visualization capabilities
- The computational materials science community for sharing knowledge and tools

---

*For questions, suggestions, or collaborations, please open an issue or contact the author.*

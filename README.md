# Permeability-calculator

 <img width="527" height="523" alt="Screenshot 2026-09-26 160428" src="https://github.com/user-attachments/assets/d681fa4a-2e70-4d90-80eb-644361607bcc" />



The permeability calculator is a COMSOL-based code. It is developed to generate an artificial 2D porous medium and calculate the corresponding absolute permeability, which is used in Darcy's law or other porous media flow formulations.

The main purpose of this code is to automate the generation of the circles in the domain by simple inputs provided by the user; then a sophisticated meshing approach is used to accelerate the meshing process. This approach decreases the meshing time substantially, especially when the domain is large.

The physics node and the study node will be created by running the code, and all the settings such as boundary conditions and material properties will be set automatically. The calculated permeability is shown to the user in the console after the calculation is complete.

Overlapping circles are not yet supported; this code is a simple solution to the problem of geometry needed in 2D, below the representative elementary volume (REV) size. In such a situation, one might need an actual porous geometry to capture the hydrodynamic signature of the real porous medium.

### A few notes about this code:

- This approach cannot replace the actual geometry of a porous medium and might only represent it.

- The code sets the material properties of water by default, which is intentional. In case the fluid of interest is a gas, one must pay extra attention to the Knudsen number and element sizes, as well as turbulence.

- Circle overlapping is not yet supported, and the program will warn the user in case it happens based on the input settings.

- COMSOL V6.4 is recommended, but the code may run on an older version if the syntax is the same; if you are using an older version, use the text file.

- The resulting porosity of the entire domain will be shown to the user in the console based on the input parameters.

- The resulting permeability of the entire domain (absolute permeability) will be shown to the user in the console based on the input parameters.

- Full incompressible NSE will be solved assuming steady-state flow.

## How to use: COMSOL v6.4

Open the `.mph` file.

1. Navigate to the Application Builder at the top left.

2. Click on “Permeability” under “Methods” in the main tree on the left.

3. To use the code, right-click on the Permeability method and click on “Edit”.

You will see the settings section:

- The first two allow the user to specify the number of circles in the x and y directions.

- **r:** represents the mean circle radius, and **rv** is the radius variation.

  To keep all circles the same, set **rv** to 0; to randomize the size of the circles by x, set the **rv** to 2x.

  For example, if `r = 1e-5 m` (10 micrometers) and you want to randomize the size so the circles are between 15–5 micrometers, you set `rv = 1e-5`; “r” will serve as the middle point.

- **pk:** The circle-to-circle center distance and controls the packing density.

- **Rey:** the Reynolds number corresponding to the empty domain; it is automatically converted to the inlet velocity based on the dimensions and material properties of the fluid.

- **Es:** The maximum element size; keep this close to the length order of the geometry.

- **Ol:** Don’t change this - control variable for overlapping.

Make changes to the global parameters in the code if you want to change the dynamic viscosity and density.

### Older versions:

Create a new method and copy and paste the code from the text file. If the syntax is not changed by COMSOL, the code will run flawlessly.

# Simsack Workflow: GenChromatographyResin for generating atomistic models for chromatography resins

# Table of contents
- [Aims](#Aims)
- [Installation](#Installation)
- [How it works](#How-it-works)
- [Contacts](#Contacts)

# Aims
[Go to the top](#Table-of-contents)

This workflow generates the atomistic representation of a polymer netowrk through coarse-grained 3D printing protocol, followed by the CG-to-All-Atom conversion.

This workflow is used to generate polymer network structures in [Ballweg et al.](https://doi.org/10.1016/j.chroma.2024.465089).

> [!IMPORTANT]
> The coarse-grained simulation to generate the topology of the 3D printed polymer network requires modified LAMMPS compilation to include the capability for generating bond with a certain bond type with an offset timestep. Currently, such LAMMPS compilation is hosted in the shared software folder on the INT-Nano cluster in int.kit.edu. A later update is planned to provide a docker for the entire software environment.

# Installation
[Go to the top](#Table-of-contents)

### Requirements

In order to run this Simstack workflow the following software are needed:
- Simstack 2021-12-15 (or newer version)
- LAMMPS 5Jun19 - modified for 3D printing

> [!NOTE]
> Simstack client can be installed and setup by following the [Simstack documentation](https://simstack.readthedocs.io/en/latest/)

> [!NOTE]
> The original results in [Ballweg et al.](https://doi.org/10.1016/j.chroma.2024.465089) were obtained using the software versions: Simstack (2021-12-15) and LAMMPS (5Jun19-modified).

# How it works 
[Go to the top](#Table-of-contents)

### Generation of coarse-grained polymer network structure and conversion to atomistic representation: inputs/outputs

The GenChromatographyResin workflow consists of 5 Simstack WaNos in a linear sequence of:
 1. Input_Polymer-Building-Blocks
 2. CG-Polymerisation
 3. Conversion_CG-to-AA
 4. MD-Relaxation
 5. Output_AA-Structure

The intermediate outputs from the previous WaNo is directly taken as the input of the next, rendering an automated protocol to generate the all-atom structure of a polymer network.

As inputs,
-  the building block types can be selected from the dropdown menu and number of corresponding building blocks are defined by the user in WaNo **Input_Polymer-Builidng-Blocks**
-  the system dimensions are defined by the user in WaNo **CG-Polymerisation** in the unit of nanometers

As output,
- The all-atom polymer network structure is downloadable in MOL2 data formats, which can subsequently be used as input to Maestro Schrödinger software in the follow-through [KNIME workflow](https://github.com/Ahmedkhalil-Mama/KNIME-Workflow-Binding-Poses-and-Energies-Calculation-of-Linear-Peptides).

A complete example, starting with 690 DHPMA monomers, 260 EGDMA crosslinkers, and 500 Q ligands with 4 -CH2- spacer units, in a simulation box size of 15x15x24 cubic nanometers, is included with all intermediate results in the [Example folder](Example/). The final MOL2 format output of the GenChromatographyResin is located in the [data of WaNo **Output_AA-Structure**](Example/2-205-01-05-17h35m04s-GenChromatographyResin_1.2c/exec_directories/2025-01-13-06h54m09s-Output_AA-structure/fPolyREF_conv.mol2).

# Contacts
If you have any question regarding this Simstack workflow, you can contact us:
-  liu.modan@kit.edu
-  wolfgang.wenzel@kit.edu
-  matthias.franzreb@kit.edu

# KNIIME Workflow: Binding Poses and Energies Calculation of Linear Peptides

<p align="center">
  <img src="https://github.com/user-attachments/assets/5c8fc319-423b-461e-9fae-daf64e3deb6c" alt="workflow image" width="400" height="auto" />
  <br />
  <small>Binding pose of Octapeptide-2 to TOYOPEARL MX-Trp-650M</small>
</p>

# Table of contents
- [Aims](#Aims)
- [Installation](#Installation)
- [How it works](#How-it-works)
- [Contacts](#Contacts)
- [Licence](#Licence)
- [References](#References)

# Aims
[Go to the top](#Table-of-contents)

This KNIME workflow streamlines the docking of linear peptides ([not exeeding 500 atoms and 100 rotatables bonds](https://support.schrodinger.com/s/article/1020)) to the chromatography resin TOYOPEARL MX-Trp-650M and computes their binding free energies in a fully automated fashion. By integrating directly with [Schrödinger's](https://www.schrodinger.com/) tools, it identifies the most favorable poses within a prepared binding site and calculates their relative energetics. The resulting scores and energy values provide key insights into how different pepetides bind, facilitating rational design or selection of peptides in chromatography and related applications. Because all steps are encapsulated within [KNIME](https://www.knime.com/), researchers can run complex simulations through a graphical interface without extensive programming or computational chemistry expertise. 

> [!IMPORTANT]
> A valid **Schrödinger license** is required to run this workflow. The license must include the following modules: Canvas, ConfGen, Core Hopping, Epik, Glide, Impact, Jaguar, Jaguar pKa, LigPrep, MacroModel, P450 SOM Prediction, Prime, PrimeX, QikProp, QSite, and SiteMap. Additionally, the Maestro, KNIME, and OPLS access licenses are also required.

# Installation
[Go to the top](#Table-of-contents)

### Requirements

In order to run this KNIME workflow the following software are needed:
- Schrödinger 2023-2 (or newer version)
- KNIME 4.7.1 (or newer version)

In addition to this repository, you can find the KNIME workflow on the KNIME Hub at this link: https://hub.knime.com/ballweti/spaces/Public/Binding%20Poses%20and%20Energies%20Calculation~bPcNwd0wgw5zvWH3/current-state. Importing the workflow from the Hub into KNIME is straightforward—simply drag and drop it into the software to streamline the upload process.

> [!IMPORTANT]
>  The original results in [Ballweg et al.](https://www.sciencedirect.com/science/article/pii/S0021967324004631) were obtained using the software versions: KNIME (4.7.1) and Schrödinger (2023-2).

# How it works 
[Go to the top](#Table-of-contents)

This section provides an example to help new users execute this KNIME workflow. First, the figure below illustrates a simplified overview of the steps involved.
### Prediction of binding poses and energies: inputs/outputs
<p align="center">
  <img src="https://github.com/user-attachments/assets/3bb05ab7-b72b-4a4c-b1d0-4e55ff5392de" alt="workflow image" width="500" height="auto"/>
  <br />
  <small>Simplified overview of the KNIME workflow</small>
</p>

To run this workflow, three different input files are required:
-  A SMILES-String file (.smi), which contains the different structures of the target molecules.
  ```
An example of a SMILES-String: C[C@H]([C@@H](C(=O)N[C@@H](CCC(=O)O)C(=O)N[C@@H]([C@@H](C)O)C(=O)N[C@@H](CCC(=O)N)C(=O)O)NC(=O)[C@H](CCCCN)NC(=O)[C@H](CCCCN)NC(=O)[C@H](CC(C)C)NC(=O)[C@H](CCCCN)N)O Octapeptide_2
```
-  A Docking Grid of Adsorbent (.sbc* or .maegz). Both file types can be generated using the _Receptor Grid Generation tool_ on Maestro Schrödinger.
-  Input parameters for the workflow as an Excel sheet (.xlsx)

Examples of the input files are provided in [input](Example/Input)

The Output files consist in:
- A Maestro Project File (.prj), which containts the different binding poses of the target molecules.
- Excel sheets (.xlsx), which containt the different binding energies of the target molecules.

Examples of the stated output files can be found under [output](Example/Output)

sbc*: The substructure file defines the locations of atoms at the outer edges of the resin model. These atoms are "frozen" during the minimization step to preserve the structural integrity of the resin while allowing the rest of the system to relax. The substructure file can be generated manually within the MacroModel Minimization Tool of the Schrödinger’s Maestro software.  An example of the SBC file structure is shown below:

“FXAT    1000      0      0      0    -1.0000     0.0000     0.0000     0.0000

FXAT   10001      0      0      0    -1.0000     0.0000     0.0000     0.0000”

Each line in the file begins with the command FXAT, which directs MacroModel to freeze the designated atom during the minimization process. The second column specifies the atom identifier, and a value of -1.0000 in column six indicates that the atom is fully restrained, ensuring it remains immobile throughout the minimization. 

# Contacts
If you have any question regarding this KNIME workflow, you can contact us:
-  ahmed-khalil.mama@kit.edu
-  matthias.franzreb@kit.edu



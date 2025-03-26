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
- [Usage of the Workflow](#Usage-of-SURFMAP)
- [Contacts](#Contacts)
- [Licence](#Licence)
- [How to cite SURFMAP](#How-to-cite-SURFMAP)
- [References](#References)

# Aims
[Go to the top](#Table-of-contents)

This KNIME workflow streamlines the docking of linear peptides ([not exeeding 500 atoms and 100 rotatables bonds](https://support.schrodinger.com/s/article/1020)) to the chromatography resin TOYOPEARL MX-Trp-650M and computes their binding free energies in a fully automated fashion. By integrating directly with [Schrödinger's](https://www.schrodinger.com/) tools, it identifies the most favorable poses within a prepared binding site and calculates their relative energetics. The resulting scores and energy values provide key insights into how different pepetides bind, facilitating rational design or selection of peptides in chromatography and related applications. Because all steps are encapsulated within KNIME, researchers can run complex simulations through a graphical interface without extensive programming or computational chemistry expertise. 

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
>  To reproduce the results exactly as stated in [Ballweg et al.](https://www.sciencedirect.com/science/article/pii/S0021967324004631), the same versions of KNIME (4.7.1) and Schrödinger (2023-2) must be used.

# How it works 
[Go to the top](#Table-of-contents)
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
-  A Docking Grid of Adsorbent (.sbc or .maegz). Both file types can be generated using the _Receptor Grid Generation tool_ on Maestro Schrödinger.
-  Input parameters for the workflow as an Excel sheet (.xlsx)
Examples of the input files are provided in the XX

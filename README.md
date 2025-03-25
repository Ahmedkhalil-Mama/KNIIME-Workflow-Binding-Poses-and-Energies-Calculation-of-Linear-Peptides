# KNIIME Workflow: Binding Poses and Energies Calculation of Linear Peptides

<p align="center">
  <img src="https://github.com/user-attachments/assets/5c8fc319-423b-461e-9fae-daf64e3deb6c" alt="workflow image" />
  <br />
  <small>Binding pose of Octapeptide-2 to TOYOPEARL MX-Trp-650M.</small>
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

This KNIME workflow streamlines the docking of linear peptides (not exeeding 500 atoms and/or 100 rotatables bonds) to the chromatography resin TOYOPEARL MX-Trp-650M and computes their binding free energies in a fully automated fashion. By integrating directly with [Schrodinger's](https://www.schrodinger.com/) tools, it identifies the most favorable poses within a prepared binding site and calculates their relative energetics. The resulting scores and energy values provide key insights into how different pepetides bind, facilitating rational design or selection of peptides in chromatography and related applications. Because all steps are encapsulated within KNIME, researchers can run complex simulations through a graphical interface without extensive programming or computational chemistry expertise. 

> [!IMPORTANT]
> A valid Schrödinger license is required to run this workflow. The license must include the following modules: Canvas, ConfGen, Core Hopping, Epik, Glide, Impact, Jaguar, Jaguar pKa, LigPrep, MacroModel, P450 SOM Prediction, Prime, PrimeX, QikProp, QSite, and SiteMap. Additionally, the Maestro, KNIME, and OPLS access licenses are also required.

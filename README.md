# Structural Modeling and Allosteric Site Identification of Thyroid Peroxidase (TPO) 🧬

## 📌 Project Overview
Thyroid Peroxidase (TPO) is a crucial enzyme responsible for thyroid hormone synthesis and is the primary target implicated in hypothyroidism and autoimmune thyroid diseases (e.g., Hashimoto's thyroiditis). Due to its large size and complexity, a complete 3D experimentally determined structure is currently unavailable. 

This project aims to computationally model the 3D structure of mature TPO, analyze its topological domains, and identify novel **allosteric binding sites** distant from the catalytic heme region for potential and highly specific drug targeting.

## 🔬 Methodology & Computational Pipeline

The workflow of this project was executed using a combination of bioinformatics tools and molecular modeling software:

### 1. Sequence Analysis & Signal Peptide Removal
* **Tool:** [SignalP 6.0]
* **Action:** The raw sequence of TPO was analyzed to identify and cleave the signal peptide, generating the **mature TPO** sequence ready for downstream processing.

### 2. Transmembrane Topology Prediction
* **Tool:** [DeepTMHMM]
* **Action:** The topological structure of the mature protein was mapped to identify functional domains. 
* **Results:**
    * `Extracellular Domain:` Residues 1 - 831
    * `Transmembrane (TM) Helix:` Residues 832 - 852
    * `Intracellular Domain:` Residues 853 - 915

### 3. 3D Structure Generation
* **Tool:** AlphaFold 
* **Action:** Due to the lack of a full PDB structure, a high-confidence 3D model of the mature TPO was generated utilizing AlphaFold's deep learning predictive capabilities.

![Insert Image of your AlphaFold 3D model here]

### 4. Protein Preparation & Minimization
* **Tool:** Schrödinger Suite (Protein Preparation Wizard)
* **Action:** The raw AlphaFold model was prepared by assigning bond orders, adding missing hydrogens, optimizing the hydrogen bond network, and performing restrained energy minimization to ensure a stereochemically stable structure.

### 5. Binding Site Identification (SiteMap)
* **Tool:** Schrödinger (SiteMap)
* **Action:** An extensive search for potential binding pockets was conducted to identify an allosteric site. 
* **Findings:** 10 potential pockets were identified.

## 📊 Results & Pocket Selection

Out of the 10 predicted pockets, **Pocket 1** was selected as the optimal allosteric binding site based on its favorable scoring metrics and strategic location.

### Pocket 1 Parameters:
* **Dscore:** $\approx$ 1.205
* **SiteScore:** $\approx$ 1.19
* **Volume:** $\approx$ 163 Å³

### Rationale for Selection:
1.  **High Druggability:** The Dscore and SiteScore indicate a highly favorable pocket for small molecule binding.
2.  **Compact Volume:** The relatively small volume (163 Å³) is ideal for a specific, high-affinity small molecule.
3.  **Allosteric Nature:** Most importantly, this pocket is located entirely distinct and distant from the **Heme region**. Targeting this site reduces the risk of completely shutting down the enzyme's catalytic activity or causing off-target effects associated with heme-binding drugs.

![Insert Image of Pocket 1 visualized in Schrodinger here]

## 🛠️ Tools Used
* SignalP
* DeepTMHMM
* AlphaFold
* Schrödinger Suite (Protein Preparation Wizard, SiteMap)

## 🚀 Future Work
* Perform virtual screening (Molecular Docking) against the identified allosteric pocket.
* Conduct Molecular Dynamics (MD) simulations to validate the stability of the protein-ligand complexes.

# Structural Modeling and Allosteric Site Identification of Thyroid Peroxidase (TPO) 🧬
![TPO Protein Visualization](https://github.com/abdulaziz-khaled/Structural-Modeling-and-Allosteric-Site-Identification-of-Thyroid-Peroxidase-TPO-/blob/main/protein_dark_highres.png)

## 📌 Project Overview
Thyroid Peroxidase (TPO) is a crucial enzyme responsible for thyroid hormone synthesis and is the primary target implicated in hypothyroidism and autoimmune thyroid diseases (e.g., Hashimoto's thyroiditis). Due to its large size and complexity, a complete 3D experimentally determined structure is currently unavailable. 

This project aims to computationally model the 3D structure of mature TPO, analyze its topological domains, and identify novel **allosteric binding sites** distant from the catalytic heme region for potential and highly specific drug targeting.

## 🔬 Methodology & Computational Pipeline

The workflow of this project was executed using a combination of bioinformatics tools and molecular modeling software:

### 1. Sequence Analysis & Signal Peptide Cleavage
* **Tool:** SignalP (version used, e.g., 6.0)
* **Action:** The raw amino acid sequence of TPO was analyzed to identify and remove the secretory signal peptide, mimicking the physiological maturation process of the enzyme.
* **Results:** * **Signal Peptide Probability:** 99.98%
    * **Cleavage Site:** Between amino acids 18 and 19.
    * **Outcome:** Residues 1 through 18 were successfully cleaved. The resulting sequence (starting from residue 19) represents the **mature TPO**, which was subsequently used for all downstream topological and structural modeling.


![signal peptide plot](https://github.com/abdulaziz-khaled/Structural-Modeling-and-Allosteric-Site-Identification-of-Thyroid-Peroxidase-TPO-/blob/main/%D9%84%D9%82%D8%B7%D8%A9%20%D8%B4%D8%A7%D8%B4%D8%A9%202026-02-27%20211856.png)

### 2. Transmembrane Topology Prediction
* **Tool:** DeepTMHMM
* **Action:** To understand the spatial orientation and functional regions of the mature TPO enzyme, a comprehensive transmembrane topology prediction was performed. This step is crucial for accurate 3D modeling and ensuring that pocket identification targets the correct physiological domains.
* **Results:** The analysis of the mature TPO sequence revealed a classic single-pass transmembrane architecture, distributed as follows:
    * **Extracellular/Luminal Domain (Outside):** Residues 1 – 831. This massive domain houses the primary catalytic core and the heme-binding region.
    * **Transmembrane Helix (TM):** Residues 832 – 852. A highly hydrophobic alpha-helix responsible for anchoring the enzyme to the apical membrane of thyroid follicular cells.
    * **Intracellular Domain (Inside):** Residues 853 – 915. A short cytosolic tail.
* **Significance:** Accurately mapping these topological domains ensured that downstream structural preparation and allosteric site searches avoided the membrane-embedded TM helix (which is typically poorly druggable) and focused on the accessible extracellular regions.

![plot](https://github.com/abdulaziz-khaled/Structural-Modeling-and-Allosteric-Site-Identification-of-Thyroid-Peroxidase-TPO-/blob/main/%D9%84%D9%82%D8%B7%D8%A9%20%D8%B4%D8%A7%D8%B4%D8%A9%202026-02-27%20213121.png)
![predict](https://github.com/abdulaziz-khaled/Structural-Modeling-and-Allosteric-Site-Identification-of-Thyroid-Peroxidase-TPO-/blob/main/%D9%84%D9%82%D8%B7%D8%A9%20%D8%B4%D8%A7%D8%B4%D8%A9%202026-02-27%20213138.png)

### 3. 3D Structure Generation
* **Tool:** AlphaFold 
* **Action:** Due to the lack of a full PDB structure, a high-confidence 3D model of the mature TPO was generated utilizing AlphaFold's deep learning predictive capabilities.

![Insert Image of your AlphaFold 3D model here](https://github.com/abdulaziz-khaled/Structural-Modeling-and-Allosteric-Site-Identification-of-Thyroid-Peroxidase-TPO-/blob/main/120649A081B0F2E6.png)


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

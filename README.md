# In Silico Structural Characterization and Functional Annotation of an Uncharacterized Hydrothermal Vent Metagenomic Protein (GenBank: CUS43520.1 / UniParc: UPI0007B67DD0)

**Author:** Mohammed Javvad  
**Date:** 01-11-2026  
**Study Type:** Computational Structural Biology & Biocuration Case Study  

---

## 1. Executive Summary
Nearly half of all sequenced proteins in public genomic databases derived from extreme environments remain unannotated as "hypothetical" or "uncharacterized" proteins. In this case study, we performed an *in silico* structural and functional investigation of **CUS43520.1** (UniParc ID: **UPI0007B67DD0**; former UniProtKB ID: **A0A160TFL8**; Gene locus: **MGWOODY_Smn2333**), a 543-amino-acid protein sequenced from a deep-sea hydrothermal vent metagenome that currently has no predicted functional or domain annotations in NCBI or UniProt.

Using **AlphaFold 3** *de novo* structure prediction (`pTM = 0.82`) combined with **Foldseek** 3D structural alignments across experimental (`PDB100`) and predicted (`AFDB50`, `AFDB-SwissProt`) structure databases, we demonstrate that:
1. **CUS43520.1** folds into a rigid, high-confidence bilobal globular architecture containing a well-defined central catalytic cleft.
2. **Resolution of Database Misannotation:** In related bacterial species, homologs of this protein exist as larger (~1,073 aa) two-domain fusion proteins containing an N-terminal Tetratricopeptide Repeat (TPR) domain (residues 1–530) fused to a C-terminal enzymatic domain (residues 531–1073). Automated annotation pipelines mislabeled many of those full-length proteins simply as *"Tetratricopeptide repeat proteins."* Structural alignment proves that **CUS43520.1** lacks the N-terminal TPR region entirely and represents a **standalone 543-aa C-terminal Restriction Endonuclease-like enzyme** (`TM-score = 0.936 – 0.965`).
3. **Conserved Active Site & Fold Topology:** The internal $\alpha/\beta$ core (residues 161–289) shares distant structural topology (`TM-score = 0.561`, `Probability = 0.96`) with an experimentally solved metallopeptidase from the deep-sea submarine volcano bacterium *Idiomarina loihiensis* (`PDB: 4FGM`), while the central cleft houses a strictly conserved putative catalytic motif (`IHSWDEARW...ERWRERFG`).

---

## 2. Target Information ("Before" Status)
* **NCBI GenBank Accession:** `CUS43520.1`
* **UniProt / UniParc Identifier:** `A0A160TFL8` / `UPI0007B67DD0`
* **Gene / Sample Locus Tag:** `MGWOODY_Smn2333`
* **Source Organism:** `hydrothermal vent metagenome`
* **Sequence Length:** 543 amino acids
* **Prior Database Annotation:** Listed as *"hypothetical protein"* (NCBI) and *"Uncharacterized protein — No predicted annotations available"* (UniParc).
![UniParc Baseline Status](01_Sequence_Data/UniParc_UPI0007B67DD0_Baseline.png)

---

## 3. Methodology
1. **Sequence Retrieval:** The 543-residue FASTA sequence (`CUS43520.1`) was retrieved from NCBI GenBank and cross-referenced against UniProtKB/UniParc (`UPI0007B67DD0`).
2. **3D Structure Prediction:** The primary amino acid sequence was submitted to the **AlphaFold 3 Server**. Model quality was evaluated using the predicted Template Modeling score (`pTM`), per-residue confidence (`pLDDT`), and Predicted Aligned Error (`PAE`) matrices.
3. **3D Structural Homology Search:** The top-ranked structural model (`model_0.cif`) was queried against **Foldseek** (`3Di/AA` structural alphabet alignment mode) across 10 structural databases, including `PDB100` (experimentally solved structures), `AFDB-SwissProt` (curated proteins), and `AFDB50`. Structural similarity was quantified using `TM-score`, Root-Mean-Square Deviation (`RMSD`), `E-value`, and alignment probability.

---

## 4. Results & Discussion

### 4.1. AlphaFold 3 Structure & Confidence
AlphaFold 3 converged on a compact, well-ordered 3D structure with a global **`pTM = 0.82`**, substantially exceeding the `0.50` threshold for reliable global fold prediction. Aside from a short flexible N-terminal tail (residues 1–15), the protein exhibits high local confidence (`pLDDT > 90`) across two distinct lobes that pack tightly together (as confirmed by low off-diagonal error in the PAE matrix) to form a central substrate-binding pocket.
![AlphaFold 3 Structure and PAE](02_AlphaFold3_Structure/AlphaFold3_Model0_and_PAE.png)

### 4.2. Structural Alignment & Domain Architecture (`AFDB50`)
Foldseek search against `AFDB50` identified full-length structural homologs with `Probability = 1.00`:
* **Homolog 1 (`AF-A0A4Q1KN06-F1`, *Sphingobium fluviale*):** `TM-score = 0.96549`, `RMSD = 1.99 Å`, `Seq. Id. = 86.9%`, `E-value = 7.41e-83`.
* **Homolog 2 (`AF-A0AA92M3W2-F1`, *Variovorax sp.*):** Annotated as **Restriction endonuclease**; `TM-score = 0.93592`, `RMSD = 2.30 Å`, `Seq. Id. = 36.9%`, `E-value = 4.58e-51`.
![Summary Hits Table](03_Foldseek_Alignments/Table_1_Summary_Hits.png)
![3D Alignment with Restriction Endonuclease A0AA92M3W2](03_Foldseek_Alignments/3_Summary_A0AA92M3W2_Endonuclease.png)

**Key Domain Finding:** Sequence-structure mapping revealed that residue `1` (`MAAAG...`) of **CUS43520.1** aligns starting at residue **`531`** (`A0A4Q1KN06`) and residue **`533`** (`A0AA92M3W2`) of its bacterial homologs. In those organisms, residues `1–530` form an N-terminal Tetratricopeptide Repeat (TPR) scaffolding domain, which caused automated annotation pipelines to mislabel the entire 1,073-aa protein as a *"TPR protein."* **CUS43520.1** lacks the `1–530` TPR domain completely and consists solely of the 543-aa C-terminal **Restriction Endonuclease-like catalytic unit**.

### 4.3. Distant Experimental Fold Match (`PDB100`)
No full-length crystal structure of this protein family currently exists in the Protein Data Bank (`PDB100`). However, local structural alignment of the central $\alpha/\beta$ core (residues `161–289`) matched the crystal structure of an M1-family aminopeptidase/metallopeptidase from the deep-sea hydrothermal vent bacterium ***Idiomarina loihiensis* L2TR** (`PDB: 4FGM`, `Probability = 0.96`, `TM-score = 0.56125`, `RMSD = 4.72 Å`), despite sharing only `11.2%` sequence identity. This confirms a conserved ancestral $\alpha/\beta$ hydrolase/nuclease core scaffold adapted to hydrothermal environments.
![PDB100 Hits Table](03_Foldseek_Alignments/Table_2_PDB100_Hits.png)
![3D Alignment with 4FGM Volcano Enzyme](03_Foldseek_Alignments/1_PDB100_4fgm_VolcanoEnzyme.png)

### 4.4. Identification of Putative Catalytic Motif
Despite `63.1%` overall sequence divergence between **CUS43520.1** and *Variovorax sp.* (`AF-A0AA92M3W2`), structural alignment identified a highly conserved block spanning residues `365–415` inside the central cleft:
`VQSVIDIHSWDEARWKGILYASYGDDVPPIFALTFTNAAGARRIFERWRERFG`
The strict conservation of spatially clustered acidic (`D`, `E`) and basic (`H`, `R`, `K`) residues (`IHSWDEARW`, `SYGDD`, and `ERWRERFG`) strongly indicates a metal-coordinating active site responsible for nucleic acid or peptide cleavage.

---

## 5. Repository Directory Structure
* `01_Sequence_Data/` — Raw NCBI FASTA sequence (`CUS43520.1.fasta`) and UniParc baseline record (`UPI0007B67DD0`).
* `02_AlphaFold3_Structure/` — Top-ranked 3D coordinate file (`model_0.cif`), confidence metrics (`summary_confidences_0.json`), PAE matrix data (`full_data_0.json`), and structure visualization.
* `03_Foldseek_Alignments/` — Full tabular Foldseek alignment archives (`.m8` tables across all databases), 3D superposition files (`.cif`), and structural alignment renderings (`.png`) for `4FGM`, `A0A4Q1KN06`, and `A0AA92M3W2`.
* `04_Final_Report/` — Complete case study documentation.
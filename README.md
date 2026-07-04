# HyperMeltome Dataset

This repository contains the **HyperMeltome** dataset, a curated high-temperature protein melting temperature ($T_m$) dataset introduced in the paper: *HyperThermNet: Prediction of Thermophilic Protein Melting Temperatures via Adaptive Dual-Graph and Structural Thermal Relaxation*.

Please note that this repository **only provides the dataset** for public access and reproducibility. The model source code is kept private.

## 📊 Dataset Overview

The HyperMeltome dataset is specifically targeted at the high-temperature domain ($50^\circ\text{C} \le T_m \le 100^\circ\text{C}$) to facilitate the prediction and engineering of thermophilic proteins. It was carefully curated from the Meltome Atlas to address common issues such as long-tail distribution, label noise, and information leakage.

**Dataset Statistics:** 

* **Total Sequences:** 3,295
* **Training Set:** 2,636
* **Test Set:** 659

## 🧠 HyperThermNet Architecture

<img width="330" height="299" alt="model_0703" src="https://github.com/user-attachments/assets/1aa68922-1b08-4f52-bedb-d16a2c76cc98" />

## 🛠️ Data Construction & Preprocessing

To ensure high-quality and unbiased data, we implemented a stringent quality-control and debiasing pipeline:

* 
**Basic Filtering:** Excluded records with missing $T_m$ values, non-standard UniProt identifiers, or anomalous sequences containing non-standard amino acids (e.g., B, J, O, U).


* 
**Length Constraint:** Restricted protein sequence lengths to a maximum of 1,000 residues.


* 
**Quality Assurance:** Retained high-confidence records with a thermal denaturation curve goodness-of-fit $R^2 > 0.9$ and preferentially selected measurements from cells.


* 
**Noise Reduction:** Excluded controversial samples where the $T_m$ range across different experimental batches or microenvironments exceeded $5.0^\circ\text{C}$.


* 
**Homology Reduction:** Applied the CD-HIT algorithm at a 40% sequence identity threshold to cluster and remove redundant sequences.


* 
**Distribution Debiasing:** Applied a uniform undersampling strategy to the densely populated $50^\circ\text{C}$--$60^\circ\text{C}$ interval, retaining 1,500 representative sequences.



## 📁 File Structure & Data Format

* `HyperMeltome.csv` : The main dataset file containing the protein sequences and their corresponding thermal properties.

The CSV file contains the following core columns:
* `uniprot_id`: The unique UniProt identifier for the protein.
* `tm`: The experimentally measured melting temperature (Tm) in Celsius.
* `ogt`: The optimal growth temperature (OGT) of the source organism in Celsius.
* `seq_length`: The length of the amino acid sequence.
* `sequence`: The complete amino acid sequence of the protein.


## 📄 License

This dataset is released under the MIT License - see the LICENSE file for details.

# GPCR_DB_project
Random Forest Classifier for Prediction of G Protein-coupled Receptor (GPCR) Ligand Function

## Description

This GitHub repository houses Python scripts/Jupyter notebooks that will allow for the prediction of a ligand's function based on its experimentally determined/docked binding mode in complex with a GPCR structure. Ideally, this model is meant to predict the funciton of potential GPCR screening candidates that have been docked into an experimentally determined/modeled structure of a GPCR.

## Getting Started

### Dependencies

* Python libraries: sklearn >= v0.24.2, pandas, numpy, joblib
* Molecular Operating Environment (MOE) for ligand docking/running SVL scripts necessary for extraction of interaction energies/types from a ligand-GPCR complex

### Executing program (more detailed steps are listed in ligand_fxn_prediction_tutorial.docx)

1. Use MOE to generate 5 docked poses per ligand docked into a GPCR structure.
2. Create a field named 'Target' in the output docking database that denotes the name of each target docked into
3. Index entries in the docking database using *loopnumber.svl*.
4. Create transmembrane (TM) domain residue position indexing database with *create_indexing_mdb.svl*.
5. Fill in the TM domain residue position database with TM start/end/x.50 residue numbers retrieved from visual inspection and [GPCRdb](https://gpcrdb.org).
6. Use *dockdb_to_lf_input.svl* to extract interaction energies/types into a .txt file for each residue position present in each docked ligand-GPCR complex in the docking database.
7. Use *LFP_classifier.py* to make per ligand predictions of ligand function using the .txt file containing interaction enegies/types.

**LFP_classifier.py usage from Windows CMD**
```
python LFP_classifier.py <textfile>
```

where ```<textfile>``` is the .txt file resulting from running *dockdb_to_lf_input.svl*. 

## Output

Per ligand predictions of ligand function will be written to a .csv file.

## Authors

Gregory Szwabowski (gszwabowski@gmail.com)

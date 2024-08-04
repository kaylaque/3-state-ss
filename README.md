# Prediction of three-State Secondary Structure Protein (SSP) using Bi-LSTM and AutoGluon
## What is 3-State Secondary Structure Protein?
Proteins play an important role in life, from DNA repair to enzyme catalysts. Proteins serve to build and repair cells in the body as well as energy production. Proteins have a complex structure consisting of a series of amino acids. The protein structure consists of 4 main structures, namely primary structure (a series of amino acids from peptide bonds), secondary structure (a series of amino acids forming a circular structure), tertiary structure (a combination of the folding results of several different secondary structures), and quarternary. Protein secondary structure is one of the important parts in bioinformatics as the first step in protein tertiary structure prediction. Through the prediction of protein secondary structure, protein activity, relation, and function can be known.

## Why is that matter to have ability to predict that?
Protein secondary structure can be calculated based on the 3D coordinates of protein tertiary structure atoms. Protein tertiary structure is obtained through X-Ray crystallography or NMR [2]. In determining the secondary structure of a protein, DSSP (Dictionary of Secondary Structure) is used which summarizes the types of secondary structures consisting of 8-state and 3-state. The DSSP algorithm processes tertiary structures into several groupings of secondary structures with the known primary structure of the protein. However, sampling with X-Ray crystallography and NMR is quite expensive. Therefore, a more comprehensive and affordable protein secondary structure prediction is needed as a one step closer to bridge the barriers of protein tertiary structure data gathering.


[The SSP algorithm](https://2struc.cryst.bbk.ac.uk/about/) works by calculating the most likely secondary structure if there is a tertiary structure of the protein by knowing the position of the atoms in the protein followed by calculating the Hydrogen bond between all atoms. The algorithm disqualifies the Hydrogen in the incoming primary structure and then gets the most optimal Hydrogen position by placing it at 1000 Avogadro from the Nitrogen backbone in the opposite direction to the backbone of the carbon-oxygen double bond.

## Flow of Case Model Development
Dataset used can be access from [Kaggle](https://www.kaggle.com/datasets/alfrandom/protein-secondary-structure/data). The dataset is dataset extracted from RCSB (Research Collaboratory for Structural Bioinformatics) PDB (Protein Data Bank) per 2018. For this case, the prediction only on 3-state SSP
### Pipeline for AutoGlon-based
1. Pre-processing data : padding sequences, orthogonal encode, graph network, window padding slide
2. AutoGluon classifier
3. Optimization Hyperparameter using Optuna
### Pipeline for Bi-LSTM-based
1. Pre-processing data : filter, N-Grams, Tokenization, Post padding sequences
2. Bi-LSTM architecture and training
3. Optimization Hyperparameter using Optuna

# Structure-Based Drug Designing and Molecular Docking on Influenza Virus

A computational study that uses structure-based drug design (SBDD) to evaluate **sucrose (PubChem CID 5988)** as a potential lead compound against three key influenza virus proteins.

> **Note:** This is an in silico study. All findings are computational predictions and have not been validated experimentally.

## Overview

Influenza remains a major global health problem because of high mutation rates and growing drug resistance. This project screens a small ligand library and docks the selected compound against proteins involved in three stages of the viral life cycle: entry, release, and uncoating.

## Target Proteins

| Protein | PDB ID | Role in viral life cycle | Method | Resolution |
|---|---|---|---|---|
| Hemagglutinin (HA) | 1HGE | Host cell attachment and membrane fusion (entry) | X-ray | 2.60 Å |
| Neuraminidase (NA) | 1NNB | Release of new virions | X-ray | 2.80 Å |
| M2 proton channel | 3BKD | Viral uncoating | NMR / X-ray | 2.05 Å |

## Workflow

1. Target identification and selection (BV-BRC, literature)
2. Retrieval of 3D structures (RCSB PDB)
3. Protein preparation (water removal, polar hydrogens, Kollman charges, energy minimization, PDBQT conversion)
4. Ligand library construction (ChemMine, similarity search on NAG and BOG)
5. Drug-likeness screening (DrugMint, SVM model)
6. Molecular docking (SwissDock) and visualization (UCSF Chimera)
7. Protein-ligand interaction analysis
8. Normal Mode Analysis (iMODS)
9. ADMET and drug-likeness prediction (SwissADME)

## Tools and Databases

| Purpose | Tool |
|---|---|
| Viral data | [BV-BRC](https://www.bv-brc.org/) |
| Protein structures | [RCSB PDB](https://www.rcsb.org/) |
| Ligand data | [PubChem](https://pubchem.ncbi.nlm.nih.gov/) |
| Library preparation | [ChemMine Tools](http://chemmine.ucr.edu/) |
| Drug-likeness | [DrugMint](http://crdd.osdd.net/oscadd/drugmint/) |
| Docking | [SwissDock](http://www.swissdock.ch/), [AutoDock](http://autodock.scripps.edu/) |
| Visualization | [UCSF Chimera](https://www.cgl.ucsf.edu/chimera/) |
| Protein dynamics (NMA) | [iMODS](http://imods.chaconlab.org/) |
| ADME properties | [SwissADME](http://www.swissadme.ch/) |

## Key Results

### Docking (SwissDock)

| Protein | PDB ID | Best ΔG (kcal/mol) | H-bonds | Interacting residues | Distance (Å) |
|---|---|---|---|---|---|
| Hemagglutinin | 1HGE | −7.71 | 2 | LYS 315, THR 313 | 2.186, 2.293 |
| Neuraminidase | 1NNB | −7.63 | 1 | PHE 469 | 1.889 |
| M2 channel | 3BKD | −7.16 | 0 | none (hydrophobic and van der Waals contacts suggested) | n/a |

### Normal Mode Analysis (iMODS)

- **1HGE:** moderate flexibility in loop regions with a stable core
- **1NNB:** lowest deformability, most rigid structure
- **3BKD:** highest flexibility, consistent with its role as a dynamic ion channel

### ADMET (SwissADME)

- Molecular formula C₁₂H₂₂O₁₁, MW 342.30 g/mol
- Consensus Log P −3.29 (highly hydrophilic), TPSA 189.53 Å²
- Highly water soluble; low GI absorption; not BBB permeable; P-gp substrate
- No CYP450 inhibition predicted; no PAINS or Brenk alerts
- Violates Lipinski (2), Veber, Egan, and Muegge rules; bioavailability score 0.17

## Limitations

- Results are based on docking scores and NMA only, with no experimental validation.
- iMODS performs normal mode analysis, which is not equivalent to full molecular dynamics simulation (no RMSD/RMSF trajectories).
- Sucrose shows poor predicted oral bioavailability and violates several drug-likeness rules, so it is better viewed as a scaffold for optimization than a ready drug candidate.
- Docking was performed on single structures and may not reflect resistant or emerging strains.

## Future Scope

- Screen a larger and more diverse ligand library
- Validate with multiple docking engines and consensus scoring
- Run true MD simulations (RMSD, RMSF) and MM-PBSA / MM-GBSA binding free energy calculations
- Test against mutant and drug-resistant strains (e.g., M2 S31N)
- Lead optimization and multi-target design (HA-NA-M2)
- In vitro and in vivo antiviral and cytotoxicity assays

## Repository Contents

```
├── README.md
└── Influenza_SBDD_Docking_Report.pdf   # Full project report
```

## Keywords

Influenza virus · Structure-Based Drug Design · Molecular Docking · Hemagglutinin · Neuraminidase · M2 protein · Normal Mode Analysis · SwissADME · Antiviral drug discovery

## Citation / Author

*Add your name, institution, and year here.*

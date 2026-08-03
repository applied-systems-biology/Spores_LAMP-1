# Co-localization of LAMP-1 (Lysosome-Associated Membrane Protein 1) and Fungal Spores and Hyphae

## Overview
This pipeline provides object-based and intensity-based colocalization analysis between LAMP-1 and fungal spores in fluorescence microscopy images at macrophage levels.

![Representative analysis](Representative%20analysis.PNG)

## Microscopy Data Structure
The pipeline expects four-channel microscopy images with the following channel order:
| Channel | Description |
|----------|-------------|
| CH1 | LAMP-1 |
| CH2 | Brightfield |
| CH3 | Macrophage |
| CH4 | Fungal spores |

## Experimental Conditions
The pipeline has been developed and tested on:
#### timepoints:
- 2 h, and 6 h post-infection
#### organisms:
- Aspergillus fumigatus wild type
- Aspergillus fumigatus ΔpksP
- Lichtheimia

## Analysis Workflow
Required Input
The analysis requires the following segmentation masks:
Macrophage segmentation masks generated from the fluorescence channel using the accompanying JIPipe workflow.
Hyphae segmentation masks generated from the brightfield channel using a trained deep learning model. The repository for the deep learning GUI is available at: [GitHub repository link here].

1. Load microscopy images and segmentation masks of macrophages and hyphae.
2. Identify individual macrophages using the provided labeled segmentation.
3. Binarize the fungal spore channel and applied watershed to resolve overlapping structures.
4. Binarize the LAMP-1 channel.
5. Measure overlap between engulfed fungal spores and LAMP-1 signal.
6. Calculate object-based and intensity-based colocalization metrics.

![Colocalization ratios](Colocalization%20ratios.PNG)

## Outputs
The pipeline generates:
- Intensity-based Colocalization ratio per macrophage
- Object-based Colocalization ratio per macrophage

## Software and Packages
The analysis was developed in Python using:
- NumPy
- Pandas
- SciPy
- scikit-image
- Matplotlib
- Seaborn
- czifile
- scikit-posthocs



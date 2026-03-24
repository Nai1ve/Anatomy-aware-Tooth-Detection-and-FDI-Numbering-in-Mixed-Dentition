# Anatomy-aware Tooth Detection and FDI Numbering in Mixed Dentition

This repository serves as the main entry point for the code accompanying the manuscript:

**An Anatomy-aware Perception-Reasoning Framework for Tooth Detection and FDI Numbering in Mixed-Dentition Panoramic Radiographs**

## Overview

Automatic tooth detection and Fédération Dentaire Internationale (FDI) numbering in pediatric mixed dentition is challenging because of physiological root resorption, eruption of permanent teeth, crowding, overlap, and substantial anatomical variability. In this study, we formulate mixed-dentition tooth numbering as an anatomically constrained assignment problem rather than a purely visual detection task.

To address this problem, we develop a two-stage anatomy-aware framework:

1. **Detection stage**  
   A detector is used to generate high-recall tooth candidates from panoramic radiographs. To better preserve primary-tooth candidates in mixed dentition, a class-conditional spatially weighted loss is introduced.

2. **Reasoning stage**  
   Candidate detections are then represented as a multi-relational anatomical graph. A graph-based reasoning module is used to refine the final FDI numbering by leveraging anatomical relationships such as overlap competition, dental-arch adjacency, same-jaw neighborhood, and spatial proximity.

3. **Evaluation stage**  
   In addition to conventional detection metrics, the framework is evaluated with task-oriented metrics, including Numbering Accuracy (NA) and fine-grained error analysis, to better reflect final numbering quality.

## Framework

Please place the architecture figure in this repository and update the image path below if needed.

![Framework Overview](docs/framework.png)

> Suggested location: `docs/framework.png`

## Repository Structure

This project is organized into three component repositories:

### 1. Detector
Code for tooth candidate detection on mixed-dentition panoramic radiographs.

**Repository:**  
[https://github.com/Nai1ve/mmdetection-dental](https://github.com/Nai1ve/mmdetection-dental)

**Main functions:**
- detector training
- detector inference
- candidate generation for downstream reasoning

---

### 2. Graph Construction and Reasoning
Code for graph construction and graph-based reasoning for anatomically consistent FDI numbering.

**Repository:**  
[https://github.com/Nai1ve/gnn-dental](https://github.com/Nai1ve/gnn-dental)

**Main functions:**
- graph construction from detector outputs
- node and edge feature preparation
- graph neural network training and inference
- relational correction of tooth numbering

---

### 3. Evaluation
Code for evaluation and error analysis.

**Repository:**  
[https://github.com/Nai1ve/TeethDataProcess](https://github.com/Nai1ve/TeethDataProcess)

**Main functions:**
- conventional detection metrics
- Numbering Accuracy (NA)
- fine-grained error analysis
- result summarization and statistics

## Workflow

The overall workflow is as follows:

1. Run the **Detector** repository to train the detector or generate candidate tooth detections.
2. Use the detector outputs as input for the **Graph Construction and Reasoning** repository.
3. Run the graph reasoning module to refine final FDI numbering.
4. Use the **Evaluation** repository to compute detection metrics, numbering accuracy, and fine-grained error statistics.

## Data Availability

The imaging data used in this study are not publicly available due to patient privacy and institutional restrictions.

## Code Availability

The code is publicly available through the three repositories listed above.

## Citation

If you find this work useful, please cite the corresponding manuscript:

## Acknowledgements
The detector component of this project is built upon the excellent open-source toolbox MMDetection.

We sincerely thank the MMDetection contributors and the OpenMMLab community for providing a powerful and well-maintained detection framework:
- MMDetection: https://github.com/open-mmlab/mmdetection￼
- OpenMMLab: https://github.com/open-mmlab￼
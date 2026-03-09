# Glossary

> Part of: ** Detecting Objects in Lidar**

## Additional Content

## Terms and Symbols
In this section, you will find a list of abbreviations and technical expressions used in the lesson. For further details and an in-depth explanation, please refer to the respective sections.

- **Frustum** : In geometry, a frustum is the portion of a cone or pyramid that lies between one or two parallel planes cutting it.
- **Voxel** : (Volume Element) Represents a value on a regular grid in three-dimensional space.
- **MLP** : multi-layer perceptrons
- **CNN** : Convolutional Neural Networks
- **YOLO**  : "You Only Look Once" is a system for detecting objects based on deep-learning.
- **BEV** : Birds-eye view
- **TP** : True positive
- **TN** : True negative
- **FP** : False positive
- **FN** : False negative
- **IoU** : Intersection-over-Union
- **mAP** : Mean Average Precision
## Equations
**BEV map properties**: 

- Height

$H_{i,j} = \max\left(P_{i,j} \cdot \left[0,0,1\right]T\right)$

- Intensity

$I_{i,j} = \max\left(I\left(P_{i,j}\right)\right)$

- Density

$D_{i,j} = \min\left( 1.0, \frac{\log(N+1)}{64}\right)$

$P_{ij}$

is the set of points  that falls into each cell, with

$i,j$

as the respective cell coordinates.

$N_{i,j}$

refers to the number of points in a cell.

----
**Precision and recall**: 

Precision:

$P = \frac{TP}{TP + FP}$

Recall:

$R = \frac{TP}{TP + FN}$

Accuracy:

$A = \frac{TP+TN}{TP+TN+FP+FN}$

TP, TN, FP and FN are the "true positives", "true negatives", "false positives" and "false negatives". 

---
**Average Precision**

$AP=\frac{1}{n}\sum_{\mathrm{Recall}_i} \mathrm{Precision}(\mathrm{Recall}_i)$

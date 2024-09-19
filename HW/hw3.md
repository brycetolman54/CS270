---
geometry: "margin=0.5in"
---
# Quadric Machine

|   x   y   xx   yy    xy  b | Target |              Weights           |  Net  | Output |           deltaWeights             |
| :------------------------: | :----: | :----------------------------: | :---: | :----: | :--------------------------------: |
|   0  0.4   0  0.16   0   1 |   0    |   0    0    0    0     0    0  |   0   |    0   |   0     0     0     0     0     0  |
| -0.1 1.2 0.01 1.44 -0.12 1 |   1    |   0    0    0    0     0    0  |   0   |    0   | -0.05  0.6  0.005  0.72 -0.06  0.5 |
|  0.5 0.8 0.25 0.64  0.4  1 |   0    | -0.05 0.6 0.005 0.72 -0.06 0.5 |  1.39 |    1   | -0.25 -0.4 -0.125 -0.32  -0.2 -0.5 |

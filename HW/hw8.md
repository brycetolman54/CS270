---
geometry: "margin=1in"
---

# K Nearest Neighbors Homework

- Using `k = 3`
- Using the Manhattan distance

|   X   |   Y   | Class | Regression | Distance | Weight |
| :---: | :---: | :---: | :--------: | :------: | :----: |
|  0.3  |  0.8  |   A   |     0.6    |    0.8   |  1.56  |
| -0.3  |  1.6  |   B   |    -0.3    |    2.2   |  0.21  |
|  0.9  |   0   |   B   |     0.8    |    0.6   |  2.78  |
|   1   |   1   |   A   |     1.2    |    1.3   |  0.59  |

- The new point is (0.5, 0.2)

- Class with no distance weighting: A
    - 2A and 1B
- Class with distance weighting: B
    - 2.15A and 2.78B
- Regression with no distance weighting: 0.87
    - (0.6 + 0.8 + 1.2) / 3
- Regression with distance weighting: 0.78
    - (1.56 * 0.6 + 2.78 * 0.8 + 0.59 * 1.2) / (1.56 + 2.78 + 0.59)

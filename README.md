# QAP-instance-Genetic-algorithm
Solving a QAP instance using genetic algorithms

What is QAP?

The quadratic assignment problem (QAP) is one of the fundamental combinatorial optimization problems in the branch of optimization or operations research in mathematics, from the category of the facilities location problems first introduced by Koopmans and Beckmann.

The problem models the following real-life problem:

There are a set of n facilities and a set of n locations. For each pair of locations, a distance is specified and for each pair of facilities a weight or flow is specified (e.g., the amount of supplies transported between the two facilities). The problem is to assign all facilities to different locations with the goal of minimizing the sum of the distances multiplied by the corresponding flows.
Intuitively, the cost function encourages facilities with high flows between each other to be placed close together.

The instance of the QAP problem with 25 facilities and locations is given by the following data.

**Distance matrix:**


| 0 | 1 | 2 | 3 | 4 | 1 | 2 | 3 | 4 | 5 | 2 | 3 | 4 | 5 | 6 | 3 | 4 | 5 | 6 | 7 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 0 | 1 | 2 | 3 | 2 | 1 | 2 | 3 | 4 | 3 | 2 | 3 | 4 | 5 | 4 | 3 | 4 | 5 | 6 | 5 | 4 | 5 | 6 | 7 |
| 2 | 1 | 0 | 1 | 2 | 3 | 2 | 1 | 2 | 3 | 4 | 3 | 2 | 3 | 4 | 5 | 4 | 3 | 4 | 5 | 6 | 5 | 4 | 5 | 6 |
| 3 | 2 | 1 | 0 | 1 | 4 | 3 | 2 | 1 | 2 | 5 | 4 | 3 | 2 | 3 | 6 | 5 | 4 | 3 | 4 | 7 | 6 | 5 | 4 | 5 |
| 4 | 3 | 2 | 1 | 0 | 5 | 4 | 3 | 2 | 1 | 6 | 5 | 4 | 3 | 2 | 7 | 6 | 5 | 4 | 3 | 8 | 7 | 6 | 5 | 4 |
| 1 | 2 | 3 | 4 | 5 | 0 | 1 | 2 | 3 | 4 | 1 | 2 | 3 | 4 | 5 | 2 | 3 | 4 | 5 | 6 | 3 | 4 | 5 | 6 | 7 |
| 2 | 1 | 2 | 3 | 4 | 1 | 0 | 1 | 2 | 3 | 2 | 1 | 2 | 3 | 4 | 3 | 2 | 3 | 4 | 5 | 4 | 3 | 4 | 5 | 6 |
| 3 | 2 | 1 | 2 | 3 | 2 | 1 | 0 | 1 | 2 | 3 | 2 | 1 | 2 | 3 | 4 | 3 | 2 | 3 | 4 | 5 | 4 | 3 | 4 | 5 |
| 4 | 3 | 2 | 1 | 2 | 3 | 2 | 1 | 0 | 1 | 4 | 3 | 2 | 1 | 2 | 5 | 4 | 3 | 2 | 3 | 6 | 5 | 4 | 3 | 4 |
| 5 | 4 | 3 | 2 | 1 | 4 | 3 | 2 | 1 | 0 | 5 | 4 | 3 | 2 | 1 | 6 | 5 | 4 | 3 | 2 | 7 | 6 | 5 | 4 | 3 |
| 2 | 3 | 4 | 5 | 6 | 1 | 2 | 3 | 4 | 5 | 0 | 1 | 2 | 3 | 4 | 1 | 2 | 3 | 4 | 5 | 2 | 3 | 4 | 5 | 6 |
| 3 | 2 | 3 | 4 | 5 | 2 | 1 | 2 | 3 | 4 | 1 | 0 | 1 | 2 | 3 | 2 | 1 | 2 | 3 | 4 | 3 | 2 | 3 | 4 | 5 |
| 4 | 3 | 2 | 3 | 4 | 3 | 2 | 1 | 2 | 3 | 2 | 1 | 0 | 1 | 2 | 3 | 2 | 1 | 2 | 3 | 4 | 3 | 2 | 3 | 4 |
| 5 | 4 | 3 | 2 | 3 | 4 | 3 | 2 | 1 | 2 | 3 | 2 | 1 | 0 | 1 | 4 | 3 | 2 | 1 | 2 | 5 | 4 | 3 | 2 | 3 |
| 6 | 5 | 4 | 3 | 2 | 5 | 4 | 3 | 2 | 1 | 4 | 3 | 2 | 1 | 0 | 5 | 4 | 3 | 2 | 1 | 6 | 5 | 4 | 3 | 2 |
| 3 | 4 | 5 | 6 | 7 | 2 | 3 | 4 | 5 | 6 | 1 | 2 | 3 | 4 | 5 | 0 | 1 | 2 | 3 | 4 | 1 | 2 | 3 | 4 | 5 |
| 4 | 3 | 4 | 5 | 6 | 3 | 2 | 3 | 4 | 5 | 2 | 1 | 2 | 3 | 4 | 1 | 0 | 1 | 2 | 3 | 2 | 1 | 2 | 3 | 4 |
| 5 | 4 | 3 | 4 | 5 | 4 | 3 | 2 | 3 | 4 | 3 | 2 | 1 | 2 | 3 | 2 | 1 | 0 | 1 | 2 | 3 | 2 | 1 | 2 | 3 |
| 6 | 5 | 4 | 3 | 4 | 5 | 4 | 3 | 2 | 3 | 4 | 3 | 2 | 1 | 2 | 3 | 2 | 1 | 0 | 1 | 4 | 3 | 2 | 1 | 2 |
| 7 | 6 | 5 | 4 | 3 | 6 | 5 | 4 | 3 | 2 | 5 | 4 | 3 | 2 | 1 | 4 | 3 | 2 | 1 | 0 | 5 | 4 | 3 | 2 | 1 |
| 4 | 5 | 6 | 7 | 8 | 3 | 4 | 5 | 6 | 7 | 2 | 3 | 4 | 5 | 6 | 1 | 2 | 3 | 4 | 5 | 0 | 1 | 2 | 3 | 4 |
| 5 | 4 | 5 | 6 | 7 | 4 | 3 | 4 | 5 | 6 | 3 | 2 | 3 | 4 | 5 | 2 | 1 | 2 | 3 | 4 | 1 | 0 | 1 | 2 | 3 |
| 6 | 5 | 4 | 5 | 6 | 5 | 4 | 3 | 4 | 5 | 4 | 3 | 2 | 3 | 4 | 3 | 2 | 1 | 2 | 3 | 2 | 1 | 0 | 1 | 2 |
| 7 | 6 | 5 | 4 | 5 | 6 | 5 | 4 | 3 | 4 | 5 | 4 | 3 | 2 | 3 | 4 | 3 | 2 | 1 | 2 | 3 | 2 | 1 | 0 | 1 |
| 8 | 7 | 6 | 5 | 4 | 7 | 6 | 5 | 4 | 3 | 6 | 5 | 4 | 3 | 2 | 5 | 4 | 3 | 2 | 1 | 4 | 3 | 2 | 1 | 0 |


**Flow matrix:**

| 0 | 3  | 2 | 0 | 0  | 10 | 5  | 0  | 5  | 2 | 0 | 0  | 2  | 0 | 5  | 3  | 0  | 1 | 10 | 0 | 2  | 1  | 1  | 1  | 0  |
|---|----|---|---|----|----|----|----|----|---|---|----|----|---|----|----|----|---|----|---|----|----|----|----|----|
| 3 | 0  | 4 | 0 | 10 | 0  | 0  | 2  | 2  | 1 | 5 | 0  | 0  | 0 | 0  | 0  | 1  | 6 | 1  | 0 | 2  | 2  | 5  | 1  | 10 |
| 2 | 4  | 0 | 3 | 4  | 5  | 5  | 5  | 1  | 4 | 0 | 4  | 0  | 4 | 0  | 3  | 2  | 5 | 5  | 2 | 0  | 0  | 3  | 1  | 0  |
| 0 | 0  | 3 | 0 | 0  | 0  | 2  | 2  | 0  | 6 | 2 | 5  | 2  | 5 | 1  | 1  | 1  | 2 | 2  | 4 | 2  | 0  | 2  | 2  | 5  |
| 0 | 10 | 4 | 0 | 0  | 2  | 0  | 0  | 0  | 0 | 0 | 0  | 0  | 0 | 2  | 0  | 0  | 2 | 0  | 5 | 0  | 2  | 1  | 0  | 2  |
| 0 | 5  | 0 | 2 | 0  | 10 | 10 | 5  | 10 | 6 | 0 | 0  | 10 | 2 | 10 | 1  | 5  | 5 | 2  | 5 | 0  | 2  | 0  | 1  | 10 |
| 5 | 0  | 5 | 2 | 0  | 10 | 0  | 1  | 3  | 5 | 0 | 0  | 2  | 4 | 5  | 10 | 6  | 0 | 5  | 5 | 5  | 0  | 5  | 5  | 0  |
| 0 | 2  | 5 | 2 | 0  | 10 | 1  | 0  | 10 | 2 | 5 | 2  | 0  | 3 | 0  | 0  | 0  | 4 | 0  | 5 | 0  | 5  | 2  | 2  | 5  |
| 5 | 2  | 1 | 0 | 0  | 5  | 3  | 10 | 0  | 5 | 6 | 0  | 1  | 5 | 5  | 5  | 2  | 3 | 5  | 0 | 2  | 10 | 10 | 1  | 5  |
| 2 | 1  | 4 | 6 | 0  | 10 | 5  | 2  | 5  | 0 | 0 | 1  | 2  | 1 | 0  | 0  | 0  | 0 | 6  | 6 | 4  | 5  | 3  | 2  | 2  |
| 0 | 5  | 0 | 2 | 0  | 6  | 0  | 5  | 6  | 0 | 0 | 2  | 0  | 4 | 2  | 1  | 0  | 6 | 2  | 1 | 5  | 0  | 0  | 1  | 5  |
| 0 | 0  | 4 | 5 | 0  | 0  | 0  | 2  | 0  | 1 | 2 | 0  | 2  | 1 | 0  | 3  | 10 | 0 | 0  | 4 | 0  | 0  | 4  | 2  | 5  |
| 2 | 0  | 0 | 2 | 0  | 0  | 2  | 0  | 1  | 2 | 0 | 2  | 0  | 4 | 5  | 0  | 1  | 0 | 5  | 0 | 0  | 0  | 5  | 1  | 1  |
| 0 | 0  | 4 | 5 | 0  | 10 | 4  | 3  | 5  | 1 | 4 | 1  | 4  | 0 | 0  | 0  | 2  | 2 | 0  | 2 | 5  | 0  | 5  | 2  | 5  |
| 5 | 0  | 0 | 1 | 2  | 2  | 5  | 0  | 5  | 0 | 2 | 0  | 5  | 0 | 0  | 2  | 0  | 0 | 0  | 6 | 3  | 5  | 0  | 0  | 5  |
| 3 | 0  | 3 | 1 | 0  | 10 | 10 | 0  | 5  | 0 | 1 | 3  | 0  | 0 | 2  | 0  | 0  | 5 | 5  | 1 | 5  | 2  | 1  | 2  | 10 |
| 0 | 1  | 2 | 1 | 0  | 1  | 6  | 0  | 2  | 0 | 0 | 10 | 1  | 2 | 0  | 0  | 0  | 5 | 2  | 1 | 1  | 5  | 6  | 5  | 5  |
| 1 | 6  | 5 | 2 | 2  | 5  | 0  | 4  | 3  | 0 | 6 | 0  | 0  | 2 | 0  | 5  | 5  | 0 | 4  | 0 | 0  | 0  | 0  | 5  | 0  |
| 1 | 5  | 2 | 0 | 5  | 5  | 0  | 5  | 6  | 2 | 0 | 5  | 0  | 0 | 5  | 2  | 4  | 0 | 5  | 4 | 4  | 5  | 0  | 2  | 10 |
| 0 | 0  | 2 | 4 | 5  | 2  | 5  | 5  | 0  | 6 | 1 | 4  | 0  | 2 | 6  | 1  | 1  | 0 | 5  | 0 | 4  | 4  | 1  | 0  | 2  |
| 2 | 2  | 0 | 2 | 0  | 5  | 5  | 0  | 2  | 4 | 5 | 0  | 0  | 5 | 3  | 5  | 1  | 0 | 4  | 4 | 0  | 1  | 0  | 10 | 1  |
| 1 | 2  | 0 | 0 | 2  | 0  | 0  | 5  | 10 | 5 | 0 | 0  | 0  | 0 | 5  | 2  | 5  | 0 | 4  | 4 | 1  | 0  | 0  | 0  | 0  |
| 1 | 5  | 3 | 2 | 1  | 2  | 5  | 2  | 10 | 3 | 0 | 4  | 5  | 5 | 0  | 1  | 6  | 0 | 5  | 1 | 0  | 0  | 0  | 0  | 0  |
| 1 | 1  | 1 | 2 | 0  | 0  | 5  | 2  | 1  | 2 | 1 | 2  | 1  | 2 | 0  | 2  | 5  | 5 | 0  | 0 | 10 | 0  | 0  | 0  | 2  |
| 0 | 10 | 0 | 5 | 2  | 1  | 0  | 5  | 5  | 2 | 5 | 5  | 1  | 5 | 5  | 10 | 5  | 0 | 2  | 2 | 1  | 0  | 0  | 2  | 0  |

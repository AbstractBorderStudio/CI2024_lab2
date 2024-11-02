# 1. Computational Intelligence CI2024_lab2

- [1. Computational Intelligence CI2024\_lab2](#1-computational-intelligence-ci2024_lab2)
  - [1.1. Lab's Objective](#11-labs-objective)
  - [1.2. The problem](#12-the-problem)
    - [1.2.1. Representation](#121-representation)
  - [1.3. Solution #1: Nearest neighbor approach](#13-solution-1-nearest-neighbor-approach)
    - [RESULTS!](#results)
  - [1.4. Solution #2: Greedy approach](#14-solution-2-greedy-approach)
  - [1.5. Solution #3: EA approach](#15-solution-3-ea-approach)

## 1.1. Lab's Objective

> - Solve the given TSP instances using both a <u>fast but approximate algorithm</u> and a <u>slower, yet more accurate one</u>.
> - Report the final cost and the number of steps.

## 1.2. The problem

> *"Given a list of cities and the distances between each pair of cities, what is the shortest possible route that visits each city exactly once and returns to the origin city?"*

- [TSP solutions for the given countries - Wolfram](https://www.wolframcloud.com/obj/giovanni.squillero/Published/Lab2-tsp.nb).

The shortest paths are:

| Region  | #cities | Shortest_path (km) |
|---------|---------|--------------------|
| Vanuatu | 8       | 1345.64            |
| Italy   | 46      | 4172.76            |
| Russia  | 167     | 32722.5            |
| US      | 340     | 3901662065726,7    |
| China   | 746     | ???                |


I'll leave here some resources used in my research:

- [Travelling salesman problem - Wikipedia](https://en.wikipedia.org/wiki/Travelling_salesman_problem)
- [What is the Traveling Salesman Problem? - Youtube](https://www.youtube.com/watch?v=1pmBjIZ20pE&ab_channel=AlphaOpt)
- [The Traveling Salesman Problem: When Good Enough Beats Perfect - Youtube](https://www.youtube.com/watch?app=desktop&v=GiDsjIBOVoA&ab_channel=Reducible)

### 1.2.1. Representation

The cities' info is loaded form a csv file into a `Dataframe`.

> We can represent the solution as a list of city indexes. So it is a <u>fixed leght integer array representation</u>.

## 1.3. Solution #1: Nearest neighbor approach

I started my research by re-implementing the simplest solution seen during the lectures.

- First, pick a random city from the avaible cities.
- Then, choose the nearest neighbor until we cover all the cities.

The only thing I added was a cycle to optimize the distanze and get the optimum.

```py
EPOCHS = 1000
tsp_sol, cost = _nn_approach(CITIES, DIST_MATRIX)
for i in range(EPOCHS):
    new_tsp_sol, new_cost = _nn_approach(CITIES, DIST_MATRIX)
    if new_cost < cost:
        tsp_sol = new_tsp_sol
        cost = new_cost
```

### RESULTS!

<table>
    <tr>
        <th>Region</th>
        <th>Shortest_path (km)</th>
        <th>Graph</th>
    </tr>
    <tr>
        <td>Vanuatu</td>
        <td>1475.528091104531</td>
        <td><img src='imgs/nn_vanuatu.png' style='width:75%'></td>
    </tr>
    <tr>
        <td>Italy</td>
        <td>4436.03176952516</td>
       <td><img src='imgs/nn_italy.png' style='width:75%'></td>
    </tr>
    <tr>
        <td>Russia</td>
        <td>40051.58704748039</td>
        <td><img src='imgs/nn_russia.png' style='width:75%'></td>
    </tr>
    <tr>
        <td>US</td>
        <td>46244.33295267395</td>
        <td><img src='imgs/nn_us.png' style='width:75%'></td>
    </tr>
    <tr>
        <td>China</td>
        <td>62161.09066703267</td>
        <td><img src='imgs/nn_china.png' style='width:75%'></td>
    </tr>
</table>

## 1.4. Solution #2: Greedy approach

## 1.5. Solution #3: EA approach

# ICS 3202: Artificial Intelligence – Practical Exercise 3
## Designing a Self-Driving Trailer on Kenya's Highway Network

### Group Members
| # | Name | Admission No. |
|---|------|---------------|
| 1 | Kelvin Wambua Syengo | 189989 |
| 2 | Jason Wachira | 172995 |
| 3 | Chelsea Muegi | 187629 |

---

## 1. Agent Design Using the PEAS Framework

The self-driving trailer is a goal-based and utility-based agent. Its goal is to deliver cargo from an origin town to a destination town, and among the routes that achieve the goal it prefers the one with the lowest cost (distance) while staying safe and legal.

| PEAS element | Description for the self-driving trailer |
|---|---|
| **Performance measure** | Arrives at the correct destination; shortest distance; no harm to other road users; obeys traffic rules; cargo delivered intact; smooth driving; low wear on the truck |
| **Environment** | Kenyan highways; other vehicles; pedestrians, cyclists and livestock; potholes, speed bumps, roundabouts, escarpments, road works; rain, fog, night-time; police checkpoints, weighbridges, fuel stations |
| **Actuators** | Steering; accelerator and gear transmission; service brakes, engine brake and trailer brakes; indicators, headlights, hazard lights, horn; display |
| **Sensors** | Cameras ; radar; GPS; odometer and speedometer; load / axle-weight, tyre-pressure, engine and fuel sensors; ultrasonic sensors for reversing and docking |

### 1.1 Task Environment

| Property | Classification | Justification |
|---|---|---|
| Fully vs. partially observable | **Partially observable** | Sensors cannot see around bends, over hills, through fog or beyond the next town. A crash or road block ahead is unknown until the agent is close. |
| Deterministic vs. stochastic | **Stochastic** | Other drivers, pedestrians, livestock, weather and tyre bursts mean the next state is not fully determined by the agent's action. |
| Episodic vs. sequential | **Sequential** | Every decision e.g. which road to take,  affects later states and the total trip cost. |
| Static vs. dynamic | **Dynamic** | Traffic moves, lights change and weather shifts while the agent is deliberating. |
| Discrete vs. continuous | **Continuous** | Position, speed, steering angle and time take continuous values. |




## 2. Directed Graph and Search Tree

### 2.1 Towns Selected 

| Region | Towns |
|---|---|
| Nairobi | Nairobi |
| Central Highlands | Thika, Murang'a, Nyeri |
| Rift Valley | Naivasha, Nyahururu, Nakuru, Narok, Bomet, Kericho, Eldoret |
| Lake Victoria Basin | Kisii, Kakamega, Kisumu |


### 2.2 Directed Graph

Each node is a town; each directed edge is a highway segment labelled with its distance. 

![Directed Graph](https://raw.githubusercontent.com/JasonWachira/PS-Agents/main/Directed%20Graph.png)

### 2.3 Search Tree 

The tree is rooted at the initial state (Nairobi) and every branch ends at the goal (Kisumu). The optimal branch is highlighted in green.

![Search tree](https://github.com/JasonWachira/PS-Agents/blob/main/search_tree.png)

---

## 3. Optimal Path from Nairobi to Kisumu

### 3.1 All Possible Routes

| # | Route | Calculation | Total (km) |
|---|---|---|---|
| 1 | Nairobi → Naivasha → Nakuru → Kericho → Kisumu | 87 + 70 + 106 + 84 | **347** |
| 2 | Nairobi → Narok → Bomet → Kericho → Kisumu | 140 + 80 + 77 + 84 | 381 |
| 3 | Nairobi → Narok → Bomet → Kisii → Kisumu | 140 + 80 + 85 + 113 | 418 |
| 4 | Nairobi → Naivasha → Nakuru → Eldoret → Kakamega → Kisumu | 87 + 70 + 152 + 105 + 52 | 466 |
| 5 | Nairobi → Thika → Murang'a → Nyeri → Nyahururu → Nakuru → Kericho → Kisumu | 48 + 49 + 64 + 102 + 63 + 106 + 84 | 516 |
| 6 | Nairobi → Thika → Murang'a → Nyeri → Nyahururu → Nakuru → Eldoret → Kakamega → Kisumu | 48 + 49 + 64 + 102 + 63 + 152 + 105 + 52 | 635 |



### 3.2 Result

**Optimal path: Nairobi → Naivasha → Nakuru → Kericho → Kisumu**

**Total distance: 87 + 70 + 106 + 84 = 347 km**

## 4. Evidence of Group Work

![Team photo](https://github.com/JasonWachira/PS-Agents/blob/main/Group%20Photo.jpeg)



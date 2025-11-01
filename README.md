# Smart City Scheduling - Graph Algorithms Implementation

A **comprehensive Java implementation** of graph algorithms for **task dependency management** and **scheduling optimization** in **smart city applications**.

---

## Overview

This project implements **three core algorithms** for **directed graph analysis**:

| Algorithm | Purpose | Complexity |
|---------|--------|------------|
| **Tarjan's SCC Detection** | Identifies strongly connected components | **O(V+E)** |
| **Topological Sorting** | Orders tasks respecting dependencies (Kahn’s + DFS) | **O(V+E)** |
| **DAG Shortest/Longest Paths** | Computes optimal/critical paths | **O(V+E)** |

---

## To Start

```bash
# Build project
mvn clean compile

# Run tests (12 test classes, 100% pass rate)
mvn test

# Execute main application
mvn exec:java -Dexec.mainClass="com.SmartCity.Main"
```

## Results of Tests
<img src="https://github.com/Asylann/DAA_4/blob/master/testsPhoto.png" alt="Demo Screenshot" width="800"/>

## Project Structure
```
src/main/java/com/SmartCity/
├── algorithms/
│ ├── SCC.java # Tarjan's algorithm
│ ├── CondensationGraph.java # DAG from SCCs
│ ├── KahnTopologicalSort.java # BFS-based topo sort
│ ├── DFSTopologicalSort.java # DFS-based topo sort
│ ├── ComponentTS.java # Component-level sorting
│ └── DAG.java # Shortest/longest paths
├── model/Graph.java # Weighted graph representation
└── utils/
├── GraphLoader.java # JSON graph loading
└── Metrics.java # Performance tracking

src/test/java/ # Comprehensive JUnit tests
input/ # 9 test datasets (JSON format)
```

## Datasets

- **Small (6–8 vertices):** Basic cycle detection and DAG validation  
- **Medium (10–18 vertices):** Dense/sparse structures with multiple SCCs  
- **Large (25–40 vertices):** Complex dependency graphs for performance testing  

All datasets use **edge weights representing task duration (1–7 hours).**

---

##  Algorithm Details

### 1. Strongly Connected Components (Tarjan)
- **Complexity:** `O(V + E)` time, `O(V)` space  
- **Features:** Single-pass DFS, detects cycles, builds condensation graph  
- **Use Case:** Identify circular dependencies in task scheduling  

---

### 2. Topological Sorting
- **Kahn’s Algorithm:** BFS with in-degree tracking, explicit cycle detection  
- **DFS-based:** Post-order traversal, memory efficient  
- **Complexity:** Both `O(V + E)`  
- **Use Case:** Determine valid task execution order  

---

### 3. DAG Paths
- **Shortest Path:** Minimum task completion time  
- **Longest Path:** Critical path analysis (project duration)  
- **Complexity:** `O(V + E)` using topological order  
- **Advantage over Dijkstra:** Handles negative weights, no priority queue overhead  

---

## Performance Results

| Dataset Size | Vertices | SCC Ops | Topo Ops | Total time (ms) |
|--------------:|:--------:|:-------:|:--------:|:----------------:|
| Small         | 7 – 10   | 21 – 31 | 14 – 30  | 0.082 – 0.285    |
| Medium        | 14 – 19  | 44 – 59 | 23 – 59  | 0.106 – 0.161    |
| Large         | 28 – 45  | 86 –141 | 53 –140  | 0.134 – 0.296    |

### Key Findings

- Linear scaling confirmed: ~3 operations per vertex  
- Condensation reduces graph complexity significantly  
- Dense graphs require more operations but maintain `O(V + E)` complexity  
- Critical path length correlates with graph depth  

---

##  Smart City Applications

### Street Maintenance Scheduling
- Detect route dependencies using SCC  
- Order tasks topologically  
- Identify critical maintenance paths  

### Sensor Network Deployment
- Determine activation sequence  
- Minimize deployment time  
- Handle circular sensor dependencies  

###  Infrastructure Project Planning
- Calculate minimum completion time (longest path)  
- Identify bottleneck tasks  
- Optimize resource allocation  

---

## Testing

Comprehensive test coverage includes:

- **SCCTest:** Cycle detection, multiple SCCs, single vertex, complex graphs  
- **CondensationGraphTest:** Component mapping, DAG validation, edge deduplication  
- **TopologicalSortTest:** Both Kahn’s and DFS variants, cycle detection, disconnected graphs  
- **DAGTest:** Shortest/longest paths, path reconstruction, critical path, unreachable vertices  

##  Key Features
- ✓ Edge-weighted graphs for realistic task durations
- ✓ Automatic cycle detection and reporting
- ✓ Component-level and task-level topological ordering
- ✓ Critical path identification for project planning
- ✓ Performance metrics tracking (operations, execution time)
- ✓ JSON-based dataset format for easy customization

## Implementation Highlights
- No external dependencies (except Gson for JSON, JUnit for tests)

- Clean separation of algorithms, models, and utilities

- Comprehensive error handling for edge cases

- Optimized data structures (adjacency lists, single-pass algorithms)

- Detailed documentation with complexity analysis

## Conclusion
The study demonstrates that all three graph algorithms operate efficiently with linear scalability.
Tarjan’s SCC detection is ideal for dependency analysis, while topological sorting ensures safe task execution order.
The DAG shortest/longest path method is recommended for time optimization and critical path planning in smart city scheduling.

### Thank You for attention!
### Author: Usen Asylan
### For the course: Design and Analysis of Algorithms — Assignment 4
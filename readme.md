# P2-COP3530-EG-ET

This was Project 2 in COP3530 Data Structures and Algorithms at the University of Florida. The assignment was to implement and compare graph search algorithms on a large-scale real-world dataset. The project documentation and specifications are detailed below.

## TrailQuest: Graph Traversal & Pathfinding Comparison

### Overview
Finding optimal paths across large geographical networks requires efficient graph representations and heuristic-driven algorithms. Standard pathfinding approaches vary substantially in time complexity, node expansion efficiency, and memory consumption depending on graph topology and weight distribution.

In this project, we implement **TrailQuest**, an interactive C++ pathfinding application evaluating **Dijkstra's Algorithm** against the **A\* Search Algorithm**. The underlying graph model utilizes real-world geospatial terrain and pathway data sourced from OpenStreetMap surrounding the University of Florida campus and the broader Gainesville area.

### Core Responsibilities
- Construct an adjacency list representation of a weighted, undirected spatial graph parsed from processed OpenStreetMap node and edge records.
- Implement Dijkstra's Algorithm using a min-priority queue to determine uniform-cost shortest paths.
- Implement A* Search Algorithm incorporating admissible spatial distance heuristics to minimize redundant node expansions.
- Profile and benchmark empirical runtime performance, total visited node counts, and memory footprints between both algorithms on identical origin-destination queries.
- Package application binaries alongside required shared libraries (DLLs) and map grid configuration files.

### Algorithm Specifications & Comparison

| Metric / Dimension | Dijkstra's Algorithm | A* Search Algorithm |
| :--- | :--- | :--- |
| **Search Strategy** | Uninformed / Uniform-Cost Search | Informed / Heuristic-Guided Best-First Search |
| **Evaluation Function** | f(n) = g(n) (accumulated edge cost from source) | f(n) = g(n) + h(n) (cost-so-far + admissible heuristic) |
| **Priority Metric** | Minimum path distance from source | Minimum estimated total cost via node n |
| **Node Expansion** | Concentric outward expansion across all directions | Directed exploration towards the target destination |
| **Optimality Guarantee** | Guarantees shortest path for non-negative edge weights | Guarantees shortest path if heuristic h(n) is admissible and consistent |
| **Empirical Performance** | Visits a higher percentage of graph nodes | Dramatically reduces expanded nodes across Gainesville spatial networks |

### Project Architecture & Dependencies
- **Data Source**: OpenStreetMap spatial network data for Gainesville and the University of Florida campus.
- **Dataset Configuration**: `grid.txt` specifies coordinate definitions, node identifiers, and edge traversal costs.
- **Runtime Dependencies**: Required Windows dynamic link libraries (`.dll`) must reside in the root execution directory alongside the compiled executable.
- **Language / Toolchain**: C++ (C++14 / C++17), CMake, MinGW-w64.
- **Repository**: https://github.com/EzraGerstein/P2-COP3530-EG-ET

### Getting Started

#### Prerequisites
- MinGW-w64 (GCC / G++)
- CMake (3.15+)
- Git

#### Setup & Execution (Pre-compiled Binary)
Ensure `grid.txt` and all packaged `.dll` files are present in the same directory as `main.exe`:

```bash
git clone https://github.com/EzraGerstein/P2-COP3530-EG-ET.git
cd P2-COP3530-EG-ET
main.exe
```

#### Building from Source
To compile the project manually using CMake and MinGW:

```bash
git clone https://github.com/EzraGerstein/P2-COP3530-EG-ET.git
cd P2-COP3530-EG-ET
cmake -B build -G "MinGW Makefiles"
cmake --build build
```

After building, ensure the generated executable runs from the directory containing `grid.txt` and all required DLL files.

### Repository Structure
```text
P2-COP3530-EG-ET/
├── CMakeLists.txt      # CMake build configuration script
├── grid.txt            # Parsed Gainesville/UF OpenStreetMap node and edge grid
├── *.dll               # Dynamic link libraries required for execution
├── src/                # C++ source files (Graph, Dijkstra, A*, UI logic)
├── include/            # Header definitions and function declarations
└── README.md           # Project documentation
```

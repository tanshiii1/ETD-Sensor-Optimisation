# ETD-Sensor-Optimisation
Geometric Optimisation for Risk-Aware Sensor Placement (PSO-ETD)

Project Overview
This project implements a Particle Swarm Optimisation (PSO) solution to solve the Optimal Sensor Placement (OSP) problem within a dynamic security context. Instead of aiming for maximum generic coverage, this solution is tailored to maximise the risk-weighted coverage score for a fixed budget of 10 Explosives Trace Detection (ETD) sensors across a high-risk urban area.

The core innovation lies in the Risk-Weighted Fitness Function, translating into a mathematically solvable geometric challenge.

Key Features and Technical Highlights
- Uses the Particle Swarm Optimisation (PSO) algorithm to navigate the non-linear, NP-hard problem space.
- Achieved rapid convergence to a high Total Weighted Coverage Score (WCS), proving efficiency over baseline methods.
- Integrates geospatial intelligence with the optimisation objective.
- Criticality Index Grid ($W_j$): Map derived from OpenStreetMap (OSM) data, assigning Tier 1 weights (e.g., 10) and larger buffer zones to critical infrastructure (HVTs).
-  The custom objective function uses  NumPy linear algebra to calculate coverage and weight summation simultaneously, avoiding slow geometric library operations.
- Converts the abstract grid solution back into physical geographic coordinates (Lat/Lon).
- Generates an interactive Folium map to visually demonstrate optimal sensor placement, coverage radius (in meters), and HVT locations on a real satellite background.

Technical Stack

- Core Logic: Python 3.9+
- Optimisation/Math: NumPy (Vectorised Distance Calculation, Fitness Function)
- Geospatial Data: OSMnx (HVT and Road Network Extraction)
- Visualisation: Matplotlib (Static Plots), Folium (Interactive Web Map Generation)
- Intelligence: Gemini API (AI-powered security analysis of the final placement).

Prerequisites:

You need Python 3.9+ and the following libraries installed:
"pip install osmnx geopandas shapely folium numpy pandas nest_asyncio"

Execution Pipeline:

The project runs in three distinct phases (best executed in sequential cells of a Jupyter/Colab notebook):
1. Data Extraction:
Queries OSM for HVT data and downloads the road network.
Output: Clean HVT coordinates.

2. Optimisation:
Generates the 100x100 Criticality Map (W_j).
Runs the 500-generation PSO to find the optimal_placement.
Output: Optimised sensor coordinates.

3. Visualisation:
Reverse-normalises the solution to Lat/Lon.
Calls the Gemini API for security analysis.
Generates the static convergence plot and the optimal_placement_map.html interactive file.

Expected Results
File: optimal_placement_map.html
Visualisation: Sensor points clustered around high-weight areas, demonstrating the successful maximisation of the Risk-Weighted Coverage Score.

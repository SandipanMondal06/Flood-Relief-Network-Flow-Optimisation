# prompt: create one readme file for this project i will copy and paste it diretly

# README for Disaster Relief Optimization Project

This project uses a two-step optimization approach to model and solve a disaster relief resource allocation problem. The goal is to efficiently distribute essential resources (food, water, medicine, cloth) from supply nodes to demand nodes, prioritizing urgent needs and minimizing transportation costs.

## Project Structure

The project is structured as follows:

1. **Data Generation:** The script first generates synthetic datasets for supply, demand, and distances using the `pandas` and `random` libraries.  These datasets are saved as CSV files:
    - `supply_data.csv`: Contains supply capacity for each resource at each supply node.
    - `demand_data.csv`: Contains demand for each resource at each demand node, along with an urgency flag.
    - `distance_data.csv`: Contains distances and transportation costs between supply and demand nodes for each resource.

2. **Data Validation:**  It then checks if the total supply capacity for each item exceeds the total demand to ensure feasibility.

3. **Optimization Model:** The core of the project uses the `Pyomo` optimization library to model and solve the resource allocation problem. The problem is broken into two steps:

   - **Step 1: Urgent Demand Fulfillment:** This step prioritizes satisfying the demands of urgent nodes by minimizing the total transportation distance.

   - **Step 2: Non-Urgent Demand Fulfillment:**  This step addresses remaining demand from non-urgent nodes, minimizing transportation costs.
    - The solution from step 1 (the amounts of resource transported) is used to update the remaining supply capacity.

4. **Result Generation:** The script outputs the detailed transportation plan, including quantity, distance, and cost for each shipment, to a CSV file named `transportation_output.csv`.

## Required Libraries and Installation

The project requires the following libraries:

- `pandas`
- `random`
- `pyomo`
- `glpk` (or a compatible solver like CBC or IPOPT)

You can install these libraries using pip

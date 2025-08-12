# EcoRoute Market — Carbon-Aware Vehicle Routing with Token Trading

**Short:** EcoRoute Market integrates vehicle routing optimization with an internal carbon token market. It solves per-company VRPs, computes CO₂ emissions, and runs a uniform-price auction so companies can buy/sell emission tokens.

**Project name:** EcoRoute Market  
**Repository slug:** `eco-vrp-carbon-market`

---

## Key features
- Parse Solomon / RC2 benchmark instances (e.g. `RC2_10_10.txt`).
- Partition large customer sets into multiple logistics companies using spatial clustering (KMeans).
- Solve each company's Capacitated VRP (CVRP) using Google OR-Tools routing solver (fast for 50–200 customers).
- Compute per-route CO₂ emissions and company emissions.
- Assign company budgets **inversely** proportional to emissions (so low-emitters get more buying power).
- Run a uniform-price double auction to clear token trades; produce clearing price, trades, payments.
- Optionally re-optimize routing with token price (makes emissions cost part of routing decision).

---

## Why this approach
Large real-world instances (≥1000 customers) are split into companies to keep optimization tractable. OR-Tools routing provides reliable, fast approximate/near-optimal VRP solutions; the auction simulates an internal carbon market to trade tokens and internalize emission externalities.

---

## Requirements
- Python 3.8+
- Packages:
  - `numpy`, `pandas`, `scikit-learn`, `ortools`, `matplotlib`
  - Optional: `pulp` if you want MILP alternatives (not required for main pipeline)

Install quickly:
```bash
pip install numpy pandas scikit-learn ortools matplotlib

# 📦 Joint Order Batching and Picker Routing Problem (JOBPRP)

> Optimizing warehouse order picking using Integer Programming and
> Machine Learning

------------------------------------------------------------------------

## 🏭 Why This Problem Matters

Order picking accounts for **50--70% of warehouse operational costs** in
large fulfillment centers.

In e-commerce and grocery warehouses: - Excessive picker travel - Poor
carton utilization - Congestion in aisles - Delayed fulfillment

This article explores how **Joint Order Batching and Picker Routing
(JOBPRP)** can significantly improve warehouse efficiency.

------------------------------------------------------------------------

# 🧩 Problem Overview

JOBPRP consists of **two tightly coupled decisions**:

### 1️⃣ Order Batching

Group multiple orders into a single picking batch.

### 2️⃣ Picker Routing

Determine the most efficient path to collect all items.

------------------------------------------------------------------------

## 🚧 Why It's Complex

-   Varied item dimensions and weights\
-   Layout constraints and congestion\
-   Picker capacity limitations\
-   Objective: Minimize total travel distance

The number of feasible batching combinations grows **exponentially**
with the number of orders.

------------------------------------------------------------------------

# 📐 Integer Programming Formulation

### Core Constraints

1.  **Order Assignment** -- Each order assigned to exactly one picker\
2.  **Picker Capacity** -- Weight/volume must not exceed limit\
3.  **Flow Conservation** -- Route continuity must be maintained\
4.  **Depot Constraint** -- Start and end at depot\
5.  **Distance Minimization** -- Minimize total travel\
6.  **Unified Order Picking** -- Single picker per order

------------------------------------------------------------------------

# 🏗 Compact Warehouse Example

## Orders

  Order   Items            Weight
  ------- ---------------- --------
  O1      Laptop, Mouse    3 kg
  O2      Printer, Paper   7 kg
  O3      Phone, Charger   2 kg

------------------------------------------------------------------------

## Optimized Allocation

**Picker 1**\
Orders: O1 + O3 (5 kg)\
Route: O → A → C → D → O\
Distance: 45 meters

**Picker 2**\
Orders: O2 (7 kg)\
Route: O → B → D → O\
Distance: 45 meters

**Total Optimized Distance: 90 meters**\
Without optimization: 125+ meters

------------------------------------------------------------------------

# 🤖 Machine Learning for Predictive Batching

Using historical order data:

-   Laptop → Mouse (90% confidence)\
-   Printer → Ink + Paper (95%)\
-   Phone → Screen Protector (85%)

Algorithms used: - Apriori\
- FP-Growth\
- Bayesian Models\
- Clustering

------------------------------------------------------------------------

# 📊 Benefits

-   Reduced travel time\
-   Lower labor cost\
-   Reduced fatigue\
-   Improved order accuracy\
-   Increased throughput

------------------------------------------------------------------------

# 🔚 Final Thoughts

Combining **Integer Programming for routing** and **Machine Learning for
predictive batching** enables 25--35% travel distance reduction and
major efficiency gains in warehouse operations.

Optimization tools such as **Gurobi, PuLP, and OR-Tools** can be used
for large-scale implementation.

------------------------------------------------------------------------

# 📚 Reference

Valle, C. A., Beasley, J. E., & da Cunha, A. S. (2017).\
*Optimally solving the joint order batching and picker routing
problem.*\
European Journal of Operational Research, 262(3), 817--834.
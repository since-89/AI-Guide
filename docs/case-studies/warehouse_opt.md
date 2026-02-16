# Warehouse Optimization: Joint Order Batching and Picker Routing (JOBPRP)

Order picking represents one of the largest operational costs in warehouse systems, often accounting for 50–70% of total warehouse labor expense.

The **Joint Order Batching and Picker Routing Problem (JOBPRP)** integrates two critical decisions:

1. Order batching  
2. Picker routing  

Solving them jointly significantly reduces travel distance, labor time, and congestion.

---

# 1️⃣ Problem Definition

Let:

- \( O \) = set of customer orders  
- \( P \) = set of pickers  
- \( N \) = set of warehouse locations (including depot)  
- \( d_{ij} \) = travel distance between location \( i \) and \( j \)  
- \( w_o \) = weight (or volume) of order \( o \)  
- \( Q_p \) = capacity of picker \( p \)

Depot is denoted as node \( 0 \).

---

# 2️⃣ Decision Variables

### Order Assignment

\[
x_{op} =
\begin{cases}
1 & \text{if order } o \text{ assigned to picker } p \\
0 & \text{otherwise}
\end{cases}
\]

---

### Routing Variable

\[
y_{ijp} =
\begin{cases}
1 & \text{if picker } p \text{ travels from } i \text{ to } j \\
0 & \text{otherwise}
\end{cases}
\]

---

# 3️⃣ Objective Function

Minimize total travel distance:

\[
\min \sum_{p \in P} \sum_{i \in N} \sum_{j \in N} d_{ij} y_{ijp}
\]

This directly reduces labor cost and picker fatigue.

---

# 4️⃣ Constraints

---

## 4.1 Order Assignment Constraint

Each order must be assigned to exactly one picker:

\[
\sum_{p \in P} x_{op} = 1
\quad \forall o \in O
\]

---

## 4.2 Picker Capacity Constraint

\[
\sum_{o \in O} w_o x_{op} \le Q_p
\quad \forall p \in P
\]

Prevents overload.

---

## 4.3 Flow Conservation (Route Continuity)

For each picker \( p \) and location \( i \):

\[
\sum_{j \in N} y_{ijp}
=
\sum_{j \in N} y_{jip}
\quad \forall i \neq 0
\]

Ensures if picker enters a node, they must leave it.

---

## 4.4 Depot Start and End Constraint

Each picker must start and end at depot:

\[
\sum_{j \in N} y_{0jp} = 1
\]

\[
\sum_{i \in N} y_{i0p} = 1
\]

---

## 4.5 Subtour Elimination (MTZ Formulation)

To prevent disconnected cycles:

Introduce auxiliary variable \( u_{ip} \):

\[
u_{ip} - u_{jp} + |N| y_{ijp} \le |N| - 1
\]

Ensures single connected route.

---

## 4.6 Linking Assignment and Routing

If order \( o \) is assigned to picker \( p \), its locations must be visited:

\[
\sum_{j \in N} y_{ijp} \ge x_{op}
\]

---

# 5️⃣ Compact MILP Formulation

\[
\min \sum_{p,i,j} d_{ij} y_{ijp}
\]

Subject to:

- Assignment constraints  
- Capacity limits  
- Flow conservation  
- Depot constraints  
- Subtour elimination  

\[
x_{op} \in \{0,1\}
\]

\[
y_{ijp} \in \{0,1\}
\]

---

# 6️⃣ Example: Compact Warehouse Case

Given:

- 3 orders  
- 2 pickers  
- Capacity = 10 kg  

Distance matrix:

\[
d =
\begin{bmatrix}
0 & 10 & 15 & 20 & 25 \\
10 & 0 & 5 & 5 & 10 \\
15 & 5 & 0 & 10 & 5 \\
20 & 5 & 10 & 0 & 5 \\
25 & 10 & 5 & 5 & 0
\end{bmatrix}
\]

Optimized solution:

Picker 1:
\[
O1 + O3 \rightarrow 45 \text{ meters}
\]

Picker 2:
\[
O2 \rightarrow 45 \text{ meters}
\]

Total:

\[
90 \text{ meters}
\]

Without optimization:

\[
>125 \text{ meters}
\]

~28% reduction in travel distance.

---

# 7️⃣ Why JOBPRP Is Hard

The problem combines:

- Bin packing (batching)
- Vehicle routing (routing)
- Assignment optimization
- Capacity constraints

Number of feasible batches grows exponentially:

\[
O(2^{|O|})
\]

Making it NP-Hard.

---

# 8️⃣ Machine Learning Extension for Dynamic Batching

Let:

\[
P(A \mid B)
\]

be probability that item \( A \) appears given item \( B \).

Association rule:

\[
P(\text{Mouse} \mid \text{Laptop}) = 0.9
\]

Use predictive clustering to pre-group likely co-occurring SKUs.

Objective becomes:

\[
\min E[\text{Travel Distance}]
\]

Under stochastic order arrivals.

---

# 9️⃣ Stochastic Extension

If orders arrive randomly:

\[
O_t \sim \text{Demand Distribution}
\]

We solve:

\[
\min E\left[
\sum_{p,i,j} d_{ij} y_{ijp}
\right]
\]

Using:

- Scenario-based optimization  
- Rolling horizon planning  
- Real-time re-optimization  

---

# 🔟 Business Impact

Optimization delivers:

- 20–35% reduction in picker travel  
- Lower congestion  
- Reduced labor fatigue  
- Faster order fulfillment  
- Improved throughput  

Companies like Amazon and Walmart implement such routing logic at scale.

---

# 🧠 Why Integer Programming Works

JOBPRP is fundamentally a:

- Binary assignment problem  
- Capacitated vehicle routing problem  
- Network flow problem  

MILP solvers efficiently handle:

- Thousands of orders  
- Multi-picker systems  
- Capacity trade-offs  

---

# 🏁 Conclusion

Warehouse order picking is not merely an operational task — it is a network optimization problem.

By integrating:

- Order batching  
- Picker routing  
- Capacity planning  
- Predictive SKU clustering  

into a unified MILP framework, warehouses can significantly reduce operational cost while improving service level.

Optimization transforms warehouse operations from reactive execution to mathematical precision.
------------------------------------------------------------------------

# 📚 Reference

Valle, C. A., Beasley, J. E., & da Cunha, A. S. (2017).\
*Optimally solving the joint order batching and picker routing
problem.*\
European Journal of Operational Research, 262(3), 817--834.

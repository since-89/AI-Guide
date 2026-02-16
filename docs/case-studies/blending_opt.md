
# Blending Optimization: Linear Programming for Product Mix Maximization

Blending optimization determines the optimal mixture of raw components to produce finished products that:

- Meet quality specifications  
- Satisfy demand  
- Maximize profit  
- Respect operational constraints  

Common in:

- Oil refining  
- Chemicals  
- Food production  
- Mining  
- Energy  

---

# 1️⃣ Problem Definition

Let:

- \( i \in I \) = set of raw components  
- \( j \in J \) = set of final products  
- \( t \in T \) = time periods  

Parameters:

- \( c_i \) = cost per unit of component \( i \)  
- \( p_j \) = selling price of product \( j \)  
- \( a_{ij} \) = proportion of component \( i \) in product \( j \)  
- \( D_j \) = demand for product \( j \)  
- \( U_i \) = available supply of component \( i \)

---

# 2️⃣ Decision Variables

\[
x_{ij} = \text{Quantity of component } i \text{ used in product } j
\]

\[
y_j = \text{Total quantity of product } j \text{ produced}
\]

---

# 3️⃣ Objective Function

Maximize net profit:

\[
\max \sum_{j \in J} p_j y_j - \sum_{i \in I} c_i \sum_{j \in J} x_{ij}
\]

---

# 4️⃣ Material Balance Constraint

\[
\sum_{j \in J} x_{ij} \le U_i
\quad \forall i \in I
\]

Cannot exceed component supply.

---

# 5️⃣ Product Composition Constraint

\[
\sum_{i \in I} x_{ij} = y_j
\quad \forall j \in J
\]

Ensures components sum to product volume.

---

# 6️⃣ Quality Constraint

If component property \( q_i \) affects product quality:

\[
L_j \le
\frac{\sum_{i} q_i x_{ij}}{y_j}
\le U_j
\]

Linearized as:

\[
L_j y_j \le \sum_{i} q_i x_{ij} \le U_j y_j
\]

Maintains specification bounds.

---

# 7️⃣ Demand Constraint

\[
y_j \le D_j
\quad \forall j
\]

---

# 8️⃣ Storage Capacity Constraint (Optional)

\[
\sum_{j} y_j \le C
\]

Where \( C \) = total storage capacity.

---

# 9️⃣ Multi-Period Extension

Inventory balance:

\[
I_{it} = I_{i,t-1} + S_{it} - \sum_{j} x_{ijt}
\]

Where:

- \( S_{it} \) = supply arrival  
- \( I_{it} \) = inventory level  

---

# 🔟 Full Linear Programming Model

\[
\max \sum_{j} p_j y_j - \sum_{i,j} c_i x_{ij}
\]

Subject to:

- Supply limits  
- Composition balance  
- Quality constraints  
- Demand limits  

\[
x_{ij} \ge 0, \quad y_j \ge 0
\]

---

# 🚀 Business Impact

Blending optimization enables:

- Higher margin through optimal mix  
- Reduced raw material waste  
- Consistent product quality  
- Improved tank utilization  
- Demand-aligned production  

---

# 🧠 Why Linear Programming Works

Blending problems are naturally linear because:

- Costs scale proportionally  
- Properties are additive  
- Flow constraints are linear  

Thus LP solvers (Gurobi, CPLEX, OR-Tools) efficiently solve large-scale industrial blending problems.

---

# 🏁 Conclusion

Blending optimization converts complex production decisions into a structured linear programming framework.

It allows firms to systematically:

- Maximize profitability  
- Maintain quality  
- Respect operational limits  

Optimization transforms product mixing from art into mathematical precision.

# Inventory Optimization: Mathematical Modeling for Retail & Supply Chain Efficiency

Inventory optimization ensures that the right product is available:

- In the right quantity  
- At the right location  
- At the right time  
- At minimum total cost  

Poor inventory planning leads to:

- Excess holding cost  
- Stockouts and lost sales  
- Working capital blockage  
- Supply chain inefficiencies  

This article formulates inventory optimization as a mathematical decision problem.

---

# 1️⃣ Problem Definition

Let:

- \( i \in I \) = set of SKUs  
- \( t \in T \) = time periods  
- \( D_{it} \) = demand for SKU \( i \) in period \( t \)  
- \( c_i^h \) = holding cost per unit  
- \( c_i^o \) = ordering cost  
- \( c_i^s \) = stockout penalty cost  
- \( L_i \) = lead time  

---

# 2️⃣ Decision Variables

\[
Q_{it} = \text{Order quantity of SKU } i \text{ in period } t
\]

\[
I_{it} = \text{Inventory level at end of period } t
\]

\[
S_{it} = \text{Shortage quantity in period } t
\]

---

# 3️⃣ Objective Function

Minimize total inventory cost:

\[
\min \sum_{i \in I} \sum_{t \in T}
\left(
c_i^h I_{it}
+ c_i^o \delta_{it}
+ c_i^s S_{it}
\right)
\]

Where:

\[
\delta_{it} =
\begin{cases}
1 & \text{if } Q_{it} > 0 \\
0 & \text{otherwise}
\end{cases}
\]

This captures:

- Holding cost  
- Ordering cost  
- Shortage penalty  

---

# 4️⃣ Core Constraints

---

## 4.1 Inventory Balance Equation

\[
I_{it} = I_{i,t-1} + Q_{i,t-L_i} - D_{it} + S_{it}
\]

Ensures proper inventory tracking over time.

---

## 4.2 Non-negativity Constraints

\[
I_{it} \ge 0
\]

\[
Q_{it} \ge 0
\]

\[
S_{it} \ge 0
\]

---

## 4.3 Service Level Constraint

To maintain service level \( \alpha \):

\[
P(\text{Stockout}) \le 1 - \alpha
\]

Often approximated via safety stock:

\[
SS_i = z_\alpha \sigma_i \sqrt{L_i}
\]

Where:

- \( z_\alpha \) = service factor  
- \( \sigma_i \) = demand standard deviation  

---

# 5️⃣ Classic (Q, R) Policy Formulation

In continuous review systems:

Reorder point:

\[
R_i = \mu_i L_i + SS_i
\]

Order quantity (EOQ):

\[
Q_i^* = \sqrt{\frac{2 D_i c_i^o}{c_i^h}}
\]

Where:

- \( D_i \) = annual demand  

---

# 6️⃣ Multi-Echelon Inventory Model

For supply chain with:

- Supplier  
- Distribution center  
- Retail store  

Inventory dynamics become:

\[
I_{it}^{(k)} = I_{i,t-1}^{(k)} + Q_{i,t-L_i}^{(k)} - D_{it}^{(k)}
\]

for echelon \( k \).

Optimization minimizes total system-wide cost.

---

# 7️⃣ Stochastic Demand Formulation

When demand is uncertain:

\[
D_{it} \sim \mathcal{N}(\mu_i, \sigma_i^2)
\]

Expected shortage:

\[
E[S_i] = \sigma_i L(z_\alpha)
\]

Where \( L(z) \) is the loss function.

---

# 8️⃣ Capacity Constraint (Optional)

If warehouse capacity is limited:

\[
\sum_{i \in I} v_i I_{it} \le C
\]

Where:

- \( v_i \) = volume of SKU  
- \( C \) = warehouse capacity  

---

# 9️⃣ MILP Compact Form

\[
\min \sum_{i,t} \left(
c_i^h I_{it}
+ c_i^o \delta_{it}
+ c_i^s S_{it}
\right)
\]

Subject to:

- Inventory balance  
- Non-negativity  
- Service constraints  
- Capacity limits  

---

# 🔟 Business Interpretation

Optimization balances:

- Holding cost vs ordering cost  
- Service level vs capital tie-up  
- Centralization vs decentralization  
- Deterministic vs stochastic demand  

---

# 🚀 Impact of Optimization

Proper implementation enables:

- 10–30% reduction in working capital  
- Lower stockouts  
- Higher fill rate  
- Reduced obsolescence  
- Improved turnover ratio  

---

# 🧠 Why Mathematical Optimization Matters

Manual inventory planning:

- Overestimates safety stock  
- Ignores variability interaction  
- Fails under multi-echelon systems  

Optimization provides:

- System-wide cost minimization  
- Structured trade-off analysis  
- Scalability to thousands of SKUs  

---

# 🏁 Conclusion

Inventory optimization is fundamentally a dynamic, multi-period cost minimization problem under uncertainty.

By formulating it mathematically and solving with:

- Linear Programming  
- Stochastic Optimization  
- Simulation-based methods  

firms can significantly improve capital efficiency while maintaining high service levels.

Optimization transforms inventory from a cost center into a strategic advantage.

# Packaging Optimization: Mathematical Modeling for Cartonization and Shipping Cost Reduction

Packaging and shipping are critical warehouse operations where items must be packed efficiently to:

- Reduce shipping cost  
- Minimize volumetric weight  
- Reduce void space  
- Protect product integrity  

Shipping vendors typically charge based on:

\[
\text{Chargeable Weight} = \max(\text{Actual Weight}, \text{Volumetric Weight})
\]

Where:

\[
\text{Volumetric Weight} = \frac{L \times B \times H}{f}
\]

- \( L, B, H \) = carton dimensions  
- \( f \) = dimensional divisor (vendor-defined factor)

Since \( f \) is fixed via negotiation, optimization must focus on minimizing:

\[
L \times B \times H
\]

---

# 1️⃣ Problem Definition

Let:

- \( i \in I \) = items in an order  
- \( j \in J \) = available carton types  
- \( v_i \) = volume of item \( i \)  
- \( w_i \) = weight of item \( i \)  
- \( V_j \) = volume of carton \( j \)  
- \( W_j \) = weight capacity of carton \( j \)  
- \( c_j \) = shipping cost of carton \( j \)

---

# 2️⃣ Decision Variables

\[
x_{ij} =
\begin{cases}
1 & \text{if item } i \text{ is assigned to carton } j \\
0 & \text{otherwise}
\end{cases}
\]

\[
y_j =
\begin{cases}
1 & \text{if carton } j \text{ is used} \\
0 & \text{otherwise}
\end{cases}
\]

---

# 3️⃣ Objective Function

Minimize total shipping cost:

\[
\min \sum_{j \in J} c_j y_j
\]

Alternatively, minimize total volumetric space:

\[
\min \sum_{j \in J} V_j y_j
\]

---

# 4️⃣ Core Constraints

---

## 4.1 Item Assignment Constraint

Each item must be assigned to exactly one carton:

\[
\sum_{j \in J} x_{ij} = 1
\quad \forall i \in I
\]

---

## 4.2 Volume Capacity Constraint

\[
\sum_{i \in I} v_i x_{ij} \le V_j y_j
\quad \forall j \in J
\]

---

## 4.3 Weight Capacity Constraint

\[
\sum_{i \in I} w_i x_{ij} \le W_j y_j
\quad \forall j \in J
\]

---

## 4.4 Carton Activation Constraint

\[
x_{ij} \le y_j
\quad \forall i,j
\]

Ensures a carton is marked used if items are assigned.

---

# 5️⃣ Cartonization as a Bin Packing Problem

Packaging optimization is a variant of the **3D Bin Packing Problem**, which is NP-Hard.

Objective:

- Minimize number of cartons  
- Minimize void space  
- Respect orientation constraints  

---

# 6️⃣ Orientation Constraints

Some items must respect orientation rules:

Example: Refrigerator cannot be flipped.

Let:

\[
o_i \in O_i
\]

Set of allowed orientations.

Feasible placement requires:

\[
\text{Dimensions after rotation} \le \text{Carton dimensions}
\]

---

# 7️⃣ Example: Void Space Reduction

Consider:

Television: \( 50 \times 35 \times 4 \)  
Football: \( 8 \times 8 \times 8 \)

Combined carton volume:

\[
50 \times 35 \times 12 = 21{,}000
\]

Separate shipment volume:

\[
(50 \times 35 \times 4) + (8 \times 8 \times 8)
= 7{,}000 + 512 = 7{,}512
\]

Void percentage:

\[
\frac{21{,}000 - 7{,}512}{21{,}000} \approx 64\%
\]

Optimization prevents such inefficiency.

---

# 8️⃣ Carton Size Selection Optimization

Warehouses typically use limited carton sizes (e.g., 10 types).

Goal:

Select optimal carton dimensions set \( J^* \subseteq J \)

\[
\min \text{Total Expected Shipping Cost}
\]

Subject to historical order distribution.

This becomes a **facility location style problem**.

---

# 9️⃣ Stochastic Demand Extension

If orders arrive randomly:

\[
D \sim \text{Demand Distribution}
\]

We optimize expected cost:

\[
\min E[\text{Shipping Cost}]
\]

Using:

- Simulation  
- Scenario-based optimization  
- Historical data modeling  

---

# 🔟 Full MILP Form

\[
\min \sum_{j} c_j y_j
\]

Subject to:

- Assignment constraint  
- Volume constraint  
- Weight constraint  
- Activation constraint  

\[
x_{ij} \in \{0,1\}
\]

\[
y_j \in \{0,1\}
\]

---

# 🚀 Business Impact

Effective packaging optimization delivers:

- 10–25% shipping cost reduction  
- Lower volumetric weight charges  
- Reduced void space  
- Fewer damaged goods  
- Improved carton utilization  

---

# 🧠 Why Optimization Matters

Manual packing decisions:

- Overuse large cartons  
- Ignore volume interaction  
- Increase dimensional weight cost  

Optimization enables:

- Data-driven carton size selection  
- Systematic void minimization  
- Scalable packing rules  

---

# 🏁 Conclusion

Packaging optimization is a combinatorial decision problem balancing:

- Volume  
- Weight  
- Orientation  
- Shipping cost  
- SKU compatibility  

By formulating it as a MILP or Bin Packing model, warehouses can significantly reduce logistics cost while improving operational efficiency.

Optimization turns packaging from a reactive activity into a structured cost-engineering discipline.

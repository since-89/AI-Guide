# Crew Scheduling Optimization for Reliable Airline Operations

Efficient crew scheduling is a large-scale combinatorial optimization problem that can be formulated as a Mixed Integer Linear Program (MILP).

This section presents the full mathematical formulation.

---

# 1️⃣ Problem Definition

Let:

- \( C \) = set of crew members  
- \( F \) = set of flights  
- \( R \) = set of crew roles (Captain, FO, FA)  
- \( B \) = set of crew bases  

Each flight \( f \in F \) has:
- Start time \( s_f \)
- End time \( e_f \)
- Required crew by role \( d_{fr} \)

Each crew member \( c \in C \) has:
- Role \( r(c) \)
- Base \( b(c) \)
- Qualification set \( Q_c \)
- Maximum duty hours \( H_c \)
- Monthly credit limit \( M_c \)

---

# 2️⃣ Decision Variable

\[
x_{cf} =
\begin{cases}
1 & \text{if crew } c \text{ is assigned to flight } f \\
0 & \text{otherwise}
\end{cases}
\]

Binary variable:
\[
x_{cf} \in \{0,1\}
\]

---

# 3️⃣ Objective Function

Typical objective: minimize total crew assignment cost.

\[
\min \sum_{c \in C} \sum_{f \in F} c_{cf} x_{cf}
\]

Where:

- \( c_{cf} \) = cost of assigning crew \( c \) to flight \( f \)

Alternative objective: maximize utilization:

\[
\max \sum_{c \in C} \sum_{f \in F} u_f x_{cf}
\]

---

# 4️⃣ Constraints

---

## 4.1 Flight Coverage Constraint

Each flight must have required crew for each role:

\[
\sum_{c \in C_r} x_{cf} = d_{fr}
\quad \forall f \in F, \forall r \in R
\]

Where:
- \( C_r \subseteq C \) = crew members with role \( r \)

---

## 4.2 No Overlapping Flights

If two flights \( f_1, f_2 \) overlap:

\[
s_{f_1} < e_{f_2} \quad \text{and} \quad s_{f_2} < e_{f_1}
\]

Then:

\[
x_{cf_1} + x_{cf_2} \le 1
\quad \forall c \in C
\]

Prevents simultaneous assignments.

---

## 4.3 Duty Time Constraint

Let:

- \( T_{cf} \) = duration of flight \( f \)
- \( G_{f_1f_2} \) = ground time between connected flights

Total duty time for crew \( c \):

\[
\sum_{f \in F} T_{cf} x_{cf} \le H_c
\quad \forall c \in C
\]

---

## 4.4 Minimum Rest Constraint

For consecutive duties:

If flight \( f_1 \) precedes \( f_2 \), then:

\[
s_{f_2} - e_{f_1} \ge R_{\min}
\]

Otherwise:

\[
x_{cf_1} + x_{cf_2} \le 1
\]

Ensures minimum rest window.

---

## 4.5 Base Constraint

Crew must start and end at base.

Let:

- \( O_f \) = origin airport
- \( D_f \) = destination airport

Feasible pairing must satisfy:

\[
O_{f_1} = b(c)
\]

\[
D_{f_k} = b(c)
\]

Enforced via pairing generation or network flow constraints.

---

## 4.6 Qualification Constraint

Crew can only operate flights for which they are certified:

\[
x_{cf} \le q_{cf}
\quad \forall c,f
\]

Where:

\[
q_{cf} =
\begin{cases}
1 & \text{if crew } c \text{ is qualified for flight } f \\
0 & \text{otherwise}
\end{cases}
\]

---

## 4.7 Monthly Credit Limit

\[
\sum_{f \in F} T_{cf} x_{cf} \le M_c
\quad \forall c \in C
\]

Prevents excessive credit accumulation.

---

## 4.8 Connectivity Constraint

If flight \( f_2 \) follows \( f_1 \):

\[
D_{f_1} = O_{f_2}
\]

\[
s_{f_2} - e_{f_1} \ge \text{Minimum Turnaround}
\]

Otherwise:

\[
x_{cf_1} + x_{cf_2} \le 1
\]

---

# 5️⃣ Compact MILP Form

\[
\min \sum_{c,f} c_{cf} x_{cf}
\]

Subject to:

- Flight coverage
- Overlap constraints
- Duty limits
- Rest limits
- Qualification limits
- Credit limits
- Base feasibility

\[
x_{cf} \in \{0,1\}
\]

---

# 6️⃣ Model Strength

This MILP:

- Guarantees legal schedules  
- Enforces global consistency  
- Handles thousands of flights  
- Evaluates millions of feasible combinations  

Solvers used:

- Gurobi  
- CPLEX  
- OR-Tools  
- CBC  

---

# 7️⃣ Strategic Impact

Embedding regulatory and fatigue rules directly into the mathematical model ensures:

- Lower cancellation risk  
- Improved cost efficiency  
- Transparent decision logic  
- Faster recovery from disruptions  

Crew scheduling thus transitions from manual planning to formal network optimization.

---

# 🏁 Conclusion

Crew scheduling is fundamentally a binary assignment optimization problem with complex temporal, regulatory, and qualification constraints.

A properly formulated MILP provides:

- Feasible schedules  
- Cost-optimal assignments  
- Resilient operations  
- Scalable workforce planning  

In modern aviation systems, optimization is not an enhancement — it is infrastructure.

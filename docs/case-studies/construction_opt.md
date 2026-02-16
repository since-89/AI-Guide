# Construction Project Optimization: Time–Cost Tradeoff Modeling

Construction project management involves balancing:

- Project duration  
- Resource allocation  
- Budget constraints  
- Equipment scheduling  
- Workforce planning  

Time–Cost Tradeoff (TCT) optimization helps determine:

> The minimum project cost for a required deadline  
or  
> The minimum completion time within a budget

---

# 1️⃣ Problem Definition

Let:

- \( i \in A \) = set of project activities  
- \( d_i \) = duration of activity \( i \)  
- \( c_i(d_i) \) = cost of activity \( i \)  
- \( P(i) \) = predecessor set of activity \( i \)  

Each activity has:

- Normal duration \( d_i^N \)  
- Crash duration \( d_i^C \)  
- Normal cost \( C_i^N \)  
- Crash cost \( C_i^C \)

---

# 2️⃣ Decision Variables

\[
d_i = \text{Chosen duration of activity } i
\]

\[
S_i = \text{Start time of activity } i
\]

\[
T = \text{Total project duration}
\]

---

# 3️⃣ Objective Function

## Option A — Minimize Total Project Cost

\[
\min \sum_{i \in A} c_i(d_i)
\]

Where cost is typically linear between crash and normal:

\[
c_i(d_i) =
C_i^N + \left( \frac{C_i^C - C_i^N}{d_i^N - d_i^C} \right)(d_i^N - d_i)
\]

---

## Option B — Minimize Project Completion Time

\[
\min T
\]

Subject to cost budget constraint:

\[
\sum_{i \in A} c_i(d_i) \le B
\]

---

# 4️⃣ Precedence Constraints (CPM Structure)

For each activity \( i \):

\[
S_i \ge S_j + d_j
\quad \forall j \in P(i)
\]

Ensures proper sequence.

---

# 5️⃣ Project Duration Definition

\[
T \ge S_i + d_i
\quad \forall i \in A
\]

Project duration equals maximum completion time.

---

# 6️⃣ Duration Bounds

\[
d_i^C \le d_i \le d_i^N
\]

Cannot exceed normal or crash limits.

---

# 7️⃣ Resource Constraint (Optional Extension)

If limited resource capacity \( R \):

\[
\sum_{i \in A} r_i(t) \le R
\quad \forall t
\]

Where \( r_i(t) \) = resource usage at time \( t \).

This transforms the model into a **Resource-Constrained Project Scheduling Problem (RCPSP)**.

---

# 8️⃣ Equipment Allocation Extension

Let:

- \( E \) = set of equipment types  
- \( y_{ie} = 1 \) if activity \( i \) uses equipment \( e \)

Constraint:

\[
\sum_{i} y_{ie} \le \text{Available Equipment}_e
\]

---

# 9️⃣ MILP Compact Form

\[
\min \sum_{i} c_i(d_i)
\]

Subject to:

- Precedence constraints  
- Duration bounds  
- Resource limits  
- Project completion definition  

---

# 🔟 Business Impact

Optimization enables:

- Reduced project delays  
- Lower cost overruns  
- Efficient equipment use  
- Better contractor scheduling  
- Improved cash flow forecasting  

---

# 🏁 Conclusion

Construction optimization transforms project management from manual CPM adjustments into a structured mathematical scheduling framework.

By solving time–cost tradeoff and resource allocation simultaneously, firms achieve:

- Predictable completion  
- Cost control  
- Operational transparency  

Optimization makes large-scale infrastructure delivery systematic and data-driven.

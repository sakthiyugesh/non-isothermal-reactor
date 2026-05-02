# 🔬 Dynamic Non-Isothermal CSTR Simulation (Reaction + Energy Balance)

This project models a **non-isothermal Continuous Stirred Tank Reactor (CSTR)** with a multi-reaction network using Python.

It captures how **reaction kinetics, temperature, and residence time** interact to determine:
- Conversion
- Product distribution
- Reactor temperature
- Optimal reactor volume

---

## 🚀 Project Overview

We simulate a reacting system with:

### Reaction Network
- **A + B → C**  (Main desired reaction)
- **A → D**      (Parallel side reaction)
- **C → E**      (Consecutive degradation)

This creates a realistic trade-off:
- More residence time → more C formation  
- But too much time → C converts to E  

👉 Result: **C has an optimal reactor volume (maximum point)**

---

## ⚙️ Model Description

### Mass Balance (CSTR)

For each component:

dCi/dt = (F/V)(Ci_in - Ci) + Ri


---

### Energy Balance

dT/dt = (F/V)(T_in - T) + Q_rxn / (ρ Cp)


Where:

- Q_rxn = Σ (−ΔH × r)
- Exothermic reactions increase temperature

---

### Residence Time

τ = V / F

This is the **most important design variable**.

---

## 🧪 Units Used (Strict SI System)

| Parameter            | Unit        |
|---------------------|------------|
| Concentration       | mol/m³     |
| Volume              | m³         |
| Flow rate           | m³/s       |
| Temperature         | K          |
| Heat of reaction    | J/mol      |
| Density             | kg/m³      |
| Heat capacity       | J/kg·K     |

⚠️ Important:
Switching from mol/L → mol/m³ increases concentration by **1000×**,  
which increases second-order reaction rates by **10⁶×** if not handled correctly.

---

## 📊 Key Results

### 1. Temperature Behavior
- Reactor temperature increases due to exothermic reactions
- Higher volume → higher temperature rise

### 2. Product Formation (C / IBA)
- Initially increases with volume
- Then decreases due to:
  - Consecutive reaction (C → E)
- Leads to an **optimal reactor size**

### 3. Residence Time Effect
- Low τ → incomplete reaction
- High τ → overreaction (product loss)
- Optimal τ balances both

---

## 🧠 Engineering Insights

- **Unit consistency is critical**  
  Small mistakes can change results by orders of magnitude

- **Second-order reactions are highly sensitive**  
  (Concentration scaling effect)

- **Temperature is governed by energy balance, not entropy intuition**

- **Optimal design is not max conversion — it's max desired product**

---

## 📁 Project Structure

--model.py


---

## ▶️ How to Run

```bash
pip install numpy scipy matplotlib
python model.py
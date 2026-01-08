# RosterAI: Intelligent & Fair Employee Scheduler for German QSRs

## 📋 Overview

**RosterAI** is an intelligent Decision Support System (DSS) designed specifically for Quick Service Restaurants (QSRs) in Germany. It solves the "Scheduling Trilemma" by balancing three critical, often conflicting goals:

1. **Legal Compliance:** Strictly enforces the German *Arbeitszeitgesetz* (Work Time Act), including the complex 11-hour mandatory rest period.
2. **Operational Efficiency:** Optimizes staff allocation to meet fluctuating demand without unnecessary labor costs.
3. **Employee Fairness:** Uses AI to ensure "bad shifts" (nights/weekends) are distributed equitably, reducing burnout and turnover.

Unlike "black box" automated schedulers, RosterAI features a **Human-in-the-Loop Feedback System**. It learns from the manager's manual edits, adapting its logic to local preferences over time.

---

## 🚀 Key Features

* **🇩🇪 German Labor Law Native:** Built-in hard constraints for §5 ArbZG (11h rest), max daily hours, and Sunday work rules.
* **⚖️ Fairness Engine:** Calculates and visualizes the **Gini Coefficient** for shift distribution. It proves mathematically that the roster is fair.
* **🧠 Reinforcement Learning Loop:** The system learns from your Excel edits. If you override the AI, it treats your choice as a new rule for future schedules.
* **📈 Explainable AI (xAI):** Generates transparent reports explaining *why* a schedule was created (e.g., "High unfairness due to limited availability on weekends").
* **📊 Excel-Based UI:** No complex software installation. Managers view and edit schedules in a familiar Excel format with traffic-light color coding.

---

## 🛠️ The Architecture

The system operates in a 4-step circular workflow:

### 1. The Scenario Builder (`sample.json`)

Generates realistic test data, including 20 employees with distinct contracts (Full-time, Part-time, Minijob) and specific "Wishlist" availability constraints.

### 2. The Logic Core (Solver)

Uses **Google OR-Tools (CP-SAT)** to solve the combinatorial optimization problem. It handles:

* **Integer Scaling:** Converts 8.5h shifts into integer units for precise calculation.
* **Anti-Clopening Logic:** Strictly forbids Late Shift (End 23:30)  Early Shift (Start 03:00) sequences.

### 3. The Dashboard & xAI

Outputs a user-friendly Excel file (`Monthly_Schedule.xlsx`) and generates immediate visual analytics:

* **Efficiency Plots:** Target vs. Actual hours.
* **Lorenz Curve:** Visual proof of fair shift distribution.

### 4. The Feedback Loop

Reads the manager's edited Excel file, identifies manual overrides, and updates the system's "Learned Weights." The next run will prioritize these human preferences.

---

## 💻 Installation & Usage

### Prerequisites

* Python 3.8+
* Google OR-Tools
* Pandas & OpenPyXL
* Matplotlib

```bash
pip install ortools pandas openpyxl matplotlib

```

### Quick Start Guide

1. **Generate Data (Block 1):**
Run the data generation script to create `sample.json`.
```python
# Run Block 1 Code

```


2. **Run Solver (Block 2):**
Execute the logic core to calculate the optimal schedule.
```python
# Run Block 2 Code

```


3. **Generate Report (Block 3):**
Create the Excel file and view the fairness plots.
```python
# Run Block 3 Code

```


4. **Manager Review (The Human Step):**
* Open `Monthly_Schedule.xlsx`.
* Make manual edits (e.g., move a shift).
* Save and close.


5. **Train the AI (Block 4):**
Feed the edits back into the system.
```python
# Run Block 4 Code

```


*Rerun Block 2 to see the AI apply your new preferences!*

---

## 📊 Metrics & Validation

RosterAI uses the **Gini Coefficient** as its primary fairness metric.

* **0.0:** Perfect Equality (Everyone shares night shifts equally).
* **1.0:** Maximum Inequality (One person does all the bad shifts).
* **Thesis Target:** < 0.15 (Proven to reduce turnover).

---

## 📝 License

This project is part of a Bachelor's Thesis at **Gisma University of Applied Sciences**.

* **Author:** Aman Panchal
* **Date:** December 2025

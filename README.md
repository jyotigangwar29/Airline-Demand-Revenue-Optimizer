# FlightMax: Airline Demand & Revenue Optimizer  
*An intelligent simulation-driven system for optimizing ticket pricing and overbooking policies under uncertainty*

---

## Project Overview

**FlightMax** addresses a real-world challenge in airline operations: **how to maximize revenue through strategic overbooking without incurring costly passenger rejections.** Since not all passengers show up on departure day, airlines often oversell tickets. However, when too many arrive, the resulting compensation costs and brand damage can significantly reduce profit.

This project models the **optimal pricing and overbooking strategy** using a dynamic programming framework. It simulates customer demand, show-up behavior, and pricing sensitivity across a 365-day booking horizon to help airlines make data-driven decisions that balance profit and risk.

---

## Problem Statement

- **Ticket Classes**: Coach (100 seats) and First-Class (20 seats)  
- **Overbooking Policy**: Up to 20 additional coach tickets can be sold  
- **Customer Behavior**:
  - Coach no-show rate: 5%
  - First-Class no-show rate: 3%
- **Objective**: Maximize **expected discounted profit** while minimizing overbooking costs and customer rejections

---

## Approach

The solution is structured using a **recursive dynamic programming model**, supported by probabilistic modeling and extensive simulation.

Key components include:
- Recursive value functions to model future profit based on current decisions
- Binomial distributions to simulate realistic show-up behavior
- Strategic pricing decisions with multiple options per day
- Terminal cost modeling on the day of flight for rejected passengers
- LRU caching to optimize computation of repeated subproblems

---

## Policies Modeled

1. **Fixed Overbooking**:  
   A static policy that permits a fixed number of oversold seats (e.g., 105 total coach tickets).

2. **Flexible Overbooking with “No-Sale” Option**:  
   Allows the airline to deliberately **skip selling a coach ticket** on specific days to avoid future risk.

3. **Seasonality-Aware Strategy**:  
   Adjusts demand probabilities as the flight date approaches, simulating last-minute booking surges.

4. **Simulation Analysis**:  
   10,000+ forward simulations of each policy under normal and stressed scenarios (e.g., increased show-up rates) to evaluate robustness.

---

## Results & Insights

- **Optimal overbooking level** under fixed policy: **9 extra coach tickets**  
  - Expected profit: ~$42,134  
- **Flexible "No-Sale" policy** slightly improved profit and reduced volatility  
- **Seasonality-aware strategy** provided a modest uplift with improved adaptability  
- In high-risk scenarios (e.g., higher show-up rates), rigid overbooking caps offered more control  
- Simulation revealed trade-offs between **maximized revenue, customer experience, and operational risk**

---

## Business Impact

**FlightMax** presents a decision-support system that can be applied across industries with:
- Perishable inventory (e.g., airline seats, hotel rooms, event tickets)
- Uncertain customer behavior
- Capacity constraints and demand-driven pricing

It enables companies to:
- Quantify risks of overbooking strategies
- Make defensible pricing decisions
- Design customer-aware policies based on historical show-up data

---

## Technologies

- **Python** – core modeling, recursion, simulation
- **Dynamic Programming** – for decision optimization
- **Binomial Modeling** – for probabilistic show-up behavior
- **Monte Carlo Simulation** – to evaluate policy performance under uncertainty


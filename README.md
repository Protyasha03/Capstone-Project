# 🚗 Dynamic Pricing for Urban Parking Lots – Summer Analytics 2025

![Architecture Diagram](architecture_diagram.png)

## 📌 Overview

This project implements a dynamic pricing system for urban parking lots. Using real-time data such as occupancy, vehicle type, traffic conditions, and queue lengths, it dynamically calculates and adjusts the price of parking slots. The goal is to optimize utilization, reduce congestion, and balance supply-demand through intelligent pricing.

## 🛠 Tech Stack

- *Python* – Data processing and modeling
- *Pandas & NumPy* – Data manipulation and numerical calculations
- *Pathway* – Stream-based data pipeline
- *Bokeh* – Interactive visualization
- *Google Colab* – Development environment
- *GitHub* – Version control and repository

## 🧠 Project Architecture & Workflow

The system processes CSV-based parking data and computes dynamic prices using three models. It then visualizes the pricing history per parking lot using Bokeh.

### 🔄 Workflow:

1. *Upload CSV* containing live parking data.
2. *Parse timestamp* from date and time fields.
3. *Clean & preprocess*: handle missing values, ensure numeric formats.
4. *Distance matrix*: Haversine function computes distances between lots.
5. *Model 1*: Baseline pricing based on occupancy.
6. *Model 2*: Adjust pricing based on demand score:
   - Includes vehicle type, queue, traffic, and special days.
7. *Model 3*: Competitive adjustment based on nearby lots.
8. *Visualize*: Display price evolution for each lot.

## 🧮 Models Used

### Model 1: Baseline Price

Adjusts based on current occupancy:

python
price = prev_price + α × (occupancy / capacity)

### Model 2: Demand Price
Scores demand using multiple features:
score = 1.0 × (occupancy / capacity) +
        0.8 × (queue_length / capacity) -
        0.6 × traffic_weight +
        0.7 × is_special_day +
        vehicle_weight

The score is then normalized using a sigmoid function and scaled into the price range.

### Model 3: Competitive Price
Modifies price if nearby lots are significantly cheaper or more expensive:

Decrease price by 10% if any nearby lot is 10% cheaper.

Increase price by 5% if all nearby lots are more expensive.

### 📊 Visualization
Interactive line charts per parking lot

Real-time price over time using Bokeh

### 🧾 Assumptions
Demand directly correlates with occupancy, vehicle type, and external conditions.

All lots have a baseline price of $10.

Radius for competitive lots = 0.5 km.

Traffic data is categorized into low, medium, and high.

Pricing must remain between 5 and 20 dollars.


### 📁 Repository Contents
Anirban Capstone_Project.ipynb – Complete Jupyter Notebook

dataset.csv – Sample dataset

architecture_diagram.png – Architecture workflow

README.md – Project documentation

👨‍💻 Author
Protyasha Pahari

GitHub: @Protyasha03

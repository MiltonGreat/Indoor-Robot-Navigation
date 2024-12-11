# Indoor Robot Navigation with Reinforcement Learning

This project explores data obtained from navigating a real robot in indoor settings. The dataset is instrumental for developing navigation algorithms, performing feature engineering, and implementing reinforcement learning (RL) models to train a robot to adapt and navigate autonomously.

### Overview

The primary objective of this project is to process robot navigation data and use it to train machine learning and reinforcement learning models. These models aim to:

- Predict the surface type (smooth or rough).
- Train a robot to navigate effectively using RL algorithms like Proximal Policy Optimization (PPO).
- Visualize important metrics and insights from the navigation data.

### Dataset

The dataset consists of JSON files that record robot sensor data during navigation. Key features include:

- direction: Clockwise (cw) or counter-clockwise (ccw) movement.
- pose: Robot's position data.
- dists: Obstacle distances from the robot using LiDAR.
- angles: Angles corresponding to LiDAR readings.
- brake: Whether brakes are applied (1 for yes, 0 for no).
- counts_left and counts_right: Speeds of the left and right wheels, respectively.
- surface: Type of surface (smooth or rough).

The dataset contains a total of 13,139 records combined from smooth and rough surfaces.

### Feature Engineering

The following features were engineered:

- min_dist, mean_dist, max_dist: Minimum, average, and maximum distances from obstacles.
- speed_ratio: Ratio of left-wheel speed to right-wheel speed.
- surface_encoded: Numerical encoding for surface types.

### Machine Learning Model

A Random Forest Classifier was trained to predict surface types using the engineered features. Key results:

- Accuracy: 87%
- Precision: 86% for smooth surfaces, 87% for rough surfaces.
- Recall: 90% for smooth surfaces, 82% for rough surfaces.

### Reinforcement Learning

Using Stable-Baselines3 and the Proximal Policy Optimization (PPO) algorithm:

An RL environment was defined with:

- State Space: Normalized features from the dataset.
- Action Space: [0: Brake, 1: Move forward, 2: Turn].
- Reward System: Safe navigation rewards, collision penalties, and goal-reaching incentives.

The model was trained for 10,000 timesteps to optimize navigation performance.

### Visualization

Key visualizations include:

- Surface type distribution.
- Brake usage frequency.
- Scatter plot of wheel speeds by surface type.
- Distribution of minimum, mean, and maximum distances.

### Results

The project successfully implemented:

- Surface type prediction using Random Forest with 87% accuracy.
- Reinforcement learning for autonomous navigation using PPO.

### Source

https://www.kaggle.com/datasets/narayananpp/indoor-robot-navigation-dataset-irnd

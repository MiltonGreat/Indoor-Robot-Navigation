# Indoor Robot Navigation with Reinforcement Learning

This project delves into the intersection of robotics and machine learning, leveraging Reinforcement Learning (RL) to enable autonomous robot navigation in indoor environments. By combining surface type classification with the Proximal Policy Optimization (PPO) algorithm, the project demonstrates how robots can adapt dynamically to varying terrains and obstacles, paving the way for smarter navigation systems.

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

### Problem Statement

Robots navigating real-world environments face challenges like dynamic terrains, unforeseen obstacles, and the need for real-time decision-making. Traditional rule-based navigation systems lack the adaptability to handle these complexities, leading to inefficiencies and safety risks.

This project addresses the following challenges:

    Classifying surfaces (smooth or rough) to adjust navigation strategies dynamically.
    Enabling robots to learn navigation policies autonomously using RL.
    Ensuring safe and efficient movement through a custom-designed reward system.

### Solution Approach

Step 1: Surface Type Prediction
- Objective: Classify surfaces as smooth or rough using sensor data to adjust movement strategies dynamically.
- Methodology:
  - Trained a supervised machine learning model on raw sensor data.
  - Applied preprocessing techniques like normalization and feature extraction.

Step 2: Reinforcement Learning with PPO
- Algorithm: Proximal Policy Optimization (PPO).
- Workflow:
  - Initialized the environment with obstacles, varying surfaces, and predefined goals.
  - Allowed the robot to interact with the environment, receiving rewards for safe and goal-oriented navigation.
  - Updated the robot's policy iteratively to maximize cumulative rewards.

Step 3: Custom OpenAI Gym Environment
- Key Features:
  - Simulated indoor environments with smooth and rough surfaces.
  - Integrated real-world sensor data for encoding states and dynamics.
  - Implemented a reward system encouraging safe, efficient, and goal-oriented navigation.

Step 4: Designing Rewards and Actions
- Action Space:
  - Brake: Avoid collisions.
  - Move Forward: Navigate in the current direction.
  - Turn: Adjust direction to avoid obstacles.

- Reward System:
  - Positive Rewards: Reaching goals and avoiding collisions.
  - Negative Rewards: Collisions and leaving the navigation area.
  - Neutral Rewards: Penalties for idle or inefficient actions.

Step 5: Visualization and Evaluation
- Visual Insights:
  - Trajectories: Displayed the robot's navigation patterns.
  - Surface Type Distribution: Showed the balance between smooth and rough surface data points.
  - Brake Usage: Highlighted the frequency of brake applications for safety analysis.

- Metrics:
  - Evaluated learning progress through cumulative rewards per episode.
  - Monitored goal-reaching success rates to ensure effective navigation.

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

### Reinforcement Learning

Using Stable-Baselines3 and the Proximal Policy Optimization (PPO) algorithm:

An RL environment was defined with:

- State Space: Normalized features from the dataset.
- Action Space: [0: Brake, 1: Move forward, 2: Turn].
- Reward System: Safe navigation rewards, collision penalties, and goal-reaching incentives.

The model was trained for 10,000 timesteps to optimize navigation performance.

### Future Directions

1. Real-World Testing: Deploy the trained agent in real robotic systems.
2. Enhanced Environment Complexity: Introduce more diverse terrains and dynamic obstacles.
3. Multi-Agent Collaboration: Explore RL techniques for coordinating multiple robots.
4. Energy Optimization: Incorporate energy consumption as a factor in navigation strategies.

### Source

https://www.kaggle.com/datasets/narayananpp/indoor-robot-navigation-dataset-irnd

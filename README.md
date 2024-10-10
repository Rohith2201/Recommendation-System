# Reinforcement Learning for Personalized Product Recommendation

## Project Overview

This project integrates reinforcement learning (RL) into personalized product recommendation systems, focusing on a Monte Carlo RL model that considers both user preferences and budget constraints. The goal is to recommend products by optimizing for both customer satisfaction and budget compliance, providing a dynamic, personalized shopping experience.

### Key Highlights:
- **Monte Carlo RL**: A model-free reinforcement learning approach, utilizing episodes to simulate and evaluate user interactions with products.
- **Budget Constraints**: Recommendations are optimized based on user-defined budget limits, ensuring product suggestions are both personalized and financially feasible.
- **Reward Signals**: The model's performance is analyzed under various reward signal schemes to understand how reward parameters affect convergence and recommendation quality.

## Techniques Used

### Monte Carlo Methods:
- **Episode-Based Learning**: The agent interacts with the environment, gathering data over complete episodes, and revises its value estimates based on the observed returns.
- **Value Estimation**: For a state or state-action pair, the value is estimated by averaging the returns collected from multiple episodes.
- **First-Visit & Every-Visit Methods**: Two approaches for value estimation. First-Visit updates the value on the agent's first visit to a state within an episode, while Every-Visit updates the value every time the state is visited.
- **Exploration vs Exploitation**: The agent balances exploration (trying new actions) and exploitation (selecting the best-known actions based on value estimates).

## Process Flow

1. **Data Preparation**:
   - Organize and structure the input data (user preferences, product features, and budget) required for the RL model.
   
2. **Initialization**:
   - Set initial state values (V) for each action (product). These initial estimates serve as the starting point for the learning process.

3. **Episode Generation**:
   - Simulate episodes in which the agent interacts with the environment (product catalog) and selects products based on user preferences and budget constraints.
   
4. **Terminal Reward Calculation**:
   - After each episode, calculate a terminal reward based on whether the selected products' total cost falls within the specified budget.

5. **Value Update**:
   - Update the value estimates for each action based on the terminal rewards and observed state-action pairs during the episode.


## How to Run

1. **Install Dependencies**:
   Make sure you have Python installed, then run:
   ```bash
   pip install -r requirements.txt
   ```

2. **Run the Model**:
   Execute the Monte Carlo RL script to train the model and evaluate recommendations:
   ```bash
   python src/monte_carlo_rl.py
   ```

3. **Analyze Results**:
   Check the `results/` directory for performance metrics and insights on the recommendation quality.

## CODE EXECUTION
The Code implements a Monte Carlo model for decision making with epsilon-greedy exploration.

**Imports:**

- `pandas` for data manipulation
- `numpy` for numerical computations
- `matplotlib.pyplot` for plotting
- `warnings` to suppress warnings

**Function Definition:**

```python
def MCModelv1(data, alpha, e, epsilon, budget, reward):
  # ... function body ...
```

**Function Arguments:**

- `data`: Pandas DataFrame containing product information
- `alpha`: Learning rate for updating V values
- `e`: Number of episodes (simulations)
- `epsilon`: Exploration rate for epsilon-greedy selection
- `budget`: Budget constraint for selecting products
- `reward`: List of rewards for each product (currently not used)

**Function Body:**

1. **Define States:**
    - Identify unique ingredients (products) from the data.

2. **Initialize V_0:**
    - Set the initial value (V_0) for each product in the data. V_0 represents the expected value of an action (product).

3. **Iterate Over Episodes:**
    - Loop for the specified number of episodes (e).

4. **Episode Run:**
    - For each episode:
        - Implement epsilon-greedy selection:
            - If it's the first episode (random selection): Choose a random product for each ingredient.
            - Otherwise:
                - With probability `epsilon`, randomly choose a product for each ingredient.
                - With probability (1 - epsilon), choose the product with the highest V value for each ingredient.
    
5. **Calculate Terminal Reward:**
    - Check if the selected products fit within the budget.
        - If yes, set the terminal reward to 1.
        - If no, set the terminal reward to -1.

6. **Update V Values:**
    - Update the V value for each product based on the selected product, the terminal reward, and the learning rate (`alpha`).

7. **Output:**
    - Return various outputs including:
        - Sum of V for all actions at each episode
        - Sum of V for the cheapest and expensive actions
        - Optimal actions selected based on V values
        - Actions chosen in each episode

**Model Execution:**

- Set hyperparameters (alpha, epsilon, budget, etc.).
- Call the `MCModelv1` function with the data and hyperparameters.
- The function returns various outputs for analysis.

**Plotting and Analysis:**

- The code uses `matplotlib` to plot various aspects of the model's behavior, such as the sum of V values over episodes and the optimal actions chosen.

**Interactive Visualization (Commented Out):**

- The code includes commented-out sections for creating interactive visualizations using `plotly`.
- These sections demonstrate how to create animations to explore the impact of different hyperparameters on model performance.

Overall, this code implements a Monte Carlo model for decision making with epsilon-greedy exploration. You can adjust the hyperparameters and analyze the outputs to understand how the model behaves and choose the best actions in your specific scenario.

## Future Work

- **Advanced RL Algorithms**: Explore more sophisticated reinforcement learning techniques like Q-learning or deep RL for enhanced precision.
- **Real-World Data**: Apply the model to real-world datasets to further validate its effectiveness and refine its performance.

## Contributing

Feel free to open issues or submit pull requests if you'd like to contribute to this project.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
```

This `README.md` provides a clear overview of the project, the techniques used, the process, and instructions on how to run the model. Let me know if you'd like to add or adjust anything!

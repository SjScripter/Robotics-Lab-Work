# AISR Laboratory Work (CSAI4014)
**Algorithms for Intelligent Systems and Robotics**  
*School of Computer Science, UPES Dehradun*  
*B.Tech CSE (AI & ML), Semester VII | Autumn Semester 2026–27*

---

## Student Information
- **Student Name:** Sarthak Jakhmola
- **SAP ID:** 500122482
- **Roll Number:** R2142231632
- **Batch / Cohort:** B2
- **Partner Details:** Individual
- **Course Teacher:** Dr. Resham Raj Shivwanshi

---

## Repository Structure & Index
```text
Robotics-Lab-Work/
├── README.md                               # Student details, repository index, sources & AI declaration
├── AISR_LabReport_500122482_SarthakJakhmola_B2.docx # Completed lab report in official Word template
├── exp01-signals/                          # Exp 1: Time and Frequency Domain, and Pendulum
│   ├── exp01.ipynb
│   └── figs/ (fig1_1 to fig1_5)
├── exp02-queens/                           # Exp 2: Eight Queens (Backtracking vs Generate & Test)
│   ├── exp02.ipynb
│   └── figs/ (fig2_1 board, fig2_2 runtime)
├── exp03-search/                           # Exp 3: BFS and DFS Maze Navigation
│   ├── exp03.ipynb
│   └── figs/ (fig3_1 paths, fig3_2 frontier size)
├── exp04-hillclimb/                        # Exp 4: Hill Climbing & Random Restarts
│   ├── exp04.ipynb
│   └── figs/ (fig4_1 landscape, fig4_2 restarts)
├── exp05-rl/                               # Exp 5: Tabular Q-Learning Grid World
│   ├── exp05.ipynb
│   └── figs/ (fig5_1 learning curves, fig5_2 policy grid)
├── exp06-neural/                           # Exp 6: Simple Neural Network (NumPy MLP on XOR)
│   ├── exp06.ipynb
│   └── figs/ (fig6_1 loss curves, fig6_2 decision boundary)
├── exp07-webots/                           # Exp 7: Webots Swarm & Pioneer Lidar Navigation
│   ├── controllers/
│   ├── runs/*.csv
│   ├── figs/ (fig7_1 to fig7_4)
│   └── NOTES.md
└── exp08-xembody/                          # Exp 8: Cross-Embodiment Transfer (PyBullet)
    ├── results/*.csv
    ├── figs/ (fig8_1 to fig8_5)
    ├── exercises/
    └── NOTES.md
```

---

## Experiments Summary

### Experiment 1: Time and Frequency Domain, and the Pendulum
- Generated multi-frequency composite signal (5 Hz, 20 Hz, 50 Hz with amplitudes 1.0, 0.5, 0.25) sampled at $f_s = 500\text{ Hz}$.
- Verified frequency spectrum via discrete Fourier transform (`rfft`), accurately locating peak frequencies and amplitudes within numerical tolerance.
- Demonstrated signal aliasing by under-sampling a 5 Hz sine wave at 8 Hz, proving the folding effect at $|f_s - f| = 3\text{ Hz}$.
- Performed numerical integration of nonlinear pendulum dynamics with varying damping coefficients ($b = 0, 0.3, 2.0$) and demonstrated the divergence of period $T$ at large amplitudes ($5^\circ$ to $175^\circ$).

### Experiment 2: The Eight Queens Problem
- Formulated the 8-Queens problem as a Constraint Satisfaction Problem (CSP).
- Implemented and evaluated recursive backtracking with pruning against full permutation generate-and-test across board sizes $n = 4$ to $10$.
- Demonstrated exponential speedup and order-of-magnitude reduction in state expansions by pruning invalid subtrees early using directional checks.

### Experiment 3: Breadth-First and Depth-First Search
- Modeled a 2D discrete grid maze ($15 \times 15$) as an implicit state graph.
- Unified BFS and DFS into an identical algorithmic structure differing only by FIFO queue (`popleft()`) versus LIFO stack (`pop()`).
- Compared memory footprint (frontier size) and path optimality: BFS guaranteed the shortest path (28 steps, 61 expansions) with larger memory, while DFS aggressively probed deeper (32 steps, 37 expansions) with minimal memory.

### Experiment 4: Hill Climbing
- Implemented local search hill climbing on the 8-queens problem and continuous multimodal benchmark landscapes.
- Quantified failure modes including local optima, plateaus, and ridges (base success rate $p \approx 14.8\%$).
- Implemented random-restart hill climbing, validating the theoretical success scaling $P = 1 - (1-p)^k$ reaching $96.5\%$ for $k=20$.

### Experiment 5: Reinforcement Learning (Tabular Q-Learning)
- Implemented off-policy tabular Q-learning on a $5 \times 5$ Grid World MDP with terminal goal ($+10$), traps ($-5$), and living cost ($-0.1$).
- Evaluated exploration parameter $\epsilon \in \{0.01, 0.10, 0.20, 0.50\}$, demonstrating that balanced exploration ($\epsilon = 0.10$) successfully converged to the optimal shortest-path policy while avoiding dangerous trap states.

### Experiment 6: A Simple Neural Network
- Constructed a 2-layer Multi-Layer Perceptron (2-4-1) in pure NumPy (no external deep learning frameworks).
- Trained using backpropagation and gradient descent to solve the non-linearly separable XOR problem.
- Analyzed learning rate sensitivity ($\eta \in \{0.1, 0.5, 2.0\}$), achieving near-zero MSE ($< 0.0001$) and generating smooth non-linear decision boundary contours.

### Experiment 7: Mobile Robot Simulation in Webots (Reactive Swarm & Lidar Navigation)
- Simulated a 5-robot e-puck swarm in a bounded arena using reactive Braitenberg infrared obstacle avoidance.
- Simulated Pioneer 3-DX differential drive robot with 2D Lidar in an $8\text{ m} \times 8\text{ m}$ room using Follow-The-Gap navigation.
- Evaluated cruise speed trade-offs and safety bubble sizing, proving that safety bubbles smaller than the robot's half-width ($0.15\text{ m}$) cause wall collisions.

### Experiment 8: Cross-Embodiment Transfer of Manipulation Skills (PyBullet)
- Evaluated policy transfer across four distinct robot arms (KUKA iiwa, Franka Panda, xArm6, KUKA Mini).
- Proved that joint-space trajectory replay fails completely across different kinematic morphologies ($0\%$ transfer success).
- Proved that task-space end-effector Cartesian velocity control ($\Delta x$) enables robust zero-shot cross-embodiment transfer ($> 90\%$ success on Franka Panda and xArm6).

---

## Sources & AI Tools Declaration (Appendix B)
All work was generated and executed directly. Reference materials and AI tools used:
1. *Laboratory Report Guidelines & AISR Sample Lab Report*, Dr. Resham Raj Shivwanshi, UPES Dehradun, 2026.
2. S. Russell and P. Norvig, *Artificial Intelligence: A Modern Approach*, 4th ed., Pearson, 2020.
3. R. S. Sutton and A. G. Barto, *Reinforcement Learning: An Introduction*, 2nd ed., MIT Press, 2018.
4. Google Antigravity Assistant (AI Agent): Used for generating simulation scaffolding, automated parameter sweep scripts, and document formatting. All code was independently verified and executed.


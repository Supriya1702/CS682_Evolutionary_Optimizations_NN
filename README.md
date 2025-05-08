# 🧬 Evolutionary Optimization of Deep Neural Network Architectures

This project explores **gradient-free optimization** of Convolutional Neural Networks (CNNs) using **evolutionary algorithms** on the CIFAR-10 dataset. By integrating **tournament** and **lexicase selection**, this hybrid framework discovers optimized CNN architectures that balance **accuracy, complexity, and training time**.

---

## 📌 Overview

**Team Members:**
- Supriya Kumari – [supriyakumar@umass.edu](mailto:supriyakumar@umass.edu)
- Kavisha Ghodasara – [kghodasara@umass.edu](mailto:kghodasara@umass.edu)
- Subhangi Choudhary – [subhangichou@umass.edu](mailto:subhangichou@umass.edu)

**Course:** COMPSCI 682 - Neural Networks  
**Institution:** University of Massachusetts Amherst

---

## 🧠 Core Contributions

- **Evolutionary Architecture Search**: Hybrid selection with tournament (exploit early) and lexicase (diversify late).
- **Multi-objective Fitness Evaluation**:
  - Accuracy
  - Model Complexity (params)
  - Training Time
- **Genetic Operations**:
  - Two-point crossover
  - Controlled mutation
  - Elitism for performance preservation

---

## 🛠️ Tools & Frameworks

- [DEAP](https://github.com/DEAP/deap): Evolutionary algorithms
- TensorFlow / Keras: CNN definition & training
- NumPy, Matplotlib: Data manipulation & visualization

---

## 📂 Project Structure

```bash
.
├── evolution/               # Evolution strategy (selection, crossover, mutation)
├── cnn_models/              # CNN architecture generation
├── data/                    # CIFAR-10 loading & preprocessing
├── experiments/             # Experiment logs and result plots
├── config.py                # Evolution hyperparameters
├── main.py                  # Training & evolution execution script
└── README.md
```

---

## 🧪 Results Summary

| Experiment | Architecture | Test Accuracy | Test Loss |
|------------|--------------|----------------|-----------|
| Exp 1 | Conv(64, ReLU) → Conv(128, Tanh) → Dense(128, Tanh) | 64.7% | 1.87 |
| Exp 2 | 3 × Conv(64) [ReLU/Tanh] | 67.9% | 0.95 |
| Exp 3 | 3 × Conv(64) [Tanh → ReLU → ReLU] | 71.1% | 1.23 |
| Exp 4 | 2 × Conv(64) + Dense(256, ReLU) | 58.6% | 3.59 |
| Exp 5 (weighted fitness) | 3 × Conv(64, ReLU) | 70.17% | 0.96 |
| Exp 6 (weighted fitness) | Conv(16 → 64 → 64, mixed) | 63.88% | 2.70 |
| **With Elitism** | Conv(16 → 64 → 64, ReLU) | **73.82%** |  – |

---

## 🧬 Genetic Strategy

- **Initialization**: Randomized CNN genome (filters, activations, layers)
- **Selection**:
  - Tournament (first half): Exploits best candidates
  - Lexicase (second half): Ensures diversity and Pareto-optimality
- **Crossover**: Two-point genetic recombination
- **Mutation**: Random layer or parameter change
- **Elitism**: Preserves top-k architectures each generation

---

## ⚖️ Fitness Configurations

| Scenario | Accuracy | Complexity | Time |
|----------|----------|------------|------|
| Equal Weighting | 1.0 | -1.0 | -1.0 |
| Varied (Exp 5) | 1.0 | -0.5 | -0.2 |
| Varied (Exp 6) | 1.5 | -1.0 | -0.75 |

---

## 📊 Comparative Evaluation

| Model      | Accuracy | Notes |
|------------|----------|-------|
| **Evolved CNN (Elitism)** | **73.82%** | Compact, evolved |
| Hand-Crafted CNN | 75.02% | Manual design with Dropout, BatchNorm |
| ResNet50 (Transfer Learning) | 25.27% | Overfitted due to small image size |

---

## 🚀 How to Run

```bash
# Clone repository
git clone https://github.com/Supriya1702/CS682_Evolutionary_Optimizations_NN.git
cd CS682_Evolutionary_Optimizations_NN

# Install dependencies
pip install -r requirements.txt

# Run evolution
python main.py --generations 10 --pop_size 20 --elitism True
```

---

## 📌 Key Takeaways

- Evolutionary algorithms can **automate CNN design** with multi-objective trade-offs.
- **Elitism and hybrid selection** enhance robustness and convergence.
- Efficient architectures can be discovered **without manual tuning**.

---

## 📖 Citation

```
Supriya Kumari, Kavisha Ghodasara, Subhangi Choudhary. 
"Evolutionary Optimization of Deep Neural Network Architectures", Final Project – COMPSCI 682, UMass Amherst, Spring 2025.
```

--- 

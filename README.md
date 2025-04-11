# Quantum-CNN-TicTacToe

### Mini Project CS-2-14(PO)

---

**Authors:**
* Krishiv Trivedi [2023UMA0218]
* Piyush Kumar [2023UMA0227]
* Krishna [2023UEE0140]
* Jyoti Yadav [2023UEE0139]

**Supervisor:**
* Sumit Kumar Pandey

**Date:** 12th April, 2025

---

## 🚀 Introduction

Quantum computing represents a new computational paradigm built upon the principles of quantum mechanics. It utilizes qubits, harnessing phenomena like superposition and entanglement, to potentially accelerate solutions for complex problems, including NP-hard algorithms like the Knapsack problem and the Travelling Salesman Problem (TSP), and to enhance modern AI models.

This project delves into the theory of quantum circuits and algorithms, with a specific focus on **Quantum Convolutional Neural Networks (QCNNs)**. We explore their development, implement a quantum circuit-based **Quantum Residual Neural Network (QRNN)**, and compare the performance of QCNNs against traditional Classical Convolutional Neural Networks (CCCNs). The comparison analyzes key metrics like accuracy and cost function trends, considering current engineering limitations.

---

## ✨ Motivation

The advent of scalable quantum computers poses a threat to current cryptographic standards, highlighting the need for **Post-Quantum Cryptography**. This project initially explored this area before shifting focus to understanding which computational problems quantum computers can solve efficiently.

#### Key Drivers:
* **Solving Brute-Force Problems Faster:** Quantum algorithms leverage superposition (e.g., via Hadamard gates) to explore multiple solutions simultaneously. Grover's Algorithm, for example, offers a quadratic speedup for unstructured search problems, reducing complexity from O(2ⁿ) to O(2ⁿ/²).
* **Focus on QCNNs/QRNNs:** These architectures were chosen for their practical relevance at the intersection of quantum computing and machine learning. By implementing concepts from recent research (e.g., a 2024 paper on QRNNs), this project aims to contribute to this rapidly evolving field.
* **Implementation Tools:** We utilize **Qiskit** for quantum circuit simulation and **IBM's Quantum Platform** for executing experiments on real quantum hardware (within qubit limits). Simulating larger quantum systems (>15 qubits) remains a significant challenge on classical computers.

---

## 🛠️ Methodology & Implementation

Our approach involves several key steps:
1.  Develop and train a QCNN model.
2.  Develop and train an equivalent CCNN model using the same dataset.
3.  Compare the performance metrics (accuracy, loss trends) of both models.
4.  Integrate and evaluate 'Residual Blocks' within the QCNN architecture.

#### Dataset:
We used a dataset comprising all tic-tac-toe endgame positions that did not result in a draw. This dataset presents a higher complexity compared to typical QCNN benchmarks (e.g., simple pattern recognition), allowing us to test the limits of the QCNN model.

*Figure 1: Dataset and Convolution Model Overview*
| Generated Dataset Examples                             | Convolution Model Overview                         |
| :---------------------------------------------------: | :-----------------------------------------------: |
| ![_Figure 1a_](/Report/assets/dataset.jpeg)           | ![_Figure 1b_](/Report/assets/CCNN.png)            |
| *(a) Generated Dataset Examples* | *(b) Convolution Model Overview* |

#### Network Architectures:
* **CCNN:** `Input → C₃ₓ₃ → P₃ₓ₃,₂ₓ₂ → C₂ₓ₂ → P₂ₓ₂,₁ₓ₁ → Output`
* **QCNN:** `Input → C₃ₓ₃ → P₃ₓ₃,₂ₓ₂ → C₂ₓ₂ → P₂ₓ₂,₂ₓ₁ → C₂ₓ₁ → P₂ₓ₁,₁ₓ₁ → Output`
    *(Where C = Convolutional Layer, P = Pooling Layer)*

The QCNN incorporates additional components:
* **ZFeatureMap:** Encodes classical input data into quantum states (qubits).
* **Residual Blocks (R(x), R₂(x)):** Integrated based on recent research to potentially improve training dynamics.

*Figure 2: QCNN Layer Structure*
![_Figure 2_](/Report/assets/QCNN.png)

*Figure 3: Quantum Circuit Components*
| ZFeatureMap                       | R(x) Block                      | R2(x) Block                       |
| :-------------------------------: | :-----------------------------: | :-----------------------------: |
| ![_Figure 3a_](/Report/assets/zfm.png) | ![_Figure 3b_](/Report/assets/rb.png) | ![_Figure 3c_](/Report/assets/r2.png) |
| *(a) ZFeatureMap* | *(b) R(x)* | *(c) R₂(x)* |

| C Layer Element                        | P Layer Element                        |
| :------------------------------------: | :------------------------------------: |
| ![_Figure 3d_](/Report/assets/conv_element.png) | ![_Figure 3e_](/Report/assets/pool_element.png) |
| *(d) C Layer element* | *(e) P Layer element* |

#### Training Details:
* **CCNN:** Trained using the **Adam** optimizer with **Cross Entropy** loss.
* **QCNN:** Trained using the **COBYLA** optimizer with **Squared Error** loss.

---

## 📊 Results

#### Classical CNN (CCNN):
* **Accuracy:** 81.5 ± 1%
* **Training Epochs:** 300

*Figure 4: CCNN Results*
| CCNN Accuracy                        | CCNN Cross Entropy Loss                   |
| :----------------------------------: | :--------------------------------------: |
| ![_Figure 4a_](/Report/assets/accu.jpeg) | ![_Figure 4b_](/Report/assets/cf.jpeg)   |
| *(a) CCNN Accuracy* | *(b) CCNN Cross Entropy Loss* |

#### Quantum CNN (QCNN):
* **Accuracy (without Residual Blocks):** 77%
* **Training Epochs (without Residual Blocks):** 200

*Figure 5: QCNN Loss Comparison*
| QCNN Loss (without Residual Blocks)                  | QCNN Visualization (with Residual Blocks)             |
| :-------------------------------------------------: | :---------------------------------------------------: |
| ![_Figure 5a_](/Report/assets/qcnn.jpeg)            | ![_Figure 5b_](/Report/assets/image5b.png)             |
| *(a) QCNN Sqrd. Error Loss wo/Residual Blocks* | *(b) QCNN w/Residual Blocks (Visualization)* |

---

## ✅ Conclusion & Achievements

The baseline QCNN achieved a respectable accuracy (77%) in significantly fewer epochs (200) compared to the CCNN (which required ~100 epochs to reach similar levels, eventually peaking at 81.5% after 300 epochs).

This suggests that QCNNs hold promise, particularly as quantum hardware matures and overcomes the limitations of classical simulation. The exploration of residual blocks further contributes to understanding how to optimize these quantum neural network architectures.

*(Note: The placeholder image below was included in the report.)*
![_Figure 6_](/Report/assets/image6.png)
*Figure 6: Placeholder*

---

## 📚 References

*(Please add the specific literature references from your report here.)*

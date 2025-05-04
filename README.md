# Quantum-CNN-TicTacToe

---

**Authors:**
* Krishiv Trivedi [2023UMA0218]
* Piyush Kumar [2023UMA0227]
* Krishna [2023UEE0140]
* Jyoti Yadav [2023UEE0139]
* Meghanshu Verma [2021UEE0148](Meghanshuverma123456@gmail.com)
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

We also made another improvement in our residual QCNN, that is, diagonally entangling the qubits
to also capture the diagonal features of this dataset. You can see the full circuit in the GitHub repo, rest
all the components of the QCNN are compeletely the same. Now the results of just adding one layer of
Residual Blocks is as follows.

#### Improved-(QCNN):
* **Accuracy (without Residual Blocks):** 81.73%
* **Training Epochs (without Residual Blocks):** 300

*Figure 5: QCNN Loss Comparison*
| QCNN Loss (without Residual Blocks)                  | QCNN Visualization (with Residual Blocks)             |
| :-------------------------------------------------: | :---------------------------------------------------: |
| ![_Figure 5a_](/Report/assets/qcnn.jpeg)            | ![_Figure 5b_](/Report/assets/imp_qcnn.jpeg)             |
| *(a) QCNN Sqrd. Error Loss wo/Residual Blocks* | *(b) QCNN w/Residual Blocks (Visualization)* |

---

## ✅ Conclusion & Achievements

The baseline QCNN achieved a respectable accuracy (77%) in significantly fewer epochs (200) compared to the CCNN (which required ~100 epochs to reach similar levels, eventually peaking at 81.5% after 300 epochs).

Meanwhile, our Improved-Residual-QCNN challenges our current Classical CNN! This small improvement and adding residual-blocks is made a significant breakthrough!

 ![_Figure 6a_](/Report/assets/2.jpeg)                   
 ![_Figure 6c_](/Report/assets/1.jpeg)        
 ![_Figure 6b_](/Report/assets/confmat.jpeg)         

Q. **So, What improved**?

Ans. We hypothezised that it is mostly to do with the ``*Diagonal wins of a player*'', this is because, when we analyzed all the games that our quantum model got wrong, we see that it was only the games where the wins were diagonal.

That is, the model correctly predicted all horizontal and vertical wins correctly. In case of diagonal cases...

**Correct**: 32/56 **Incorrect**: 24/56

So we think the diagonalization due to the ``Residual-Blocks'' and convolution layers made it so that our new QCNN was good at identifying those extra features. Our new and improved model however, has only 19 incorrect diagonals.

---

## 📚 References

Wen, J., Huang, Z., Cai, D. et al. Enhancing the expressivity of quantum neural networks with residual connections. Commun Phys 7, 220 (2024). https://doi.org/10.1038/s42005-024-01719-1
https://pennylane.ai/qml/glossary/qcnn
https://docs.quantum.ibm.com/api/qiskit/0.27/qiskit.algorithms.optimizers.COBYLA
https://docs.quantum.ibm.com/api/qiskit/qiskit.circuit.library.ZFeatureMap

# Learning Quantum Phase Estimation by Variational Quantum Circuits 

<img src="/images/title_.png" width="900px" align="center">

## Team LearnQPE

Member : Chu-Hsuan Lin and Chris L

## Project description 
Presentation file can be found [here](LearnQPE_presentation.pdf).  

Quantum Phase Estimation (QPE) is one of the most important subroutines in quantum computing. The quantum circuit of QPE includes inverse Quantum Fourier Transform, but increasing the accuracy of the estimation will significantly increase the circuit depth. On NISQ hardware, the increased circuit depth will undermine the functionality of QPE and cause a noisy result, since the accumulated gate errors greatly influence the output measurement signal. In this project, we aim to construct the variational quantum circuit approximation corresponding to a given QPE circuit, where the circuit depth is reduced in the sense that it could outperform the original QPE circuit in noisy simulation and on real hardware.

In this repository, we provide the source code for implementing the idea of "Learning Quantum Phase Estimation by Variatinoal Quantum Circuits". In the jupyter notebook `LearnQPE.ipynb`, we demonstrate the workflow of training the VQC given a classical simulatable QPE circuit. In the QPE circuit we use it as an [example](https://qiskit.org/textbook/ch-algorithms/quantum-phase-estimation.html#3.2-The-Solution-), the circuit depth has reduced from 43 to 14.  

<img src="/images/method.png" width="800px" align="center">

To demonstrate the effectiveness of our method, we conducted the following setups of experiments:
1. Ideal QPE (QPE on ideal simulator)
2. Noisy QPE (QPE on noisy simulator)
3. QPE on real hardware
4. Ideal VQC (VQC on ideal simulator)
5. Noisy VQC (VQC on noisy simulator)
6. VQC on real hardware

<img src="/images/main_result.png" width="800px" align="center">
(You can click the figure for high resolution)  

The results showed that, compared to the measurement result of the `Ideal QPE`, which is the QPE run on an ideal simulator, the VQC on real hardware (ibm_oslo) outperformed both the `Noisy QPE` and QPE on real hardware. This is because the noise of the circuit was mitigated by reducing the circuit depth.  
When the execution of a quantum circuit is faster than its classical simulation and is still simulatable classically, the noise on the quantum computer can affect the measurement results. In such cases, our LearnQPE method can be useful. The LearnQPE method can be integrated into the quantum compiler as an intermediate step between the input circuit and the decomposed circuit that is fed into the quantum computer, while the circuit is classical simulatable. 

<img src="/images/helpful_case.png" width="800px" align="center">

It is worth noting that our method is not restricted to being combined solely with quantum phase estimation, but rather with any quantum algorithm that has an excessively deep circuit depth. In future work, our primary objective is to investigate which types of quantum algorithms could benefit from our method, and also to implement on various architectures of quantum computing hardware.

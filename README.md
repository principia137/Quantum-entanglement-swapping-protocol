# 2021_Quantum_Hackathon
    Topic : Entanglement Swapping Protocol
    Goal : implement 4 Qubits and 10 Qubits Entanglement Swapping Protocol on Qiskit
    Team : NetworQ
    Junsik Yu(ChungAng University),Leader
    KwangMin Kim(Soongsil University)
    JunYoung Kim(Hanyang University)

## 1. Abstraction
Quantum entanglement is an unintuitive phenomenon that takes place only in the quantum realm. Alice can transfer data to bob without any interaction. Consequently, alice and bob has the same bits. There are two possible state for Alice, one is 0-state and the other is 1-state. If Alice's bit is 0, then bob's bit also has the 0, vice versa.
We will introduce this protocol mathematically and implement using qiskit;python framework for quantum computer.
And experiment the measurement result in real machine - IBM, IonQ hardware.

## 2. Mathematical representation of quantum teleportation. 
Prepare four qubits q_0 ~ q_3
q_0 : Alice 
q_3 : Bob   
We must observe that q_0 and q_3 share the same bit. 

To make bell state, we apply the hardamard gate on q_0 and Cnot gate on q_0, q_1.We call that state as |e_1> 
(H *q_0) X (q_1) = 1/β2(|0> + |1>) X |0>
= 1/β2(|00> + |10>),
(X : tensor product)
|π_1>  = Cnot * {(H * q_0) X (q_1)} = 1/β2  (|00> + |11>)
Simillary apply on q_2, q_3.then,
|π_2>  = Cnot * {(H * q_2) X (q_3)}= 1/β2  (|00> + |11>)

So, there are two bell pair.
Represent the e_1 and e_2 using tensor product.
|π> = |π_1> β |π_2> =1/2(|0000> + |0011> + |1100> + |1111>)
|π> = |q_0 q_1 q_2 q_3> represent 4-quits system.

Connect the each bell pair by applying Cnot gate on q_1, q_2 and hardamard gate on q_1.
|π'> = |(πΌβπ» βπΌβπΌ)(πΌβπΆπππβπΌ)(|π>)
=  1/(2β2)(γ|00>γ_π΅πΆ (γ|00>γ_π΄π·+γ|11>γ_π΄π· )+γ|01>γ_π΅πΆ (γ|01>γ_π΄π·+γ|10>γ_π΄π· )+γ|10>γ_π΅πΆ (γ|00>γ_π΄π·βγ|11>γ_π΄π· )+γ|11>γ_π΅πΆ (γ|01>γ_π΄π·βγ|10>γ_π΄π·)

To achieve our purpose;alice and bob has the same bit. we do more operations on the circuit.
Consider |q_1 q_2>
if |00> then do nothing
if |01> then apply X gate
if |10> then apply Z gate
if |11> then apply X gate and Z gate
Then as a result, |π'> has only two possible that |0000> or |1001>.
It means that q_0(Alice) and q_4(Bob) shares the same bits. 
Finally we achieved our purpose. Alice and Bob have the same bit through this protocol.

## 3. Implement quantum circuit
![image](https://user-images.githubusercontent.com/62958764/124542387-458b9600-de5e-11eb-9659-3d30240706c8.png)
We can see successful simulation result. Alice and Bob have the same bits.
![image](https://user-images.githubusercontent.com/62958764/124542633-b2069500-de5e-11eb-8656-74ba9cf966ed.png)

## 4. Measurement result
Below is the real machine data. It conclude error due to noise. 
![image](https://user-images.githubusercontent.com/62958764/124543242-e2026800-de5f-11eb-9f38-3e798ee73fa6.png)

## 5. Additional research

Currently there are two available hardware in the market. 
1. IBM Quantum Computer uses superconductivity in temperature as low as 100K to 
enact quantum environment. 
2. IonQ Quantum Computer traps atoms in 3D space to produce naturally occurring 
quantum systems.
Our team was curious which hardware produced more accurate result in 
the case of Entanglement Swapping protocol. The result of error rate is as follows.
![image](https://user-images.githubusercontent.com/62958764/124543617-913f3f00-de60-11eb-8e2c-757db921afab.png)
![image](https://user-images.githubusercontent.com/62958764/124543781-d8c5cb00-de60-11eb-95a9-edb10a3678d3.png)



## 6. Conclusion
Our purpose in this paper was to devise a quantum teleportation protocol that could 
be applied in quantum networking. The reason this technology is noteworthy is because 
it does not lose its quantum property when relaying information. Although our research
results show relatively high error rates, this is due to the quantum hardware technology 
being young, and will no doubt improve in near future. It is our hope that with this 
research we have contributed to the possibility of quantum teleportation based 
networking, and that we shed a light to where it needs improvement.

## [Reference]

[1]"Quantum Teleportation."Β Qiskit Textbook. n.d. (2021.06.29), https://qiskit.org/textbook/ch-algorithms/teleportation.html.   
[2] M. Nielsen and I. Chuang, Quantum Computation and Quantum Information, Cambridge Series on Information and the Natural Sciences (Cambridge University Press, Cambridge, 2000).

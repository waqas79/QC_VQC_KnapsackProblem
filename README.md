# QC_VQC_KnapsackProblem
## VQC Optimizer for Knapsack Problem
This project is about implementing a quantum machine learning model using a VQC to estimate the optimum solution of Knapsack Problem (KP). KP is the problem of selecting some of the items in a given set to insert into a knapsack with a limited capacity (total weight). For each item, a weight and a value are given. The aim is to maximize the total value of the inserted items without exceeding the capacity. Possible solutions of a KP are selection of all the items created by assigning either 0 (non-selected) or 1 (selected) to each item.

The purpose of the developed VQC is to create selections to a given KP. The parameters of the VQC will be altered in a way that the total value of the selected items will be increased without exceeding the capacity. If a resulting selection exceeds the capacity, it will be given 0 reward (or maximum loss). You are free to use different circuits with different entanglement schemes and parameterized gates. However, the encoding and the decoding of the circuit are given by the supervisor as well as the number of qubits and you are expected to apply these to your VQCs.

### Data

The example problems for training and testing and the python code to calculate the values will be provided by the supervisor. The size of the problems will be 8 items. Therefore, your VQCs are supposed to have a qubit count of 8.

### Encoding
A KP is defined by the weights and values of the items, which are to be encoded to the VQC. To do this angle encoding with two different rotation gates can be utilized. For instance, the weights can be encoded by RX gates and values by RZ gates. With this encoding method, a KP is encoded by 2 rotation gates for each qubit.

### Decoding

Since the desired output from the VQC is a selection, there is no need to do additional operations after qubits are measured. If a qubit is measured as 1 (0), it means that the related item is (not) selected. With this decoding method, the outcome of the VQC can be obtained using only one shot of the circuit.
Implementation

The implementation of the VQC will be done using Qiskit. It will be trained using PyTorch. You are free to choose the optimizer you like, or to try a few optimizers to find the most effective one.

Supervisor: Umut Çalıkyılmaz

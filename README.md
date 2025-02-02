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

## Knapsack Problem Supplement

Knapsack problem is the problem of selecting some of the given items to put in a
knapsack. Each item has a given weight and price. The knapsack has a weight capacity
and the objective is to maximize the total price of items in it without exceeding the
capacity. Finding the optimal selection is NP-Hard.
To train VQCs, 20000 problem instances with their optimal solutions are provided. Each
line in the text file gives the data for a problem instance. Each problem represents a
knapsack problem with 8 items and the weight limit of each problem is set as 2000 for
ease.
In the given data, each problem instance is represented by two arrays. The capacity
values for the instances are not given in the file. The reason is that capacity value is the
same for each problem, so you do not need to encode this value. The first array holds
the weights of the items. Each weight value is an integer and they are separated by
commas. As an example, the length array for the first problem instance is given below.


[100,641,972,563,336,180,624,633]


The prices of the items are given in the same format. The price array for the first
problem instance is given below as an example.


[353,1805,541,916,1539,1209,1658,1121]


The last array in each line shows the optimal solution for the problem instance. In this
array, 1(0) means the item is (not) selected to be inserted in the knapsack. For instance
if the first number in this array is 1, it means that the first item is put into the knapsack.
The solution array for the first problem instance is given below as an example.


[1,1,0,0,1,1,1,0]


You are expected to train your models using the given labeled data, where a weight
array and a price array contains the initial values to be encoded in your quantum circuit,
and the solution array is the label of the data. Therefore, supervised learning methods
are to be used in your applications. You can try out different optimizers to train your
circuits.
As explained on the project description, both the encoding and the decoding of the data
will be done using angle encoding. The weights are created from a uniform distribution
with the lower bound of 100 and upper bound of 1000, and the prices are created from a
uniform distribution with the lower bound of 200 and upper bound of 2000. Normalize
your rotation angles in the encoding layer accordingly. Since there are two values to be
encoded for each qubit, you should use different rotation gates to encode them. I would
suggest you to use a Ry gate to encode a weight value and then to use an Rz gate to
encode a price value.
The output for each item is either 0 or 1. Therefore, the result from the circuit can be
obtained by only running the circuit once. For instance, if you measure |0⟩ from the first
qubit, it means that the first item is not selected, and if you measure |1⟩ from the first
qubit, it means that the first item is selected.

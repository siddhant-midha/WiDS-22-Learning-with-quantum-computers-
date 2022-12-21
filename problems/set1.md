# Problem Set 1
This problem set is to help you practice some of the fundamental ideas in Quantum Computing and introduce you to two popular libraries you will be using for the remaining project. Before starting, we need to install *Qiskit* and *Pennylane*. Qiskit is an SDK by IBM, while Pennylane is a software library by Xanadu AI.

## Installation
If this is your first time working with Python, we recommend using Miniconda/Anaconda to manage virtual environments. Please refer to the following links:
1. [Qiskit](https://qiskit.org/documentation/getting_started.html)
2. [Pennylane](https://pennylane.ai/install.html)

## Deutsch-Jozsa Algorithm
[The Deutsch-Jozsa Algorithm](https://qiskit.org/textbook/ch-algorithms/deutsch-jozsa.html) was the first algorithm to demonstrate the power of quantum computers.

### Problem
We are given a Boolean function, $f: \{0, 1\}^{n} \to \{0, 1\}$. Although we do not know $f$, it is known that the function is either constant or balanced. The task is to determine whether $f$ is constant or balanced.

#### Part 1
Try to come up with a classical **deterministic** algorithm that solves the Deutsch-Jozsa Problem. What is its query complexity? (query complexity is the number of inputs on which you have to evaluate the function to check the desired property)

#### Part 2
Can you come up with a quantum circuit that does the same thing in a single evaluation? Since $f$ might be irreversible, it must be implemented as a quantum *oracle* $U_{f}$,

$$ U_{f}|x\rangle |y\rangle = |x\rangle |y \oplus f(x)\rangle $$

$U_{f}$ is a reversible quantum operation that can be implemented in the form of a unitary. For the purposes of this task, we would like you to choose your own Boolean function, implement it as an oracle and use it in your circuit. To keep things simple, only look at functions over bit strings of length $2$.

Note: An evaluation can be thought of as a query to the oracle.

#### Part 3
Now, we would like you to try to come up with a classical **randomised** algorithm that solves the Deutsch-Jozsa Problem. The randomised algorithm will not succeed with 100% probability but in general, will require fewer queries to check the property (constant or balanced) *with certain probability*.

## Deutsch-Jozsa with a Twist
(This problem has been taken from [QHack 2022](https://github.com/XanaduAI/QHack))
In this problem, we are not just given a single Boolean function, but rather $4$ Boolean functions $f_{i}, i \in \{0, 1, 2, 3\}$. Just like in the Deutsch-Jozsa 
Problem, each $f_{i}$ is either constant or balanced but we have also been told the following,

1. All the functions are constant.
2. All the functions are balanced.
3. Two of the functions are constant and the other two are balanced. 

Can you construct a quantum circuit to determine whether all the four functions are of the same type (all constant or all balanced) or equally split (two constant and two balanced)? Try to implement the solution using not more than $8$ qubits (although you should be able to do the problem using only $5$). You can find more information on the task [here](https://github.com/XanaduAI/QHack/tree/master/Coding_Challenges/algorithms_500_DeutschJozsaStrikesAgain_template), a template to write your code along with $2$ testcases to check your solution. 

## Disclaimer
We have added a link to the Qiskit tutorial on Deutsch-Jozsa in the first task but this is **only** for your reference. You can refer to the solution given, but please DO NOT COPY! Since the second task is taken from a completed contest, you will find solutions to the task on the web. Only refer to these **after** you have thought of an approach yourself. Of course, you are free to refer to the [Pennylane documentation](https://docs.pennylane.ai/en/stable/).
# QHACK 2023



<p align="left">
  
</p>


# QUANTUM NATURAL LANGUAGE GENERATION

## TEAM : QHAQER


 



<p align="left">
  
</p>


# QUANTUM-CLASSICAL TIC-TAC-TOE

## TEAM : QHAQER


For the **QHACK 2023 OPEN CHALLENGE** I implemented the paper **Quantum Natural Language Generation on Near-Term Devices**, published on   1st November 2022 and be found via link: 
## - [Link To The Paper](https://arxiv.org/pdf/2211.00727.pdf)


## - [Implementation Notebook](https://github.com/Alfaxad/Quantum_Natural_Language_Generation/blob/main/Notebooks/Quantum_Natural_Language_Understanding_Main_Notebook.ipynb)


## ABSTRACT

The emergence of noisy medium-scale quantum devices has led to proof-of-concept applications for quantum computing in various domains. Examples include Natural Language
Processing (NLP) where sentence classification experiments have been carried out, as well
as procedural generation, where tasks such as
geopolitical map creation, and image manipulation have been performed. We explore applications at the intersection of these two areas
by designing a hybrid quantum-classical algorithm for sentence generation.
Our algorithm is based on the well-known simulated annealing technique for combinatorial
optimisation. An implementation is provided
and used to demonstrate successful sentence
generation on both simulated and real quantum
hardware. A variant of the algorithm can also
be used for music generation.
ThE paper also aimed to be self-contained, introducing all the necessary background on NLP and
quantum computing along the way




## Some  Background on QNLP
The current state of QNLP has by large extent been developed on **Diagramatic Quantum Theory**, Diagrammatic Quantum Theory (DQT) is a mathematical framework for understanding and calculating quantum systems using diagrams as a visual representation

One of the key advantages of DQT is that it provides a way to simplify complex quantum staes, especially sequential ones such as language. Specifically, String diagrams provides a way to express nonseparable and separable processes in a diagrammatic fashion as seen in the diagram below.

![Screenshot (253)](https://user-images.githubusercontent.com/68440833/221954392-cb494e25-c732-47c3-bb2f-dabd2578a7e5.png)


**Hill-climbing algorithm**
```python 
    import random

def hill_climbing(start_state, goal_state, get_neighbors_fn, heuristic_fn):
    current_state = start_state
    while current_state != goal_state:
        neighbors = get_neighbors_fn(current_state)
        neighbor_states = [(neighbor, heuristic_fn(neighbor)) for neighbor in neighbors]
        best_neighbor, best_neighbor_score = min(neighbor_states, key=lambda x: x[1])
        if best_neighbor_score < heuristic_fn(current_state):
            current_state = best_neighbor
        else:
            break
    return current_state

# Example usage:
# Define the start and goal states
start_state = [0, 0]
goal_state = [10, 10]

# Define the function that generates neighboring states
def get_neighbors(state):
    x, y = state
    neighbors = []
    for dx, dy in [(1, 0), (-1, 0), (0, 1), (0, -1)]:
        neighbor = [x + dx, y + dy]
        if 0 <= neighbor[0] <= 10 and 0 <= neighbor[1] <= 10:
            neighbors.append(neighbor)
    return neighbors

# Define the heuristic function
def heuristic(state):
    x, y = state
    return abs(x - goal_state[0]) + abs(y - goal_state[1])

# Run the hill-climbing algorithm
solution = hill_climbing(start_state, goal_state, get_neighbors, heuristic)
print("Found solution:", solution)

```













![Screenshot (254)](https://user-images.githubusercontent.com/68440833/221955560-86420fcb-ec90-49ab-84ff-1d6da9ad5ecb.png)


### 2.2 DisCoCat and QNLP
The Distributional Compositional Categorical (DisCoCat) model of language meaning (Coecke et al.,
2010) is a mathematical framework that allows for
the meaning of a sentence to be described as a combination of the meaning of its constituent words,
and the grammatical relationships between these
words. This is in contrast to many older NLP models, which treat sentences as “bags of words” while
ignoring their grammatical structure.
DisCoCat comes equipped with a pictorial representation, allowing any sentence to be represented
by a so-called string diagram. Such a diagram
consists of boxes representing words, and wires
connecting these boxes according to the formalism of pregroup grammars (Lambek, 2008). This
means that every wire in the diagram is annotated
either by some atomic type p, a left adjoint p.l, or
a right adjoint p.r. Let us explain the role of types
and adjoints through example, by considering the
sentence “Alice generates language“. The DisCoCat diagram corresponding to this sentence is given
in figure below:
![Screenshot (255)](https://user-images.githubusercontent.com/68440833/221956980-e20a3baf-0438-45d0-8241-a1af2afabec1.png)

It is worth noting that DisCoCat diagrams are
more than simple pictures. They are based on the
rigorous formalism of monoidal categories (Heunen and Vicary, 2019, Chapter 1), which means
they are equipped with a diagrammatic calculus.
This calculus can be used to rewrite complicated string diagrams into simpler ones that still encode
the meaning of the original sentence.




## General Steps of the algorithm Using Lambeq Framework



1. A sentence is converted to a DisCoCat diagram using the Combinatory Categorical
Grammar (CCG) based techniques of Yeung
and Kartsaklis (2021).

2. The DisCoCat diagram is simplified using
some of the rewrite rules available in lambeq. Even though this step is strictly speaking
optional, applying rewrite rules often leads to
crucial computational advantages, for instance
by reducing the number of qubits required to
implement the parameterised quantum circuit.

3. An ansatz is used to transform the simplified
diagram to a parameterised quantum circuit.
This ansatz is a mapping that assigns a number of qubits to each wire type in the string
diagram, as well as a set of quantum logic
gates to each word in the diagram.

4. The quantum compiler t|keti (Sivarajah et al.,
2020) is used to translate the parameterised quantum circuit into machine-specific instructions, which can be executed on real IBM quantum computers or simulators



### The algorithm for natural language generation was **Simulated Quantum Annealing** which is an optimization algorithm built on top of **Hill-Climbing Algorithm**

### Hill Climbing Algorithm
The Hill Climbing algorithm is a type of heuristic search algorithm used in artificial intelligence and optimization problems. It is a local search algorithm that tries to find the best solution by iteratively improving the current solution.

The basic idea of the Hill Climbing algorithm is to start with an initial solution and then to repeatedly modify it by making small changes and selecting the best one at each iteration. The algorithm terminates when it reaches a local maximum, meaning that no further improvement is possible.

**visualization of the algorithm**


https://user-images.githubusercontent.com/68440833/221959527-5e97585a-7c89-4787-a9fc-f78eab8f38e2.mp4








https://user-images.githubusercontent.com/68440833/221959889-6fb3e23c-39a6-455d-9679-4b6d6e8335cf.mp4








































## QHAQER TEAM





<tr>
    <td align="center"><a href="https://github.com/Alfaxad"><img src="https://github.com/Alfaxad.png" width="100px;" alt=""/><br /><sub><b>Alfaxad</b></sub></a><br /><a href="" title="Code">💻</a></td>
</tr>











g
[










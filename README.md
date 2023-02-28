# QHACK 2023



<p align="left">
  
</p>


# QUANTUM NATURAL LANGUAGE  GENERATION & SENTENCE GENERATION

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



**Hill-climbing algorithm**
```python import random

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



### Simulated Annealing Algorithm
is a probabilistic technique for approximating the global optimum of a given function. Specifically, it is a metaheuristic to approximate global optimization in a large search space for an optimization problem. It is often used when the search space is discrete (for example the traveling salesman problem, the boolean satisfiability problem, protein structure prediction, and job-shop scheduling). For problems where finding an approximate global optimum is more important than finding a precise local optimum in a fixed amount of time, simulated annealing may be preferable to exact algorithms such as gradient descent or branch and bound.

The name of the algorithm comes from annealing in metallurgy, a technique involving heating and controlled cooling of a material to alter its physical properties. Both are attributes of the material that depend on their thermodynamic free energy. Heating and cooling the material affects both the temperature and the thermodynamic free energy or Gibbs energy. Simulated annealing can be used for very hard computational optimization problems where exact algorithms fail; even though it usually achieves an approximate solution to the global minimum, it could be enough for many practical problems.






**Simulated annealing visualization**
https://user-images.githubusercontent.com/68440833/221959889-6fb3e23c-39a6-455d-9679-4b6d6e8335cf.mp4


**Simulated Annealing implementation**
```python
import math
import random

def simulated_annealing(initial_solution, objective_function, T0, Tf, cooling_rate):
    current_solution = initial_solution
    current_energy = objective_function(current_solution)
    T = T0
    while T > Tf:
        # Generate a new candidate solution
        candidate_solution = generate_neighbor(current_solution)
        # Evaluate the candidate solution
        candidate_energy = objective_function(candidate_solution)
        # Calculate the energy difference
        delta_E = candidate_energy - current_energy
        # If the candidate solution is better, accept it
        if delta_E < 0:
            current_solution = candidate_solution
            current_energy = candidate_energy
        # If the candidate solution is worse, accept it with a certain probability
        else:
            acceptance_probability = math.exp(-delta_E / T)
            if random.random() < acceptance_probability:
                current_solution = candidate_solution
                current_energy = candidate_energy
        # Decrease the temperature
        T *= cooling_rate
    return current_solution, current_energy

def generate_neighbor(solution):
    # Generate a random neighbor by making small changes to the solution
    # For example, swap two randomly selected elements in a list
    neighbor = list(solution)
    i, j = random.sample(range(len(solution)), 2)
    neighbor[i], neighbor[j] = neighbor[j], neighbor[i]
    return neighbor

# Example usage: solve the traveling salesman problem
# Define the objective function as the total distance traveled
def objective_function(solution):
    # Assume that the solution is a list of city indices
    total_distance = 0
    for i in range(len(solution)):
        j = (i + 1) % len(solution)
        distance = get_distance(solution[i], solution[j])
        total_distance += distance
    return total_distance

# Define the initial solution as a random permutation of city indices
cities = [0, 1, 2, 3, 4]
initial_solution = random.sample(cities, len(cities))

# Set the initial and final temperatures, and the cooling rate
T0 = 100
Tf = 1
cooling_rate = 0.99

# Run the Simulated Annealing algorithm
solution, energy = simulated_annealing(initial_solution, objective_function, T0, Tf, cooling_rate)

print("Final solution:", solution)
print("Final energy:", energy)

```



## CONCLUSION & FUTURE PROJECTIONS.

In this open-hackathon Project I have successfully implemented a Quantum Machine Learning Model that can classify and generate sentences  and be able to classify sentences according to the paper **Quantum Natural Language Generation on Near-Term Devices(https://arxiv.org/pdf/2211.00727.pdf)**

- My main motivation came from the sudden popularity and convenience of Large Language Models that has led to impressive Generative AI such as Open AI's ChatGPT Dall-E, and Google's Imagen. As an inspiration I wanted to implented a Quantum Text2Image model, however the computational complexity, current state of Quantum computers and the duration of the hackathon did not give room for this.

- I am glad I got to implement this instead, but **I am even more optimistic of the future of Quantum computing**. My next goal is implementing a Text2Image model that can run on a Quantum Computer and I cannot wait to see the unfolding potential of AI and Quantum Computing. **What A Time To Be Alive**

**Thank you QHack Organizers :), this was a an amazing event**



## REFERENCES

1. Quantum Natural Language Generation on Near-Term Devices: https://arxiv.org/pdf/2211.00727.pdf
2.Bob Coecke, “Foundations for Near Term Quantum Natural
Language Processing”, https://arxiv.org/abs/2012.03755
3. Stephen Clark, “Something Old, Something New: Grammarbased CCG Parsing with Transformer Models”,
https://arxiv.org/abs/2109.10044
4.Imagen unprecedented photorealism × deep level of language understanding: https://imagen.research.google/
5. Introducing ChatGPT : https://openai.com/blog/chatgpt
6. An Introduction to Quantum Natural Language Processing by Srinjoy Ganguly :https://www.udemy.com/course/quantum-natural-language-processing-beginners/
7. lambeq : https://cqcl.github.io/lambeq/
8. https://medium.com/cambridge-quantum-computing/quantum-natural-language-processing-ii-6b6a44b319b2







































## QHAQER TEAM





<tr>
    <td align="center"><a href="https://github.com/Alfaxad"><img src="https://github.com/Alfaxad.png" width="100px;" alt=""/><br /><sub><b>Alfaxad</b></sub></a><br /><a href="" title="Code">💻</a></td>
</tr>






















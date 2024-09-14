---
layout: default
---

# Query Algorithm
Nowadays, many researches has put their attention on quantum computing. In this document, query model, a simple but fundamental model is introduced as the start of quantum query algorithms.

## The query model of computation (Quantum Algorithm Explanation)
Query model could be considered as the base of quantum computing developing. To summarize, it is an computation model, which has different input pattern from the classical computing systems. In this section, we first introduce the difference between query model and classic computation model.

### Difference between conventional computation model and query model
The key insight is that the inputs of query model and computation model are different.

The processing to solve a problem in classical computing consist of input, function unit and output. This system has an input and an output. The input is fully exposed to the computation unit and than the output is streamed out. In this process, for instance, if the input is a 8 bit 0,1 sequence (01110101), this whole sequence will be streamed into the computation block.

However, the query model does not access the whole input but only a function of the input. The function which represent the input could be determined as the following format:
$$f:\Sigma^n -> \Sigma^m$$
$\Sigma$ here represents binary alphabet, which could be write as $\Sigma={0,1}$. 
I could provide an example. Considering the form $f: \Sigma^n->\Sigma (m=1)$ If we let $f$ be the repesent of a sequence of $2^3$ bits to which we have , which means $n=3$. Then, we could get $\Sigma^n$ as $000,001,010...111$. Assume $f$ is some logic function, we may could have $f(000)=0, f(001)=1...$ The processor could not access $000,001...$, but only access $f(000)=0$, $f(001)=1$. If we make one time access to $f$, that is to say, we do $f(xxx)=x$ for one time, we are considered to do one query. The access operation to the $f$ is query.

### How we define the query complexity
Before the explaination of the query gates, we have to clarify the calculation method of query complexity. To simplify the problem, we only care about the high level performance of the algorithm. Hence the query complexity is simply defined as the number of queries and the operation overhead is omitted.

## Query gates
### Classical query gates
Queries could be made by query gates. This gate has $n$ input and $m$ output (n,m in $f:\Sigma^n -> \Sigma^m$). For this circuit, once the $f$ function is accessed, one query is done. Hence, we could simply consider the number of queries as the query gates appear in the circuit.

### Quantum Query gates
Though the previous format works in classical Boolean circuit. It does not make mense for quantum circuits, because the gates with simply n input and m output may lead to non-unitary gates. The solution of this problem is to define $U_f$ for which represent unitary query gates. In this gate, we stream in two arbitrary strings. One is $x\in \Sigma^n$, this will bypass and output $x$. The other one is $y\in \Sigma^m$ and this will output $y\oplus f(x)$ where $\oplus$ means exclusive OR of strings. This could ensure the $f$ function is unitary.

### Quantum Query model speedup
For the previous described classic query models the number of queries needed typically scales linearly or polynomially with the size of the input, depending on the problem. For example, searching an unsorted list of $N$ items classically requires $O(N)$ queries.
However, Quantum query algorithms often achieve a lower query complexity due to parallel processing of multiple states. For example, Grover’s algorithm can search an unsorted list of $N$ items in $O(N)$ queries, demonstrating a quadratic speedup.

## What context do we need quantum computing (Critical Evaluation of Algorithm Performance)
Whether quantum computing could achieve better permformance compare with the classic counterport actually depends on specific problems. For most classical computing problems, sunch as matrix multiplication, conventional computing systems could achieve higher performance. First, classical memory access and classical computing units are time efficient, energy efficient and scalable thanks to high memory indensity and high parallelism. Second, conventional counterports have less circuit level non-idealities compared with quantum query algorithm because of mutual fabrication techniques and stable electrical properties.

However, quantum computing is fast in several specific complex problem solving. For instance, it could decrease Shor's algorithm time complexity. Though has less scalability and stablity, it could achieve high speedup in those complex problems due to the properties of quantum circuits. Hence, the most significant advantage we care about in quantum computing is time, which means, quantum computing sacrifice other properties for speedup.

Though existing quantum query algorithms are well-studied, there are many opportunities from my view of research. (I am not familiar with quentum algorithms and could only provide information on a high level). Frist, hardware aware algorithm design could be further studied to increase the system robustness. For instance, in my research, I modify some algorithm to limit the output data distribution in a specific range which could avoid saturation noise. Second, due to the complexity of quantum devices, algorithm level simplify is needed. Implementing high-precision data, for instance FP16, in unconventional systems is expensive. It is nesserary to think about decrease the required data precision of the algorithms.

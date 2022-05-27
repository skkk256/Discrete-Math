## Chapter 1 What's a Graph?

### 1.1 Definition

- a graph is expressed as 

$$
G = (V, E)
$$


​	$V$ means **vertices ( vertex )**, such as $\{ a_{1},a_{2},a_{3}...\} $

​	$E$ means **edges**, such as $\{\{a_{1}, a_{2}\},\{a_{2},a_{3}\}\}$ for undirected edges, or $\{ (a_{1},a_{2}),(a_{3},a_{4}) \}$ 	for directed edges.

- $|V|$ is called the **order** of $G$

- if $|V| = \infty $ or $|E| = \infty $, the graph is an **Infinite Graph**

  if $|V| < \infty $ or $|E| < \infty $, the graph is a **Finite Graph**

- example

![image-20220527113312077](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527113312077.png)

### 1.2 Type of Graph

- special components in the graph

  - **Loop & multiple edges**

  - **Weighted edge**

    each edge in the graph is assigned with a positive number

  - **Directed edge**

- table

| Type                  | Edges                 | Multiple Edges Allowed? | Loops Allowed? |
| --------------------- | --------------------- | ----------------------- | -------------- |
| Simple graph          | undirected            | No                      | No             |
| Multigraph            | undirected            | Yes                     | No             |
| Pseudograph           | undirected            | Yes                     | Yes            |
| Simple directed graph | directed              | No                      | No             |
| Directed multigraph   | directed              | Yes                     | No             |
| Mixed graph           | undirected + directed | Yes                     | Yes            |

### 1.3 Special Simple Graph

- **Complete Graph** ( $K_{n}$ )

$$
V=\{ v_{1},...,v_{n} \}\\
E=\{ \{ v_{i}, v_{j} \}:1 \leq i \neq j \leq n \}
$$

![image-20220527121435636](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527121435636.png)

- **Cycle** ( $C_{n}$ )

$$
V=\{ v_{1},v_{2},...,v_{n} \}\\
E=\{ \{ v_{1}, v_{2} \} \{ v_{2}, v_{3} \} ,..., \{ v_{n}, v_{1} \} \}
$$

![image-20220527121736921](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527121736921.png)

- **Wheel** ( $W_{n}$ )

$$
V=\{ v_{0},v_{1},v_{2},...,v_{n} \}\\

E=\{ \{ v_{1}, v_{2} \} \{ v_{2}, v_{3} \} ,..., \{ v_{n}, v_{1} \} \} \cup \{ \{ v_{0}, v_{1} \} \{ v_{0}, v_{2} \} ,..., \{ v_{0}, v_{m} \} \}
$$

![image-20220527122343458](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527122343458.png)

- **$n-$Cubes** ( $Q_{n}$)

$$
V=\{ 0 , 1\}^{n}\\
E=\{ \{ u,v \}: d(u,v) = 1\}\quad 坐标中不相等的方向个数为1\\
d(u,i) = |i\in [n]:u_{i} \neq v_{i}|
$$

![image-20220527123619633](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527123619633.png)

## Chapter 2 How to descripe a graph?

### 2.1 Expression of the Graph

- **Adjacency list**

  The adjacency list of $G$ is a list of the vertices of the graph and all adjacent vertices

![image-20220527125323378](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527125323378.png)

- **Adjacency Matrix**

$$
a_{ij} = multiplication\ of\ \{ v_{i},v_{j} \}\\
a_{ii} = 1\ if \ \exists \ a \ loop;a_{ii}=0,otherwise
$$

  ![image-20220527125423596](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527125423596.png)

1. if $a_{ii} \neq 0$, it means there exists a loop
2. The $(𝑖,𝑗)$ entry counts the multiplicity of $\{v_{i}, v_{j}\}$, $i ≠ j$
3. The adjacency matrix of a simple graph is always symmetric

- **Incidence Matrix**

  if $v_{i}$ and $v_{j}$ are two sides of $e_{k}$, then $a_{ki}$ and $a_{kj}$ are 1, and 0 otherwise.

![image-20220527222638100](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527222638100.png)

### 2.2 Degree

#### 2.2.1 for <u>undirected</u> graph

- If $u,v\in V$ and $\{u,v\}\in E$, we say that vertices $u,v$ are **adjacent** ( or **neighors** )

- **neighborhood** if $v$ in $G$:  $N(v) = \{ u\in V:\{ u,v \} \in E \}$

  - $N(A) = \cup_{v\in A} N(v)$ for $A ⊆ V$

- $deg(v)$ is the number of edges incident with $v$

  - every loop contribute to 2 to $deg(v)$

- $v$ is **isolated** if $deg(v)=0$; $v$ is **pendant** if $deg(v)=1$

  ![image-20220527224749426](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527224749426.png)

#### 2.2.2 for the <u>directed</u> graph

- If $(u,v)\in E$, we say that $u$ is **adjacent to** $v$ and $v$ is **adjacent from** $u$, $u$ is the **initial vertex**, $v$ is the **terminal vertex**. ( when $u=v$, it's a loop )

- **in-degree** $deg^{-}(v)$: the number of edges where $v$ is the terminal vertex

- **out-degree** $deg^{+}(v)$: the number of edges where $v$ is the initial vertex

  - a loop contributes 1 to $deg^{+}(v)$ and $deg^{-}(v)$

  ![image-20220527225750947](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527225750947.png)

### 2.3 Handshaking Theorem

1. for the <u>undirected</u> graph

$$
2|E|=\Sigma_{v\in V}deg(v)\\
and \quad|\{ v\in V:deg(v)\ is\ odd \}|\quad is\ even
$$

   ![image-20220527232122604](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527232122604.png)

2. for the <u>directed</u> graph

$$
|E|=\Sigma_{v\in V}deg^{+}(v) = \Sigma_{v\in V}deg^{-}(v)\\
$$

![image-20220527232241167](https://github.com/skkk256/Discrete-Math/raw/main/images/image-20220527232241167.png)

## Chapter 3 Some operations on the graph

### 3.1 Subgraph


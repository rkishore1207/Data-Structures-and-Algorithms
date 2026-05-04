# Graphs

- Types of Graphs are **Undirected and Directed Graphs**.
- Each graphs having **Nodes (vertex) and Edges**.
- Edges are presenting in Directed and Undirected types.
- Cyclic Graphs and Acyclic Graphs.

![Graphs](https://github.com/user-attachments/assets/55abdeb8-01f4-4f76-a563-570792619cad)

### Path

- A node should not appear more than once in a Path.
- There should be present a Edge between two nodes in a path.

### Degree

- Undirected Graphs - A degree is the number of Edges that are incoming and outgoing to the particular Node.

`Property` - The Degree of the Graph is equal to the Twice of the Edges.

- Directed Graphs - **Indegree and Outdegree**

![Degree in a Graph](https://github.com/user-attachments/assets/f2c168e6-e109-4143-add6-055265d6940d)

### Edge weight

- Each Edge in a Graph should have some weights, if there is no weights, then we can take it as `1`.

### Graph Representation

- Matrix (Adjacency Matrix)
- List

> If n(node) is 5, then Matrix size will be adj[n+1][n+1]

### Connected Components

- There may be a multiple Graph components which are not connected with each other.
  ![Connected Components](https://github.com/user-attachments/assets/9156324a-543c-43f4-a485-cc7b3f619338)

- For Traversal, we have to use Visited Array concepts.
- Array's length - Node length + 1, initially all are marked as Zero.
- Traversing the array, if it is zero, then traverse the entire connected Nodes and mark them as One.

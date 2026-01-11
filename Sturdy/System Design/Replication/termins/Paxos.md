

- **Description**: A foundational algorithm for achieving consensus in a network of unreliable nodes.
- **How It Works**:
    - Nodes act as proposers, acceptors, or learners.
    - A proposer suggests a value.
    - Acceptors agree on a single value through a series of message exchanges (prepare and accept phases).
    - Learners are informed of the chosen value.
- **Strengths**:
    - Highly fault-tolerant.
- **Weaknesses**:
    - Complex to implement and understand, with high communication overhead.
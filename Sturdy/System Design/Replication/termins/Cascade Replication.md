
- **Description**: Replicas are organized hierarchically, with updates flowing from the master to intermediate replicas and then to leaf replicas.
- **Characteristics**:
    - Reduces replication load on the master by distributing it.
    - Can create a replication tree or chain.
- **Use Case**: Large-scale systems where a single master cannot handle direct replication to all replicas.
- **Challenges**:
    - Increases replication lag at lower levels of the hierarchy.
    - Complexity in managing the hierarchy.
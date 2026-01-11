
- **Description**: The master waits for acknowledgment from replicas before committing transactions.
- **Characteristics**:
    - Guarantees data consistency across replicas.
    - Slower due to network delays.
- **Use Case**: Systems where strong consistency is critical, such as financial applications.
- **Challenges**:
    - Reduced performance and increased latency.
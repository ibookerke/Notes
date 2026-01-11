
- **Description**: A single master handles writes, and multiple replicas are dedicated to read operations.
- **Characteristics**:
    - Read replicas reduce the load on the master for read-heavy workloads.
    - Write operations go only to the master.
- **Use Case**: Scenarios with high read-to-write ratios, like analytics dashboards.
- **Challenges**:
    - Data consistency lags due to replication delays.
    - Write operations cannot be distributed.
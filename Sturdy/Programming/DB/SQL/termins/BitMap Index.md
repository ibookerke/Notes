A **bitmap index** is ideal for columns with **low cardinality** (few unique values, such as `gender`, `status`, or `yes/no`). It represents data using binary bits instead of traditional B-trees, making it efficient for certain types of queries.

- **How It Works**:
    1. Each unique value in the column is assigned a bit.
    2. For every row, the bit corresponding to its value is set to `1`, while others are `0`.
    3. Queries combine these bitmaps to quickly identify matching rows.
- **Use Case**:
    - Analytical queries involving multiple conditions (e.g., filters on gender, region, or status).
    - Works best in data warehouses or read-heavy systems.
- **Example**: For a `status` column with values `active`, `inactive`, and `pending`:
    - Bitmap for `active`: `100101`
    - Bitmap for `inactive`: `011010`
    - Bitmap for `pending`: `000100`
    
    A query like `WHERE status = 'active' AND region = 'north'` combines the bitmaps efficiently to find matches.
    

#### **Limitations of Bitmap Indexes**:

- Not ideal for high-cardinality columns (e.g., unique IDs).
- Bitmap indexes can become large and less efficient in write-heavy environments.
# Hash table
> https://www.geeksforgeeks.org/hashing-set-1-introduction/
## Hash functions
**Table size should better be a prime number**
- Division: Slot_id = Key % table_size
- Combination:  
  ```
  hash function (h1) on key to obtain mid_key  
  hash function (h2) on mid_key to obtain Slot_id
  ```
- Others(eg): Slot_id = (Key^2 + Key + 41) % table_size
## Collision
- Separate Chaining  
  **Linked list in slot**
- Open Addressing
  - Linear Probing ((hash(key) + n) % table_size)
  - Quadratic Probing ((hash(key) + n * n) % table_size)
  - Double Hashing ((hash1(key) + n * hash2(key)) % table_size)  
    **hash2(key) = PRIME – (key % PRIME)**  
    **PRIME is a prime that smaller than table_size**
    
| Type | Separate Chaining | Open Addressing |
| :---: | --- | --- |
| Implementation | Simpler to implement | Require more computation |
| Usage | Unknown how many and how frequently keys may be inserted or deleted | Frequency and number of keys is known |
| Performance | Not good (linked list) | Better cache performance (stored in same table) |
| Memory | Waste of Space (Some slot never use) & Use extra space (linked list) | / |
## Rehashing
**Load factor = occupied/total slots**  
**Rehash all the elements into a double-size table (current load factor > pre-defined value (0.75 default))**

# Tree


# Q4 – Comparison of HashMap, TreeMap and LinkedHashMap

## 1. Objective

To compare HashMap, TreeMap and LinkedHashMap based on insertion, searching, lookup and iteration performance for different inventory sizes.

## 2. Experimental Setup

The experiment uses three inventory sizes:

- Small inventory: 1,000 items
- Medium inventory: 10,000 items
- Large inventory: 50,000 items

Each implementation performs 100,000 lookup operations per repetition. The experiment is repeated three times, and average execution time is reported.

## 3. Implementation Details

### HashMap

HashMap stores key-value pairs using hashing. It provides average O(1) insertion and lookup performance. However, it does not guarantee any particular iteration order.

### TreeMap

TreeMap stores entries in sorted key order using a Red-Black Tree. Insertion and lookup operations take O(log n) time.

### LinkedHashMap

LinkedHashMap maintains insertion order using a linked list along with hash table functionality. It provides average O(1) insertion and lookup performance while preserving insertion order.

## 4. Time Complexity Comparison

| Operation | HashMap | TreeMap | LinkedHashMap |
|---|---|---|---|
| Insertion | O(1) average | O(log n) | O(1) average |
| Lookup | O(1) average | O(log n) | O(1) average |
| Iteration | O(n) | O(n) | O(n) |
| Ordering | No guarantee | Sorted order | Insertion order |

## 5. Experimental Results

The Java program measures insertion, lookup and iteration time for all three implementations.

The actual execution times are machine-dependent. The measured values from the program output should be recorded in the final report.

Expected general observations:

- HashMap is suitable for fast searching and retrieval.
- TreeMap is useful when sorted keys are required.
- LinkedHashMap is useful when insertion order must be maintained.

## 6. Ordering Behaviour

The program displays the first five keys obtained during iteration.

- HashMap: Does not guarantee insertion or sorted order.
- TreeMap: Displays keys in sorted order.
- LinkedHashMap: Preserves insertion order.

## 7. Alternatives

### Hashtable

Hashtable is an older synchronized map implementation. It does not allow null keys or null values. For modern concurrent applications, ConcurrentHashMap is generally preferred.

### Sorted Array with Binary Search

A sorted array can be used as an alternative for inventory searching.

- Searching: O(log n) using binary search.
- Insertion: O(n) because elements may need shifting.
- Iteration: O(n).
- Storage: O(n).

This approach is useful when the inventory changes infrequently and searching is performed frequently.

## 8. Analysis and Conclusion

HashMap is appropriate when fast insertion and lookup are the main requirements. TreeMap is preferable when sorted key access is necessary. LinkedHashMap is suitable when the application must preserve insertion order.

Therefore, the selection of a map implementation depends on the application's requirements, data size, ordering needs and performance observations.

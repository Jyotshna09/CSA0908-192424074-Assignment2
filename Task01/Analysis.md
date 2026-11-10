
# Q1 – Building Text Under Load

## 1. Objective
To compare String, StringBuilder and StringBuffer while generating railway e-tickets.

## 2. Prediction Before Execution

- String: Expected to be slower because String objects are immutable.
- StringBuilder: Expected to be faster because it modifies a mutable buffer.
- StringBuffer: Expected to be slightly slower than StringBuilder because its methods are synchronized.

## 3. Experimental Workloads

| Workload | Number of Tickets | Fields per Ticket |
|---|---:|---:|
| Small | 1 | 5 |
| Large | 10,000 | 50 |
| Custom | 1,000 | 100 |

Each approach is measured over five repetitions after warm-up.

## 4. Complexity Analysis

| Approach | Time Complexity | Space Complexity |
|---|---|---|
| String concatenation | O(L²) | O(L²) cumulative allocation in the simplified model |
| StringBuilder | O(L) amortized | O(L) |
| StringBuffer | O(L) amortized | O(L) |

L represents the total length of the generated ticket.

## 5. Design Decision

StringBuilder is recommended for generating individual railway tickets because it provides efficient mutable text construction without unnecessary synchronization.

StringBuffer is recommended when multiple threads need to modify a shared log through synchronized operations.

String is suitable for fixed and unchanging text.

## 6. Alternative Concepts

String.join() can combine fields using a delimiter.

StringJoiner can build strings using delimiters, prefixes and suffixes.

String.format() can create formatted ticket output, but repeated formatting may introduce additional overhead.

## 7. Experimental Results

The execution time, estimated object creation and approximate heap changes are recorded in the program output.

Actual observations:

To be filled after executing the program.

## 8. Conclusion

StringBuilder is generally suitable for high-volume ticket generation. StringBuffer provides synchronized methods for shared mutable text, while String is appropriate for immutable text.

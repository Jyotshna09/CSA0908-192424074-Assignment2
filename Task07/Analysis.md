
# Q7 – Performance Improvement Through Data Structure Redesign

## 1. Selected Limitation

The limitation selected from Task 2 is the poor performance of ArrayList during frequent front insertion and front removal operations.

ArrayList stores elements in a dynamic array. When an element is inserted or removed at index zero, the remaining elements must be shifted.

This can increase execution time when the playlist contains many songs.

## 2. Problem Diagnosis

Consider a music application with an Up Next playlist.

When a user selects a song to play next, the song must be inserted at the beginning of the playlist. After playback, the first song must be removed.

If these operations are performed frequently using ArrayList, multiple elements must be shifted.

The time complexity of front insertion and removal in ArrayList is O(n).

## 3. Design Objective

The objective is to reduce the cost of frequent front insertion and removal while maintaining the same playlist order and functionality.

The redesigned solution should:

- Support adding songs at the beginning.
- Support removing the first song.
- Preserve the correct playlist order.
- Reduce execution time for front operations.
- Maintain correctness for different playlist sizes.

## 4. Proposed Redesign

ArrayDeque is selected as the replacement for ArrayList.

ArrayDeque uses a resizable circular array and supports efficient insertion and removal at both ends.

Original implementation:

- ArrayList.add(0, element)
- ArrayList.remove(0)

Redesigned implementation:

- ArrayDeque.addFirst(element)
- ArrayDeque.removeFirst()

## 5. Complexity Comparison

| Operation | ArrayList | ArrayDeque |
|---|---|---|
| Add at beginning | O(n) | O(1) amortized |
| Remove at beginning | O(n) | O(1) |
| Add at end | O(1) amortized | O(1) amortized |
| Remove at end | O(1) | O(1) |
| Indexed access | O(1) | Not supported |

Both implementations require O(n) space for n playlist elements.

## 6. Experimental Methodology

The experiment compares ArrayList and ArrayDeque using identical workloads.

Playlist sizes:

- 1,000 elements.
- 5,000 elements.
- 10,000 elements.

For each playlist size:

1. Create and populate the playlist.
2. Perform 1,000 front insertion operations.
3. Perform 1,000 front removal operations.
4. Measure execution time using System.nanoTime().
5. Repeat the experiment five times.
6. Calculate average execution time.
7. Verify that both implementations produce the same final playlist.

Two warm-up runs are performed before collecting measurements.

## 7. Experimental Results

Record the actual results from Q7.java.

| Playlist Size | ArrayList Time (ms) | ArrayDeque Time (ms) |
|---|---|---|
| 1,000 | ______ | ______ |
| 5,000 | ______ | ______ |
| 10,000 | ______ | ______ |

The measurements depend on the processor, JVM, memory and system load.

## 8. Analysis of Results

Compare the measured execution times for both implementations.

The expected result is that ArrayDeque performs better for frequent front insertion and removal because these operations do not require shifting all existing elements.

The correctness check verifies that both implementations maintain the same final playlist.

If the measured timings differ from the expected trend, the actual measurements should be reported and discussed rather than changed.

## 9. Trade-offs and Limitations

Advantages of ArrayDeque:

- Efficient insertion and removal at both ends.
- Suitable for queue and stack operations.
- Avoids shifting elements during front operations.

Limitations:

- Does not support direct indexed access.
- Does not allow null elements.
- ArrayList is preferable when frequent random access is required.

The benchmark is a classroom microbenchmark and is not a fully controlled JMH experiment. JVM optimization, garbage collection and background processes can influence measurements.

## 10. Real-World Application

A music streaming application can use ArrayDeque to manage its Up Next playlist.

When a user selects a song to play immediately, the application can insert it at the front. Once playback begins, the first song can be removed efficiently.

This makes ArrayDeque a suitable choice for applications that frequently operate at the beginning or end of a collection.

## 11. Conclusion

The experiment identifies the performance limitation of ArrayList during frequent front operations and proposes ArrayDeque as an alternative.

The redesign is supported by complexity analysis, execution-time measurements and correctness validation.

ArrayDeque is a better choice for the selected Up Next playlist workload, while ArrayList remains useful for applications requiring frequent indexed access.

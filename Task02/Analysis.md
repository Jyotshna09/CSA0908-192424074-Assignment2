
# Q2 – When Is ArrayList an Appropriate Engineering Choice?

## 1. Objective

To compare ArrayList, LinkedList and ArrayDeque for different playlist operations.

## 2. Experimental Design

Three playlist sizes were selected:

| Experiment | Playlist Size |
|---|---:|
| Small | 1,000 |
| Medium | 5,000 |
| Large | 10,000 |

Each experiment was repeated five times, and average execution time was calculated.

## 3. Expected Time Complexity

| Operation | ArrayList | LinkedList | ArrayDeque |
|---|---|---|---|
| Add at end | O(1) amortized | O(1) | O(1) amortized |
| Insert at front | O(n) | O(1) | O(1) amortized |
| Insert in middle | O(n) | O(n) | Not supported |
| Remove from front | O(n) | O(1) | O(1) amortized |
| Remove from middle | O(n) | O(n) | Not supported |
| Access k-th element | O(1) | O(n) | Not supported |
| Full iteration | O(n) | O(n) | O(n) |

## 4. Space Complexity

- ArrayList: Stores elements in a dynamic array. Requires O(n) storage.
- LinkedList: Stores elements in separate nodes containing data and links. Requires O(n) storage with additional node overhead.
- ArrayDeque: Stores elements in a resizable circular array. Requires O(n) storage.

## 5. Experimental Results

The program measures the average execution time of different operations for all three playlist sizes.

Actual observations:

To be filled after executing the program.

## 6. Engineering Analysis

ArrayList is a reasonable choice when users frequently access songs by index, add songs at the end and iterate through playlists.

LinkedList is useful when frequent insertions and removals occur at the beginning or through an already-known iterator position. Finding a middle position still requires traversal.

ArrayDeque is suitable for an Up Next queue because it supports efficient insertion and removal at both ends.

ArrayDeque does not support indexed access or insertion at arbitrary middle positions.

## 7. Alternative Concept: Plain Array

A plain array can store playlist songs.

- Accessing an element: O(1).
- Inserting at the end when space exists: O(1).
- Inserting at the front or middle: O(n), due to shifting.
- Removing at the front or middle: O(n), due to shifting.
- Iteration: O(n).

Unlike ArrayList, a plain array has a fixed capacity unless a larger array is manually created and copied.

## 8. Changed Condition

When the application introduces an Up Next queue, ArrayDeque becomes a better choice because it supports adding songs at both ends and removing songs from the front efficiently.

## 9. Conclusion

ArrayList is the preferred choice for ordinary playlists requiring frequent indexed access. LinkedList is useful for operations at known positions, while ArrayDeque is the preferred structure for double-ended queue operations.


# Q5 – Generics, Comparator and Comparable

## 1. Objective

To implement a generic leaderboard using Java Generics and Comparator. The objective is to rank teams based on points, goal difference and team name while demonstrating type safety and code reusability.

## 2. Understanding Generics

Generics allow classes, interfaces and methods to work with different data types while providing compile-time type safety.

Example:

`ArrayList<Integer> numbers = new ArrayList<>();`

Here, the ArrayList stores only Integer values.

Benefits:
- Type safety.
- Code reusability.
- Reduced type casting.
- Easier maintenance.

## 3. Comparator

Comparator is used to define custom sorting logic.

In this experiment, the leaderboard follows three conditions:

1. Teams with higher points are ranked first.
2. If points are equal, higher goal difference is ranked first.
3. If both are equal, team names are arranged alphabetically.

This provides a consistent ranking mechanism.

## 4. Comparable

Comparable defines the natural ordering of objects using the compareTo() method.

For example, Integer values are naturally sorted in ascending order.

The program demonstrates this using Collections.sort().

## 5. Generic Leaderboard

The Leaderboard<T> class accepts different object types using a generic type parameter.

It provides:
- add(): Adds an item to the leaderboard.
- getRankedList(): Returns a sorted copy.
- display(): Displays ranked results.

Using a generic class avoids creating separate leaderboard implementations for different object types.

## 6. Wildcards

The program uses `List<? extends Number>`.

This upper-bounded wildcard allows the method to accept lists of Number or its subclasses, such as Integer, Double and Float.

The comparator also uses `Comparator<? super T>` to support comparators defined for the generic type or its parent types.

## 7. Complexity Analysis

Let n represent the number of teams.

| Operation | Time Complexity |
|---|---|
| Adding a team | O(1) amortized |
| Copying the list | O(n) |
| Sorting | O(n log n) |
| Displaying results | O(n) |

Space complexity: O(n), because a separate copy is created for sorting.

## 8. Alternative Approaches

### Using Comparable

The Team class can implement Comparable<Team> and define its natural ranking using compareTo().

This is useful when the same sorting order is required throughout the application.

### Stable Multi-Stage Sorting

The leaderboard can also use multiple stable sorting operations to apply tie-breaking conditions.

However, a single Comparator chain is clearer and easier to maintain.

## 9. Results and Observations

The program displays the teams in descending points order. Teams with equal points are compared using goal difference. If both values are equal, alphabetical team-name ordering is applied.

The program also demonstrates natural ordering using Comparable and generic wildcard usage.

## 10. Conclusion

The experiment demonstrates how Java Generics improve reusability and type safety. Comparator provides flexible custom sorting, while Comparable supports natural ordering.

These concepts are useful in real-world applications such as sports leaderboards, student ranking systems, employee performance lists and online gaming rankings.

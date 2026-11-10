
# Q6 – PriorityQueue-Based Hospital Patient Triage System

## 1. Objective

To implement a hospital patient triage system using Java PriorityQueue. Patients are prioritized based on medical severity, while patients with equal severity are treated according to arrival time.

## 2. PriorityQueue Implementation

PriorityQueue is a queue that processes elements according to priority rather than simple insertion order.

In this experiment:
- Severity 1 represents the highest priority.
- Severity 5 represents the lowest priority.
- Patients with the same severity are ordered by arrival time.

The comparator uses severity first and arrival time second.

## 3. Experimental Setup

The program tests three patient queue sizes:

- Small queue: 3 patients.
- Medium queue: 5 patients.
- Large queue: 8 patients.

The treatment order is displayed by repeatedly removing the highest-priority patient using poll().

## 4. Time Complexity

| Operation | PriorityQueue |
|---|---|
| Insert patient (offer) | O(log n) |
| Remove highest priority (poll) | O(log n) |
| View highest priority (peek) | O(1) |
| Iterate through queue | O(n) |

Space complexity: O(n).

## 5. Arrival Order

When two patients have the same severity, their arrival numbers are compared.

The patient who arrived earlier is processed first. This ensures FIFO behaviour among patients with equal severity.

## 6. Starvation Problem

Starvation occurs when low-priority patients continuously wait because higher-priority patients keep arriving.

In a hospital system, this can cause long waiting times for patients whose conditions are less severe.

## 7. Fairness Improvement Using Aging

Aging is a technique used to gradually improve a waiting patient's priority.

In this implementation:
- Waiting time is calculated.
- Every 20 time units, the effective priority of a non-critical patient improves by one level.
- The critical severity level remains protected.

This reduces starvation while ensuring that critical patients retain the highest priority.

## 8. Alternative Data Structures

### LinkedList with Sorted Insertion

Patients can be inserted into a LinkedList according to severity and arrival time.

- Insertion: O(n).
- Removal of first patient: O(1).
- Space: O(n).

### Five FIFO Queues

Five separate FIFO queues can be maintained, one for each severity level.

- Insertion: O(1).
- Removal: O(1) when checking the five queue heads.
- Space: O(n).

This approach is useful when the number of priority levels is fixed.

## 9. Analysis

PriorityQueue is suitable for dynamically managing patients according to severity. It efficiently inserts patients and retrieves the highest-priority patient.

However, a basic priority queue may cause starvation for low-priority patients. The aging technique provides a fairness improvement by increasing the priority of patients who have waited longer.

## 10. Conclusion

The experiment demonstrates the use of PriorityQueue in a real-world hospital triage system. Severity-based ordering, arrival-time tie-breaking and aging can improve patient management and reduce unnecessary waiting.

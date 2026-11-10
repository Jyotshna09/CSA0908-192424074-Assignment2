
# Q3 – Engineer the hashCode–equals Contract

## 1. Objective

To investigate how equals() and hashCode() affect duplicate detection in HashSet.

## 2. Understanding the Concepts

equals() compares two objects based on their logical values.

hashCode() generates an integer value used by hash-based collections to identify the bucket where an object should be stored.

According to the Java contract:

- If two objects are equal according to equals(), they must have the same hash code.
- Two objects with the same hash code do not necessarily have to be equal.

## 3. Experimental Tests

### Test 1: Incorrect hashCode()

Two students have the same registration number but different identity-based hash codes.

Prediction: Set size will be 3.

Observation: The duplicate student is stored because the hash codes differ.

### Test 2: Correct hashCode()

The Student class overrides hashCode() using registration number.

Prediction: Set size will be 2.

Observation: The duplicate student is rejected by HashSet.

### Test 3: Immutable Registration Number

The registration number is declared final.

Prediction: The registration number cannot be changed after object creation.

Observation: The unique student identity remains stable, preventing hash-related lookup problems caused by changing the registration number.

## 4. Why Do Duplicates Appear?

HashSet first uses hashCode() to locate a bucket. It then uses equals() to compare objects within that bucket.

If equal objects produce different hash codes, they may be placed in different buckets. Therefore, HashSet may fail to identify them as duplicates.

## 5. Correcting the Student Class

The corrected implementation overrides both equals() and hashCode().

The registration number is used in both methods and declared final.

This maintains consistency and prevents changes to the field used for hashing.

## 6. Alternative Concepts

### TreeSet

TreeSet can store unique students using a Comparator based on registration number.

Insertion and searching generally take O(log n).

### HashMap

HashMap<String, Student> can use registration number as the key.

Before inserting a student, the program checks whether the registration number already exists.

Average insertion and lookup take O(1).

## 7. Complexity Analysis

| Structure | Search/Insertion | Space |
|---|---|---|
| HashSet | O(1) average | O(n) |
| TreeSet | O(log n) | O(n) |
| HashMap | O(1) average | O(n) |

## 8. Conclusion

The experiment demonstrates that overriding equals() alone is insufficient for correct HashSet behaviour.

Both equals() and hashCode() must follow the Java contract. Using an immutable registration number provides a reliable way to identify unique students.

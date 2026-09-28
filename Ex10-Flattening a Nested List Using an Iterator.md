# Flattening a Nested List Using an Iterator

## DATE: 18-09-2026

## AIM:

To design and implement a class `NestedIterator` that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (`next()` and `hasNext()`).

## Algorithm

1. Start and create a nested list containing integers and other nested lists.
2. Create the `NestedIterator` class and use a list to store all the integer elements in flattened form.
3. Recursively traverse each element; if it is an integer, add it to the flattened list, otherwise recursively process the nested list.
4. Implement `hasNext()` to check whether more integers are available and `next()` to return the next integer.
5. Stop and display all integers sequentially using the iterator.

## Program:

```java
/*
Program to find Flattening a Nested List Using an Iterator
Developed by: charan kumar s
RegisterNumber: 212223220015
*/

import java.util.*;

public class Main {

    // NestedInteger interface
    interface NestedInteger {
        boolean isInteger();
        Integer getInteger();
        List<NestedInteger> getList();
    }

    // Implementation of NestedInteger
    static class MyNestedInteger implements NestedInteger {

        Integer value;
        List<NestedInteger> list;

        MyNestedInteger(int value) {
            this.value = value;
            this.list = null;
        }

        MyNestedInteger(List<NestedInteger> list) {
            this.list = list;
            this.value = null;
        }

        public boolean isInteger() {
            return value != null;
        }

        public Integer getInteger() {
            return value;
        }

        public List<NestedInteger> getList() {
            return list;
        }
    }

    // NestedIterator class
    static class NestedIterator implements Iterator<Integer> {

        List<Integer> flattenedList = new ArrayList<>();
        int index = 0;

        NestedIterator(List<NestedInteger> nestedList) {
            flatten(nestedList);
        }

        // Recursively flatten the nested list
        void flatten(List<NestedInteger> nestedList) {

            for (NestedInteger element : nestedList) {

                if (element.isInteger()) {
                    flattenedList.add(element.getInteger());
                } else {
                    flatten(element.getList());
                }
            }
        }

        // Check if another integer exists
        public boolean hasNext() {
            return index < flattenedList.size();
        }

        // Return the next integer
        public Integer next() {
            return flattenedList.get(index++);
        }
    }

    public static void main(String[] args) {

        // Create nested list:
        // [1, [2, [3, 4]], 5]

        List<NestedInteger> nestedList = new ArrayList<>();

        nestedList.add(new MyNestedInteger(1));

        List<NestedInteger> list1 = new ArrayList<>();
        list1.add(new MyNestedInteger(2));

        List<NestedInteger> list2 = new ArrayList<>();
        list2.add(new MyNestedInteger(3));
        list2.add(new MyNestedInteger(4));

        list1.add(new MyNestedInteger(list2));

        nestedList.add(new MyNestedInteger(list1));

        nestedList.add(new MyNestedInteger(5));

        // Create iterator
        NestedIterator iterator = new NestedIterator(nestedList);

        // Display flattened list
        System.out.print("Flattened List: ");

        while (iterator.hasNext()) {
            System.out.print(iterator.next() + " ");
        }
    }
}
```

## Output:


<img width="387" height="128" alt="image" src="https://github.com/user-attachments/assets/43e7ac79-3ab7-48d7-a1c0-7876ec6a6405" />


## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.

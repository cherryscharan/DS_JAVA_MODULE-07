# Ex8 Detection of a Cycle in a Linked List

## DATE: 18-09-2026

## AIM:

To write a Java program that detects a cycle in a linked list and returns the node where the cycle begins. If there is no cycle, the program should return `null` without modifying the linked list.

## Algorithm

1. Start and create the singly linked list with the given elements.
2. Use two pointers, `slow` and `fast`, and move `slow` one step and `fast` two steps at a time.
3. If `slow` and `fast` meet, a cycle exists in the linked list.
4. Set `slow` back to `head` and move both pointers one step at a time; the point where they meet is the **start of the cycle**.
5. If `fast` reaches `null`, there is no cycle; return `null` without modifying the linked list.

## Program:

```java
/*
program that detects a cycle in a linked list and returns the node
where the cycle begins. If there is no cycle, the program returns null.
Developed by: charan kumar s
RegisterNumber: 212223220015
*/

import java.util.Scanner;

public class Main {

    // Node class
    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    // Insert node at the end
    static Node insert(Node head, int data) {

        Node newNode = new Node(data);

        if (head == null) {
            return newNode;
        }

        Node temp = head;

        while (temp.next != null) {
            temp = temp.next;
        }

        temp.next = newNode;

        return head;
    }

    // Detect cycle and return the node where cycle begins
    static Node detectCycle(Node head) {

        Node slow = head;
        Node fast = head;

        // Find if a cycle exists
        while (fast != null && fast.next != null) {

            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {

                // Find the beginning of the cycle
                slow = head;

                while (slow != fast) {
                    slow = slow.next;
                    fast = fast.next;
                }

                return slow;
            }
        }

        // No cycle
        return null;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        Node head = null;

        int n = sc.nextInt();

        // Store all nodes
        Node[] nodes = new Node[n];

        // Create linked list
        for (int i = 0; i < n; i++) {
            int data = sc.nextInt();
            head = insert(head, data);
        }

        // Store nodes in the array
        Node temp = head;

        for (int i = 0; i < n; i++) {
            nodes[i] = temp;
            temp = temp.next;
        }

        // Read position where cycle should begin
        int pos = sc.nextInt();

        // Create cycle if position is valid
        if (pos >= 0 && pos < n) {
            nodes[n - 1].next = nodes[pos];
        }

        // Detect cycle
        Node cycleStart = detectCycle(head);

        if (cycleStart != null) {
            System.out.println("Cycle begins at node: " + cycleStart.data);
        } else {
            System.out.println("No cycle");
        }
    }
}
```

## Output:

<img width="377" height="116" alt="image" src="https://github.com/user-attachments/assets/225b4483-c0ea-4788-9463-e710a8ea933e" />



## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.

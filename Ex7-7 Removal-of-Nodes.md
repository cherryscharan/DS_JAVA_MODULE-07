# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE: 18-09-2026
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
1. Start and create the singly linked list with the given elements.
2. Read the integer val whose matching nodes must be removed.
3. Remove all matching nodes from the beginning of the list and update head.
4. Traverse the remaining list and remove every node whose value equals val.
5. Stop and return/display the new head of the modified linked list.  

## Program:
```
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
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

    // Remove all nodes whose value matches val
    static Node removeElements(Node head, int val) {

        // Remove matching nodes from the beginning
        while (head != null && head.data == val) {
            head = head.next;
        }

        Node temp = head;

        // Remove matching nodes from the rest of the list
        while (temp != null && temp.next != null) {

            if (temp.next.data == val) {
                temp.next = temp.next.next;
            } else {
                temp = temp.next;
            }
        }

        return head;
    }

    // Display the linked list
    static void display(Node head) {

        Node temp = head;

        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }

        System.out.println();
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        Node head = null;

        int n = sc.nextInt();

        // Create linked list
        for (int i = 0; i < n; i++) {
            int data = sc.nextInt();
            head = insert(head, data);
        }

        // Read value to remove
        int val = sc.nextInt();

        // Remove matching nodes
        head = removeElements(head, val);

        // Display modified list
        display(head);
    }
}
```

## Output:

<img width="379" height="122" alt="image" src="https://github.com/user-attachments/assets/26832131-27b7-4294-8ff8-81d67371efe3" />


## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.

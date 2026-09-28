# Ex6 Right Rotation LinkedList
## DATE:18/09/2026
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.
## Algorithm
1. Start and create a singly linked list by inserting the given elements.
2. Find the length of the linked list and calculate k = k % length.
3. Connect the last node to the first node to temporarily make the list circular.
4. Move length - k positions to find the new tail, set the next node as the new head, and break the circular link.
5. Stop and display the rotated linked list. 

## Program:
```
/*
Program to  Right Rotation LinkedList
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

    // Insert a node at the end
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

    // Rotate the linked list to the right by k positions
    static Node rotateRight(Node head, int k) {

        if (head == null || head.next == null || k == 0) {
            return head;
        }

        // Find the length of the list
        int length = 1;
        Node temp = head;

        while (temp.next != null) {
            temp = temp.next;
            length++;
        }

        // Avoid unnecessary rotations
        k = k % length;

        if (k == 0) {
            return head;
        }

        // Make the list circular
        temp.next = head;

        // Find the new tail
        int steps = length - k;
        Node newTail = head;

        for (int i = 1; i < steps; i++) {
            newTail = newTail.next;
        }

        // New head is after the new tail
        Node newHead = newTail.next;

        // Break the circle
        newTail.next = null;

        return newHead;
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

        int k = sc.nextInt();

        // Rotate the list
        head = rotateRight(head, k);

        // Display rotated list
        display(head);
    }
}
```

## Output:


<img width="385" height="114" alt="image" src="https://github.com/user-attachments/assets/628b9e48-6ae0-41bb-bcd6-6c00fa104647" />



## Result:
Thus, the C program to perfom right rotation on linked list is implemented successfully.

# Ex6 Right Rotation LinkedList
## DATE:
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.
## Algorithm
```text
1. Start
2. Read the number of nodes n
3. Initialize head as null
4. Repeat the following steps n times:
   a) Read a data value
   b) Create a new node with this data
   c) If head is null, set head to this new node
   d) Otherwise, traverse to the last node and link its next to this new node
5. Read the integer k (number of positions to rotate to the right)
6. If head is null, or head->next is null, or k = 0, then go to Step 15
7. Traverse the list to find its length len
8. Compute k = k mod len
9. If k = 0, go to Step 15
10. Traverse to the last node (tail) of the list
11. Set tail->next = head to make the list circular
12. Compute stepsToNewTail = len - k
13. Set newTail = head
14. Move newTail forward (stepsToNewTail - 1) times
15. Set newHead = newTail->next
16. Set newTail->next = null to break the circle
17. Starting from newHead, traverse the list and print each node’s data
18. End
```

## Program:
Program to  Right Rotation LinkedList
```java
import java.util.Scanner;



public class Main {
    private static class Node {
        int data;
        Node next;
        Node(int d) {
            data = d;
            next = null;
        }
    }
    static Node insertEnd(Node head, int data) {
        Node newNode = new Node(data);
        if (head == null)
            return newNode;
        Node temp = head;
        while (temp.next != null)
            temp = temp.next;
        temp.next = newNode;
        return head;
    }

    static int length(Node head) {
        int len = 0;
        Node temp = head;
        while (temp != null) {
            len++;
            temp = temp.next;
        }
        return len;
    }

    static Node rotateRight(Node head, int k) {
        if (head == null || head.next == null || k == 0)
            return head;
        int len = length(head);
        k = k % len;
        if (k == 0)
            return head;
        Node tail = head;
        while (tail.next != null)
            tail = tail.next;
        tail.next = head;
        int stepsToNewTail = len - k;
        Node newTail = head;
        for (int i = 1; i < stepsToNewTail; i++)
            newTail = newTail.next;
        Node newHead = newTail.next;
        newTail.next = null;
        return newHead;
    }

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
        int n = sc.nextInt();
        Node head = null;
        for (int i = 0; i < n; i++)
            head = insertEnd(head, sc.nextInt());
        int k = sc.nextInt();
        head = rotateRight(head, k);
        display(head);
        sc.close();
    }
}

```
Developed by: THILAK RAJ . P  
RegisterNumber:  212224040353
## Output:
<img width="423" height="378" alt="image" src="https://github.com/user-attachments/assets/215108d2-bc3d-48d9-b6b9-8585ed4b34ca" />



## Result:
Thus, the Java program to perfom right rotation on linked list is implemented successfully.

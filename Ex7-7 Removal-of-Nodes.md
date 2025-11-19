# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE:
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
```text
1. Start
2. Read the number of nodes n
3. Initialize head as null
4. Repeat n times:
   a) Read a data value
   b) Create a new node with this data
   c) Insert the new node at the end of the linked list
5. Read the integer val (value to be removed)
6. While head is not null and head.data equals val:
   a) Set head = head.next
7. Set current = head
8. While current is not null and current.next is not null:
   a) If current.next.data equals val:
        i) Set current.next = current.next.next
      Else:
        ii) Set current = current.next
9. Traverse the list starting from head and print each node’s data
10. End
```

## Program:

program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
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

    static Node removeElements(Node head, int val) {
        while (head != null && head.data == val)
            head = head.next;
        Node current = head;
        while (current != null && current.next != null) {
            if (current.next.data == val)
                current.next = current.next.next;
            else
                current = current.next;
        }
        return head;
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
        int val = sc.nextInt();
        head = removeElements(head, val);
        display(head);
        sc.close();
    }
}
```
Developed by: THILAK RAJ . P  
RegisterNumber:  212224040353


## Output:

<img width="452" height="387" alt="image" src="https://github.com/user-attachments/assets/c7f764af-c772-4c77-81ed-9d861801c080" />


## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.

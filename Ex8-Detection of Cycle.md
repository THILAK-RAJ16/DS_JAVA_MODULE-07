# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## DATE:
## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
## Algorithm
```text
1. Start
2. Read the number of nodes n
3. Initialize head as null
4. Repeat n times:
   a) Read a data value
   b) Create a new node with this data
   c) Insert the new node at the end of the linked list
5. Read an integer pos (position to connect tail to, -1 means no cycle)
6. If pos is not -1:
   a) Traverse the list to find the tail node
   b) Traverse the list to find the node at index pos
   c) Set tail.next to that node to create a cycle
7. To detect the cycle, set slow = head and fast = head
8. While fast is not null and fast.next is not null:
   a) Move slow one step forward
   b) Move fast two steps forward
   c) If slow and fast point to the same node, a cycle is detected; go to step 9
9. To find the start of the cycle:
   a) Set p1 = head and p2 = slow
   b) While p1 is not equal to p2:
        i) Move p1 one step forward
       ii) Move p2 one step forward
   c) The node where p1 and p2 meet is the start of the cycle
10. If a cycle was found, print the data value of the start node
11. If no cycle was found, print null
12. End
```

## Program:
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
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

    static Node detectCycle(Node head) {
        if (head == null || head.next == null)
            return null;
        Node slow = head;
        Node fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                Node p1 = head;
                Node p2 = slow;
                while (p1 != p2) {
                    p1 = p1.next;
                    p2 = p2.next;
                }
                return p1;
            }
        }
        return null;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Node head = null;
        for (int i = 0; i < n; i++)
            head = insertEnd(head, sc.nextInt());
        int pos = sc.nextInt();
        if (pos >= 0) {
            Node tail = head;
            Node join = null;
            int index = 0;
            while (tail.next != null) {
                if (index == pos)
                    join = tail;
                tail = tail.next;
                index++;
            }
            if (index == pos)
                join = tail;
            if (join != null)
                tail.next = join;
        }
        Node cycleStart = detectCycle(head);
        if (cycleStart == null)
            System.out.println("null");
        else
            System.out.println(cycleStart.data);
        sc.close();
    }
}
```
Developed by: THILAK RAJ . P  
RegisterNumber:  212224040353


## Output:
<img width="524" height="389" alt="image" src="https://github.com/user-attachments/assets/ccbe8f98-52ba-42fd-9490-81224ac9b978" />



## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.

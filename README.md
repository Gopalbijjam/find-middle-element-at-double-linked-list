# find-middle-element-at-double-linked-list
class Node {
    int data;
    Node next;
    Node prev;

    Node(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

public class FindMiddleOfDoublyLinkedList {

    // Method to find the middle node in a doubly linked list
    static Node findMiddle(Node head) {
        if (head == null) return null;

        Node slow = head;
        Node fast = head;

        while (fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;
        }

        return slow;
    }

   
    static Node createDoublyLinkedList(int[] values) {
        if (values.length == 0) return null;

        Node head = new Node(values[0]);
        Node current = head;

        for (int i = 1; i < values.length; i++) {
            Node newNode = new Node(values[i]);
            current.next = newNode;
            newNode.prev = current;
            current = newNode;
        }

        return head;
    }

    public static void main(String[] args) {
     
        int[] values = {1, 2, 3, 4, 5};
        Node head = createDoublyLinkedList(values);
        Node middleNode = findMiddle(head);
        if (middleNode != null) {
            System.out.println("The middle node value is: " + middleNode.data);
        } else {
            System.out.println("The list is empty.");
        }
    }
}

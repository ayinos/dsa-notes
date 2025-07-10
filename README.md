# dsa-notes
Notes on dsa &amp; leetcode problems.

# LinkedList
## Linked List Problems

### Find Middle Node 
```java
public Node findMiddleNode(){
    Node slow = head;
    Node fast = head;
  
    while (fast != null && fast.next != null){
        slow = slow.next;
        fast = fast.next.next;
    }
    
    return slow;
}
```

### Has Loop
```java
 public boolean hasLoop(){
      Node slow = head;
      Node fast = head;
      
      while(fast != null && fast.next != null){
          slow = slow.next;
          fast = fast.next.next;
          
          if(slow == fast){
              return true;
          }
      }
      return false;
  }
```
### Find Nth Node From End

```java
public Node findNthFromEnd(int n){
    Node slow = head;
    Node fast = head;
    
    //Move fast ahead by k positions
    for (int i = 0; i < n; i++) {
        //if n is more than the length of the list return null
        if (fast == null) {
            return null;
        }
        fast = fast.next;
    }

    
    //Then move both by one position untill fast reaches the end.
    while(fast != null){
        slow = slow.next;
        fast = fast.next;
    }
    
    return slow;
}
```

### Convert Binary Number in a Linked List to Integer

```java
public int binaryToDecimal(){
    Node curr = head;
    int binaryValue = 0;
    
    while (curr != null){
        if(curr.value == 1){
            binaryValue = (binaryValue * 2) + 1;
        }
        else{
            binaryValue = (binaryValue * 2) + 0;
        }
        curr = curr.next;
    }
    
    return binaryValue;
}
```

### 86. Partition List 
```java
public void partitionList(int x){
    if (head == null) return;

    //Less than elements list
    Node dummy1 = new Node(0); //First node of less than elements list
    Node curr1 = dummy1; //Pointer to last node of less than elements list
    
    //Greater than elements list
    Node dummy2 = new Node(0);
    Node curr2 = dummy2;
    
    Node curr = head;
    
    while(curr != null){
        if (curr.value < x){
            curr1.next = curr;
            curr1 = curr;
            
        }else{
            curr2.next = curr;
            curr2 = curr;
        }
        curr = curr.next;
    }
    curr2.next = null;
    
    curr1.next = dummy2.next;
    head = dummy1.next;
    
}
```

### 92. Reverse Linked List II  
```java
public ListNode reverseBetween(ListNode head, int left, int right) {

    //Create a dummy node pointing to the head
    ListNode dummy = new ListNode (0, head);

    //For saving the node before left
    ListNode leftPrevNode = dummy;
    ListNode curr = head;

    //Move curr to left position & leftPrevNode to the node before left.
    //The reference to node before left is needed,
    //since we need to point to to the right end node.
    for(int i = 0; i<left-1;i++){
        leftPrevNode = curr;
        curr = curr.next;
    }

    ListNode prev = null;

    for(int i=0; i<right-left+1; i++){
        //Save curr since we are going to break curr->next to curr->prev
        //and we need curr.next to iterate.
        ListNode tempNext = curr.next;
        curr.next = prev;//Reverse link
        prev = curr; //Move prev pointer ahead
        curr = tempNext; //Move curr pointer ahead
    }

    //Update pointers
    leftPrevNode.next.next = curr;
    leftPrevNode.next = prev;

    //Return head
    return dummy.next;
}
```

### 24. Swap Nodes in Pairs
```java
public ListNode swapPairs(ListNode head) {
    ListNode dummy = new ListNode(0, head);

    //Pointer to node previous to the pair.
    //Needed so that the link between pairs is maintained.
    ListNode prevToPair = dummy; 

    //First element in the pair
    ListNode first = head; 

    while(first != null && first.next != null){
        ListNode second = first.next; //Second element in the pair.
      
        //Swap
        prevToPair.next = second;
        first.next = second.next;
        second.next = first;

        //Move pointers ahead.
        //After swapping first element is swapped to second. 
        //Hence first becomes the new prevToPair.
        prevToPair = first; 
        //Move ahead first as well.
        first = first.next;
    }

    return dummy.next;
}
```

## Doubly Linked List
### Constructor
```java
public class DoublyLinkedList {

    private Node head;
    private Node tail;
    private int length;
    
    class Node{
        int value;
        Node next;
        Node prev;
        
        Node (int value){
            this.value = value;
        }
    }
    
    public DoublyLinkedList (int value){
        Node newNode = new Node(value);
        head = newNode;
        tail = newNode;
        length = 1;
    } 

    public Node getHead() {
        return head;
    }

    public Node getTail() {
        return tail;
    }

    public int getLength() {
        return length;
    }

    public void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.println(temp.value);
            temp = temp.next;
        }
    }

    public void printAll() {
        if (length == 0) {
            System.out.println("Head: null");
            System.out.println("Tail: null");
        } else {
            System.out.println("Head: " + head.value);
            System.out.println("Tail: " + tail.value);
        }
        System.out.println("Length:" + length);
        System.out.println("\nDoubly Linked List:");
        if (length == 0) {
            System.out.println("empty");
        } else {
            printList();
        }
    }
}
```

### Append
```java
public void append(int value){
    Node node = new Node(value);
    
    if(tail != null){
        node.prev = tail;
        tail.next = node;
        tail = node;
    }
    else{
        tail = head = node;
    }
    length++;
}
```

### Remove Last
```java
public Node removeLast(){
    if (length == 0){
        return null;
    }
    else if(length == 1){
        Node temp = tail;
        head = tail = null;
        length --;
        return temp;
    }
    else{
        Node temp = tail;
        
        tail = tail.prev;
        tail.next = null;
        temp.prev = null;
        length --;
        
        return temp;
        
    }
}
```

### Prepend
```java
    public void prepend(int value){
        Node node = new Node(value);
        
        if(length == 0){
            head = tail = node;
        }
        else{
            node.next = head;
            head.prev = node;
            head = node;
        }
        length++;
    }
```

### Renove First
```java
    public Node removeFirst(){
        
        if(length == 0)
            return null;
        
        Node first = head;
        
        if (length == 1){
            head = tail = null;
        }
        else{
            head = head.next;
            head.prev = null;
            first.next = null;
        }
        length --;
        return first;
    }
```

### Get
```java
public Node get(int index){
        if (index < 0 || index >= length){
            return null;
        }
        else{
            Node temp = null;
            if(index < length/2){
                temp = head;
                for(int i=0; i<index;i++){
                    temp = temp.next;
                }
            }
            else{
                temp = tail;
                for(int i=length-1; i>index;i--){
                    temp = temp.prev;
                }
            }
            return temp;
        }
                
    }
```

### Set
```java
public boolean set(int index, int value){
    Node node = get(index);
    if(node!=null){
        node.value = value;
        return true;
    }
    return false;
}
```



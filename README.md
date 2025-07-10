# dsa-notes
Notes on dsa &amp; leetcode problems.

# LinkedList

<table>
<tr>
<td><b>Problem</b></td> <td><b>Visual</b></td><td><b>Code</b></td>
</tr>
  
<tr>
<td> Find Middle Node </td>
<td> Visual TBD </td>
<td>
  
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

</td>
</tr>

<tr>
<td> Has Loop </td>
<td> Visual TBD </td>
<td>
  
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

</td>
</tr>

<tr>
<td> Find Nth Node From End </td>
<td> Visual TBD </td>
<td>
  
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

</td>
</tr>

<tr>
<td> Convert Binary Number in a Linked List to Integer </td>
<td> Visual TBD </td>
<td>
  
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

</td>
</tr>

<tr>
<td> 86. Partition List </td>
<td> Visual TBD </td>
<td>
  
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

</td>
</tr>

<tr>
<td> 92. Reverse Linked List II </td>
<td> Visual TBD </td>
<td>
  
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

</td>
</tr>
```

</td>
</tr>

</table>


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
</table>


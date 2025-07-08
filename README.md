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
</table>

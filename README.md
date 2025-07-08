# dsa-notes
Notes on dsa &amp; leetcode problems.

# LinkedList

<table>
<tr>
<td> Problem </td> <td> Visual </td> <td> Code </td>
</tr>
  
<tr>
<td> Find middle node  </td>
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

</table>

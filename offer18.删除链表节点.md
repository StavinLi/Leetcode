let deleteNode = function(head, val){
  if(head.val === val){
    return head.next
  }
  head.next = deleteNode(head.next, val)
  return head
}
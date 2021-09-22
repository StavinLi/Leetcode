
1.顺序查找

<!-- 时间复杂度：O(n)，其中 n 为链表的长度。需要两次遍历。

空间复杂度：O(1)。 -->
var getKthFromEnd = function(head, k){
  let node = head, num = 0;
  while(node){
    node = node.next
    num++
  }
  node = head
  for(let i = 0; i < num - k; i++){
    node = node.next
  }
  return node
}
方法二：双指针
思路与算法

快慢指针的思想。我们将第一个指针 fast 指向链表的第 k + 1  个节点，第二个指针 slow 指向链表的第一个节点，此时指针 fast 与 slow 二者之间刚好间隔  k  个节点。此时两个指针同步向后走，当第一个指针 fast 走到链表的尾部空节点时，则此时 slow 指针刚好指向链表的倒数第 k 个节点。

我们首先将 fast 指向链表的头节点，然后向后走  k  步，则此时 fast 指针刚好指向链表的第 k + 1  个节点。

我们首先将 slow 指向链表的头节点，同时 slow 与 fast 同步向后走，当 fast 指针指向链表的尾部空节点时，则此时返回 slow 所指向的节点即可。

<!-- 时间复杂度：O(n) ，其中 n 为链表的长度。我们使用快慢指针，只需要一次遍历即可，复杂度为 O(n) 。

空间复杂度：O(1)。 -->
```
var getKthFromEnd = function(head, k){
  let fast = head, slow = head;
  while(fast && k > 0){
    [fast, k] = [fast.next, k-1]
  }
  while(fast){
    [fast, slow] = [fast.next, slow.next]
  }
  return slow
}
```
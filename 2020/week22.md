## Algorithm

```
/// 92. 反转链表 II
    func reverseBetween(_ head: ListNode?, _ m: Int, _ n: Int) -> ListNode? {
        if head == nil { return nil }
        var count = 1
        var current = head
        var last: ListNode? = nil //last表示已经反转好的部分链表的头结点
        var start: ListNode? = nil  //start表示开始反转的节点前一个节点
        var end: ListNode? = head     //end表示反转部分的最后一个节点
        while current != nil {
            if count < m {
                start = current
                current = current?.next
                end = current
            } else if count < n + 1 {
                let next = current?.next
                current?.next = last
                last = current
                current = next
            } else {
                break
            }
            count += 1
        }
        end?.next = current
        start?.next = last
        if m == 1 {
            return last
        } else {
            return head
        }
    }
```

## Review
[Objective-C Documentation](https://nshipster.com/objective-c-documentation/)

## Tip    
使用CALayer的`zPosition`属性，可以修改layer的显示层级，`zPosition`值越大，显示越靠上。但是这并不影响UIView的响应链，各种事件的响应流程还是按UIView的层级来传递，所以修改`zPosition`可能会造成“你以为点击的是看到的最上面的A，但其实点到是A下面的B”这种奇葩的表现，还是慎用为妙。

## Share
[Type Encodings](https://nshipster.com/type-encodings/)

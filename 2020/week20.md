## Algorithm

```
/// 86. 分隔链表
    func partition(_ head: ListNode?, _ x: Int) -> ListNode? {
        var result: ListNode? = nil
        var big: ListNode? = nil
        var currentSmall: ListNode? = nil
        var currentBig: ListNode? = nil
        var current = head
        while current != nil {
            if current!.val < x {
                if result == nil {
                    result = current
                    currentSmall = current
                } else {
                    currentSmall?.next = current
                    currentSmall = current
                }
            } else {
                if big == nil {
                    big = current
                    currentBig = current
                } else {
                    currentBig?.next = current
                    currentBig = current
                }
            }
            current = current?.next
        }
        currentBig?.next = nil
        currentSmall?.next = big
        return result == nil ? big : result
    }
```

## Review
[Namespacing](https://nshipster.com/namespacing/)    


## Tip    
待补充

## Share
https://optshiftk.com/2012/04/04/draft-proposal-for-namespaces-in-objective-c/
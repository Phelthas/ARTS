## Algorithm

```
/// 83.删除排序链表中的重复元素
    func deleteDuplicates(_ head: ListNode?) -> ListNode? {
        guard let head = head else { return nil }
        var last = head
        var current = head.next
        while current != nil {
            if current!.val == last.val {
                current = current?.next
            } else {
                last.next = current
                last = current!
                current = current?.next
            }
        }
        last.next = nil
        return head
    }

```

## Review
https://stackoverflow.com/questions/15343122/what-is-inherited-in-xcodes-search-path-settings


## Tip    
https://stackoverflow.com/questions/4631878/how-to-set-iphone-uiview-z-index    
UIView的显示层级控制    
使用layer.zIndex 属性可以控制页面的层级，使其不受addSubview顺序的影响；    
需要注意的是，view的事件响应链还是按subView本身的顺序的；跟视觉上看到的会不一样！！！
    

## Share
https://pewpewthespells.com/blog/xcconfig_guide.html#VariableAssignment


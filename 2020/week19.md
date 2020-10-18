## Algorithm

```
/// 82.删除排序链表中的重复元素 II
    func deleteDuplicates2(_ head: ListNode?) -> ListNode? {
        if head?.next == nil {
            return head
        }
        
        let blank = ListNode(x: Int.min)
        blank.next = head
        
        var last = blank
        var start = head
        var current = start?.next
        
        while current != nil {
            if start!.val == current!.val {
                var temp = current?.next
                while temp != nil {
                    if temp!.val == start!.val {
                        temp = temp?.next
                    } else {
                        break
                    }
                }
                last.next = temp
                start = temp
                current = temp?.next
                
            } else {
                last = start!
                start = current
                current = current?.next
            }
        }
        return blank.next
        
    }

```

## Review
[Method Swizzling](https://nshipster.com/method-swizzling/)

## Tip    
https://stackoverflow.com/questions/28990545/cocoapods-no-arc-in-only-few-files    
CocoaPods的podspec文件中有个`requires_arc`参数
> `requires_arc` allows you to specify which source_files use ARC. This can either be the files which support ARC, or true to indicate all of the source_files use ARC.    
Files which do not use ARC will have the -fno-objc-arc compiler flag.     
The default value of this attribute is true.

但是现在我们一般的情况都是项目默认是arc的，只有个别文件使用了mrc，所以这个参数用起来就有点蛋疼了。    
还有有人想出了变通的方法，就是利用subspec
https://stackoverflow.com/questions/28990545/cocoapods-no-arc-in-only-few-files
```
non_arc_files = ['Classes/Frameworks/PGSQLKit/*.{h,m}',
                   'Classes/Frameworks/PGSQLKit/**/*.{h,m}',
                   'Classes/Frameworks/QRunLoopOperation/*.{h,m}']
  spec.exclude_files = non_arc_files
  spec.subspec 'no-arc' do |sna|
      sna.requires_arc = false
      sna.source_files = non_arc_files
  end
```
因为podspec还有个参数`default_subspecs`
> An array of subspecs names that should be used as preferred dependency. If not specified, a specification requires all of its subspecs as dependencies.

> You may use the value :none to specify that none of the subspecs are required to compile this pod and that all subspecs are optional.

即默认情况下所有的subspec都会作为依赖加入到podspec中，所以只需要把所有的mrc文件当做subspec中的文件就行了。
    

## Share
https://mp.weixin.qq.com/s?__biz=MzI2NjIzNTcyNA==&mid=2247491324&idx=1&sn=9296efbbe02e23070adf40d347624574&chksm=ea9064dfdde7edc9a6350a36c6879fa7d63ddcd6b6dade0eb3fb1e6881b3dd47a1f755e45b53&mpshare=1&scene=1&srcid=1014HxN129wvrpr9NVZbcaho&sharer_sharetime=1602641648464&sharer_shareid=f613c89c0e720e805f228eac65d9e675&version=3.0.31.2308&platform=mac&rd2werd=1#wechat_redirect

## Algorithm
```
/**
首先把数组排序，然后开始遍历；    
从第一个数开始遍历到倒数第三个，这是比不可少的，    
然后取两个指针，分别指向剩下的数组的第一个和最后一个，    
判断当前三个数的和与目标值的关系，计算出当前的最小diff，并保存起来，用于下次迭代的比较，
然后根据情况分别移动两个指针即可
*/
func threeSumClosest(_ nums: [Int], _ target: Int) -> Int {
        var array = nums.sorted()
        var diff = Int.max
        var result = 0
        for i in 0 ..< array.count - 2 {
            let a = array[i]
            
            var j = i + 1
            var k = array.count - 1
            while j < k {
                let b = array[j]
                let c = array[k]
                let tempSum = a + b + c
                if abs(tempSum - target) < diff {
                    diff = abs(tempSum - target)
                    result = tempSum
                }
                if tempSum > target {
                    k -= 1
                } else if tempSum < target {
                    j += 1
                } else {
                    return result
                }
            }
        }
        return result
    }
```

## Review
[#pragma](https://nshipster.com/pragma/)    
介绍如何用`#pragma`组织代码    
1，如果一个类重载了继承自其他类的某些方法，那这些被重载的方法可以用`#pragma className`标记一下    
2，如果一个类遵从了某个协议，那协议方法要用`#pragma protocolName`标记一下（如果标记的顺序和声明的顺序一致，会是额外加分项）    
可以用`-Wno-deprecated-implementations`取消掉使用废弃方法的warning    
可以用`#pragma clang diagnostic push/pop`让编译器忽略掉某些特定的warning    
例如：    
```
#pragma clang diagnostic push
#pragma clang diagnostic ignored "-Wdeprecated-implementations"
@implementation DeprecatedClass
…
@end
#pragma clang diagnostic pop
```


## Tip
给Associated Objects实现weak属性，关键是引入一个容器，这个容器只有一个weak的id属性，指向原本需要实现weak的对象，然后用`OBJC_ASSOCIATION_RETAIN_NONATOMIC`关联这个容器即可。

## Share
[浅谈Associated Objects](https://www.desgard.com/iOS-Source-Probe/Objective-C/Runtime/%E6%B5%85%E8%B0%88Associated%20Objects.html)
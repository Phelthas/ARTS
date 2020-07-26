
## Algorithm

```
/// 42.接雨水,这个算法的核心思路是：一块柱子能接水的量取决于它左右两边最高的柱子中较短的一个
    /// 这个算法是分别计算每个柱子能接到的雨水的量，再求和！！！
    func trap(_ height: [Int]) -> Int {
        let n = height.count
        if n <= 2 { return 0 }
        var leftArray = [Int](repeating:0, count: n) //leftArray是保存height[i]左边最大值的数组
        var rightArray = [Int](repeating:0, count: n)//rightArray是保存height[i]右边边最大值的数组
        var maxLeft = 0
        for i in 0 ..< n {
            maxLeft = max(maxLeft, height[i])
            leftArray[i] = maxLeft
        }
        
        var maxRight = 0
        for i in (0 ..< n).reversed() {
            maxRight = max(maxRight, height[i])
            rightArray[i] = maxRight
        }
        
        var result = 0
        for i in 1 ..< n - 1 {
            if leftArray[i - 1] <= 0 || rightArray[i + 1] <= 0 {
                continue
            }
            let temp = min(leftArray[i - 1], rightArray[i + 1]) - height[i]
            if temp > 0 {
                result += temp
            }
        }
        return result
    }
```

## Review
[Associated Objects](https://nshipster.com/associated-objects/)    
需要注意的其实是不要滥用，文章提到了这个应该作为最终的手段，不能为了用而用

## Tip
https://stackoverflow.com/questions/50552752/how-to-rebuild-development-pod-changes    
使用CocoaPods时，如果使用了`development pod`(podfile中使用`:path => 'xxx'`指定路径)，那有时候修改`development pod`中的代码，然后直接编译时，修改并不会体现出来，必须要clean一下才行，但clean的话会导致项目重新编译，工程比较大的时候编译编译太慢这就不能忍了。Stack Overflow上有大神给出了解决方案，就是上面这个链接，在EditScheme-Build中，点击加号，把需要每次都编译的`development pod`的target加进去即可。    
下面有其他回答说到CocoaPods1.8.0已经修复了这问题，我还没试过，有空可以试一下。

## Share
https://juejin.im/post/5eccceb9f265da76f30e4e13







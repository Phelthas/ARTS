## Algorithm
```
/// 367. 有效的完全平方数
    func isPerfectSquare(_ num: Int) -> Bool {
        if num == 1 { return true }
        var left = 0
        var right = num
        while left <= right {
            let mid = (left + right) / 2
            if num / mid == mid && num % mid == 0 {
                return true
            } else if num / mid < mid {
                right = mid - 1
            } else {
                left = mid + 1
            }
        }
        return false
    }
```

## Review
[Launch Arguments & Environment Variables](https://nshipster.com/launch-arguments-and-environment-variables/)    
介绍了一些Xcode启动时可以传的参数或者环境变量，貌似用的不是很多，但某些场景下可能很有用    


## Tip
NSAttributedString的attributeDict里面还有一个`NSShadowAttributeName`，可以设置为`NSShadow`类，可以用来设置字符串的阴影。    
甚至可以利用其属性实现字体模糊的效果（设置真字符串的的颜色透明，而阴影颜色不透明，阴影可以设置shadowBlurRadius属性）

## Share
[iOS图像最佳实践总结](https://juejin.im/post/5c84bd676fb9a049e702ecd8)
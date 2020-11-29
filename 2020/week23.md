## Algorithm

```
   /// 96. 不同的二叉搜索树,关键是：总个数=分别以各个数为根节点的二叉搜索树的综合
    /// 而以某个数为根节点的二叉树的个数 = 其左边子树的个数*右边子树的个数
    func numTrees(_ n: Int) -> Int {
        if n == 0 { return 1 }
        if n == 1 { return 1 }
        var result = [Int](repeating: 0, count: n + 1)
        result[0] = 1
        result[1] = 1
        for i in 2 ... n  {
            
            for j in 1 ... i {
                result[i] += result[j - 1] * result[i - j]
            }
            
        }
        return result[n]
    }
```

## Review
[Unit Testing](https://nshipster.com/unit-testing/)


## Tip    
iOS中使用自定义字体，可以参考https://www.jianshu.com/p/61168d610531，    
需要注意的是，使用`[UIFont fontWithName:fontName size:40];`的时候，这个fontName必须是字体的`PostScriptName`，而不是字体包的文件名。    
在mac系统上，可以通过mac上自带的字体册查看，直接双击字体包，点击安装，然后点击左上角info按钮即可。    
`PostScriptName`的具体介绍，可以参考https://www.douban.com/note/771217330/


## Share
https://www.jianshu.com/p/61168d610531

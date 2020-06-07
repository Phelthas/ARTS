## Algorithm
```
/// 6. Z字形变换
    func convert(_ s: String, _ numRows: Int) -> String {
        if numRows == 1 { return s }
        var array = [Character](s)
        let n = array.count
        var matrix = [[Character]]()
        for i in 0 ..< numRows {
            let a = [Character](repeating: "0", count: n)
            matrix.append(a)
        }
        
        var index = 0
        var i = 0
        var j = 0
        var isVertical = true
        while index < array.count {
            let current = array[index]
            index += 1
            matrix[i][j] = current
            if isVertical {
                i += 1
                if i == numRows {
                    i -= 2
                    j += 1
                    isVertical = false
                }
            } else {
                i -= 1
                j += 1
                if i < 0 {
                    i += 2
                    j -= 1
                    isVertical = true
                }
            }
        }
        array.removeAll()
        for i in 0 ..< numRows {
            for j in 0 ..< n {
                let a = matrix[i][j]
                if a != "0" {
                    array.append(a)
                }
            }
        }
        return String(array)
    }
```

## Review
https://nshipster.com/xcode-snippets/    
用Xcode的snippet简化输入的方法，这个是很早之前就有的功能了，但貌似好多程序猿们都还没有把它利用起来。理论上我们程序猿应该时刻想着如何提高自己敲代码的效率，对于这种能减少重复劳动的方法应该尽早利用起来。我自己还专门在github上建了个项目([LXMSnippets](https://github.com/Phelthas/LXMSnippets))保存自己常用的snippets，方便自己重装系统或者换电脑的时候能瞬间把snippet也带过来。


## Tip
**在Xcode中创建子工程及依赖**     
假设存在一个主工程mainProject，一个子工程subProject用于生成a文件，主工程mainProject需要依赖subProject编译出来a文件`libSubProject.a`。那让mainProject每次都可以用最新编译出来的a文件的设置方式如下：    
1，将子工程的xcodeproj文件拖入到主工程中；（是否Copy Files无所谓，因为主工程真正用到的是编译出来的a文件，但子工程的路径要与主工程相对固定）    
2，在主工程的`Build Phases - Dependencies`中点击+号，选择子工程的`libSubProject.a`;这一步是设置主工程依赖子工程的编译结果，使主工程每次编译时都会先去编译子工程。    
3，在主工程的`Build Phases - Link Binary With Libraries`中点击+号，选择子工程的`libSubProject.a`;这一步是设置主工程链接子工程的编译结果。    
4，在主工程的`Build Settings - Search Paths - Header Search Paths`中点击+号，填入`$(TARGET_BUILD_DIR)`,并设置为`recursive`; 这一步是设置主工程的头文件搜索路径，`$(TARGET_BUILD_DIR)`是工程编译结果的路径，子工程的编译结果也会在这儿；设置`recursive`是为了递归搜索这个目录下所有文件夹，如果设置`non-recursive`就需要具体到头文件的路径。    
5，如果子工程中有category，需要在主工程的的`Build Settings - Linking - Other Link Flags`中点击+号，填入`$(TARGET_BUILD_DIR)/xxx.a`,即具体的a文件路径；    

以上，然后就可以在主工程中import子工程的头文件，尽情使用了~    
    
PS: 一般是子工程作为一个公共基础库被多个项目公用时，才会用到这种方式，这是Xcode原生支持的集成方式，但这已经是很落后很落伍的方式了，现在应该都是使用CocoaPods来集成子工程了吧。不过了解一下也好，能知道CocoaPods帮我们做了点什么。




## Share
https://juejin.im/post/5d67b720f265da039a289bb4

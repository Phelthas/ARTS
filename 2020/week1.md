## Algorithm
```
/// 9 回文数
func isPalindrome(_ x: Int) -> Bool {
        if x < 0 {
            return false
        }
        var one = [Int]()
        var two = [Int]()
        var x = x
        while x != 0 {
            let a = x % 10
            one.append(a)
            two.insert(a, at: 0)
            x = x / 10
        }
        return one == two
}
```

## Review
[Xcode Build Configuration Files](https://nshipster.com/xcconfig/)    
     
核心思想是：  配置和代码应该严格区分开来，Xcode提供了 `xcconfig` 文件来达到这一效果    
1, https://xcodebuildsettings.com/ 上有Xcode支持的所有设置的文档    
2, 添加配置而不是修改配置，用`$(inherited) `    
Xcode赋值给`inherited values`时顺序如下
* Platform Defaults
* Xcode Project xcconfig File
* Xcode Project File Build Settings
* Target xcconfig File
* Target Build Settings    

3, 空格用来区分字符串和路径中的元素，所以如果某个元素包含了空格，需要用"将这个元素包起来    







## Tip
mac中，如何在当前文件夹打开终端（Terminal）    
1）系统自带服务，在SystemPreference-Keyboard-Shortcuts-Services 中勾选`New Terminal at Folder`，然后右键单击某个文件夹时，就会出现`New Terminal at Folder`选项，单击机会新建一个Terminal窗口，并cd到这个文件夹    
2) 使用大神写的工具[https://github.com/jbtule/cdto](https://github.com/jbtule/cdto)，可以直接在文件夹的工具栏上加一个按钮，点一下就行！

## Share
https://juejin.im/post/5e5fc16df265da575155723b

## Algorithm
```
//27. 移除元素
    func removeElement(_ nums: inout [Int], _ val: Int) -> Int {
        guard nums.count > 0 else { return 0 }
        var i = 0
        var last = nums.count - 1
        while i <= last {
            if nums[i] == val {
                nums[i] = nums[last]
                nums[last] = 0
                last -= 1
            } else {
                i += 1
            }
        }
        return i
    }
```

## Review
[Xcode and XCFrameworks — new format of packing frameworks](https://medium.com/trueengineering/xcode-and-xcframeworks-new-format-of-packing-frameworks-ca15db2381d3)    
XCFrameworks是苹果推出的新的打包方式，可以将所有平台和架构下的库文件打包成一个`.xcframeworks`后缀的包。  
跟现在的framework方式相比，它有几个明显的优势：     
1，把所有平台和架构的包封装成一个单独的包；    
2，链接xcframewrok格式的包时，所有平台和架构只需要单独依赖这一个包即可    
3，不需要创建`fat/universal Framework`    
4, 上传最终app到App Store的时候，不用移除`x86_64`架构的包    

PS：现在还必须用脚本调用命令行工具xcodebuild，用Xcode11才可用的关键字 `-create-xcframework`    


## Tip
**如何创建一个xcframework**     
1，将`build setting`中`build libraries for distribution`选项设置为 YES; (这是一个Xcode11新增的选项)    
2，针对不同的平台和架构编译工程; 这里介绍了用xcodebuild命令行的方式
```
# iOS device
xcodebuild archive \
-scheme XCFrameworkExample \
-archivePath "./build/ios.xcarchive" \
-sdk iphones \
SKIP_INSTALL=NO
# iOS simulator
xcodebuild archive \
-scheme XCFrameworkExample \
-archivePath "./build/ios_sim.xcarchive" \
-sdk iphonesimulator \
SKIP_INSTALL=NO
```
3，将编译好的.framework 打包成 xcframework    
```
xcodebuild -create-xcframework \
-framewrok "./build/ios.xcarchive/Products/Library/Frameworks/XCFrameworkExample.framework" \ 
-framewrok "./build/ios_sim.xcarchive/Products/Library/Frameworks/XCFrameworkExample.framework" \ 
-output "./build/XCFrameworkExample.xcframework"
```

PS:不看不知道，一看吓一跳~ 这是苹果2019年4月推出的新功能，这篇文章是2019年11月写的，而我现在2020年6月才知道。。。真是学如逆水行舟，不进则退呀！


## Share
[与程序员相关的CPU缓存知识](https://coolshell.cn/articles/20793.html)
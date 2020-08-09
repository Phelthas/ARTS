
## Algorithm

```
/// 58. 最后一个单词的长度 
    func lengthOfLastWord(_ s: String) -> Int {
        guard s.count > 0 else { return 0 }
        let array = [Character](s)
        var i = array.count - 1
        while i >= 0 {
            if array[i] == " " {
                i -= 1
                if i < 0 {
                    return 0
                }
            } else {
                var j = i - 1
                while j >= 0 {
                    if array[j] == " " {
                        return i - j
                    } else {
                        j -= 1
                    }
                }
                return i - j
            }
        }
        return array.count
    }
```

## Review
[Benchmarking](https://nshipster.com/benchmarking/)    
 CACurrentMediaTime()    
 ```
 uint64_t t = dispatch_benchmark(iterations, ^{
    @autoreleasepool {
        NSMutableArray *mutableArray = [NSMutableArray array];
        for (size_t i = 0; i < count; i++) {
            [mutableArray addObject:object];
        }
    }
});
NSLog(@"[[NSMutableArray array] addObject:] Avg. Runtime: %llu ns", t);
 ```
## Tip
sourceTree 给某个repo设置代理    
* 打开需要设置代理的仓库
* 选择 仓库 > 仓库设置 ，会弹出仓库设置面板
* 选择 远程仓库 > 编辑配置文件
* 在打开的 config 文本中添加代理设置

```
[http]
        proxy = 127.0.0.1：xxxxx
```
Copy
* 保存    
其实就是编译这个repo的config文件而已，跟直接在该repo下的 .git文件夹下面修改config文件是一样的

## Share
[形象展示傅里叶变换](https://www.bilibili.com/video/av19141078/)   
看到14:25的时候不由自主的 哇 了一声~








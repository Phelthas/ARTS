

## Algorithm

```
// 77
func combine(_ n: Int, _ k: Int) -> [[Int]] {
        var array = [Int]()
        for i in 1 ... n {
            array.append(i)
        }
        var result = [[Int]]()
        
        func helper(temp: [Int], start: Int) {
            if start > n {
                return
            }
            if temp.count == k {
                result.append(temp)
            } else {
                for i in start ..< array.count {
                    let current = array[i]
                    var newTemp = temp
                    newTemp.append(current)
                    helper(temp: newTemp, start: i + 1)
                }
            }
        }
        helper(temp: [Int](), start: 0)
        return result
    }

```

## Review
[objc_msgSend's New Prototype](https://www.mikeash.com/pyblog/objc_msgsends-new-prototype.html)    
老高端了   
介绍了iOS14中 `objc_msgSend`的新的函数原型，强烈建议细读。
核心的思想是，把objc_msgSend的修改成了一个明显错误的Prototype，这样的话，使用的时候，必须显示的将其转换为正确的类型，否则调用就会报错；     
这样就可以在编译阶段就发现可能存在的问题，而不是等函数出错了都不知道错在了哪里。


## Tip    
对于死循环之类造成的内存不停增大直到爆掉，常规方法可能不好调试，可以用instrument开allocation来看；    
选中callTree，然后选hide system library，看看详情区哪个方法占用的内存最大，那个地方大概率有死循环了。

## Share
https://git-scm.com/docs/git-worktree







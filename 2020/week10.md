
## Algorithm

```
/// 47 全排列 II  跟40有点像
func permuteUnique(_ nums: [Int]) -> [[Int]] {
    var array = nums.sorted()
    var n = nums.count
    var result = [[Int]]()
    func helper(remain: [Int], temp: [Int]) {
        if temp.count == n {
            result.append(temp)
        } else {
            for i in 0 ..< remain.count {
                if 0 == i || remain[i] != remain[i - 1] {
                    var newRemain = remain
                    let current = newRemain.remove(at: i)
                    var newTemp = temp
                    newTemp.append(current)
                    helper(remain: newRemain, temp: newTemp)
                }
            }
        }
    }
    helper(remain: array, temp: [Int]())
    return result
}
```

## Review


## Tip
使用`git lfs prune`命令的时候，命令行有时候会卡住
我这儿的具体原因是 最大文件打开数的限制 比lfs需要打开的文件数要小，就是 open file descriptors 设置太小了。。。 
命令行输入 ulimit -a 可以查看，默认值貌似是256
输入 ulimit -n 2048 可以将其设置为2048

参考 [stackoverflow](https://superuser.com/questions/302754/increase-the-maximum-number-of-open-file-descriptors-in-snow-leopard/1171023#1171023)上的答案 

## Share
https://zhuanlan.zhihu.com/p/75735751
理解YUV这个格式，注意文中有错误的地方，下面评论中已经指出来了。








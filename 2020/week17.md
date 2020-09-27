## Algorithm

```
/// 80.删除排序数组中的重复项 II
    func removeDuplicates(_ nums: inout [Int]) -> Int {
        guard nums.count > 2 else { return nums.count }
        var index = 2
        var last1 = nums[0]
        var last2 = nums[1]
        
        for i in 2 ..< nums.count {
            let current = nums[i]
            if last1 == last2 && last2 == current {
                
            } else {
                nums[index] = current
                index += 1
                last1 = last2
                last2 = current
            }
        }
        return index
    }

```

## Review
https://spin.atomicobject.com/2016/06/26/parallelize-development-git-worktrees/     
介绍Git的worktree功能的，用了一下以后感觉确实很好用，尤其是在git仓库很大的时候。     
切换分支后，部分编译缓存会失效，编译会慢很多。用了worktree以后，切换分支变成了切换文件夹的操作，原来的编译缓存完全没变。     
效率大大提升！！！


## Tip    
CALayer的隐式动画
当直接修改CALayer的标为animatable的属性时，系统不是瞬间就将其变过来的，而是会经历一个动画，就是系统的隐式动画。    
如果想要关闭这个隐式动画，主要有两种方式：   
1. 使用CATransaction并将DisableActions设置为YES；    
注意不是CATransition！！！别看错了，我因为没看清这个被自己坑了半天。。。    
     需要注意的是，这个方法仅针对这次修改有效，如果之后再普通的修改属性，还是会触发隐式动画
```
    [CATransaction begin];
    [CATransaction setValue:@(true) forKey:kCATransactionDisableActions];
    //在这里修改属性 不会触发隐式动画 
    [CATransaction commit];
```
2. 将对应属性的action设置为nil；    
注意：这种方法是针对整个实例生效的，设置之后，之后随便修改属性，都不会触发隐式动画
```
//1 如果要自定义类，且这个类的所有实例都要忽略某个属性的隐式动画，可以用这几句代码
+ (id<CAAction>)defaultActionForKey:(NSString *)event {
    if ([event isEqualToString:@"contentsRect"]) {
        return (id<CAAction>)[NSNull null];
    }
    return [super defaultActionForKey:event];
}

//2 如果仅仅是某个实例要忽略，可以用这一句代码
someLayer.actions = @{@"contentsRect" : [NSNull null]};    
```
    

## Share
http://yulingtianxia.com/blog/2019/09/01/App-Order-Files/


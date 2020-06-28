## Algorithm
```
/// 11. 盛最多水的容器
    func maxArea(_ height: [Int]) -> Int {
        var result = 0
        var left = 0
        var right = height.count - 1
        while left < right {
            let m = (right - left) * min(height[left], height[right])
            result = max(result, m)
            if height[left] <= height[right] {
                left += 1
            } else {
                right -= 1
            }
        }
        return result
    }
```

## Review
[Git LFS](https://www.atlassian.com/git/tutorials/git-lfs)
主要介绍了git-lfs的基本使用方法，简单介绍了其原理，简单来说，git-lfs的机制有点像我们上传图片或者视频，先把文件上传到服务器，拿到一个文件url，本地只保存这个url，需要显示或者播放的时候再根据这个url去加载。git-lfs是把大文件上传到服务端以后，git仓库保存了一个指针文件，指针文件指向真正的大文件，在checkout的时候，才真正把大文件下载回来。


## Tip
用`git lfs ls-files -l`可以显示出所有git-lfs管理的文件的id，    
用`git lfs push --object-id origin xxx`可以单独将某个id的大文件直接push到远程 其中xxx是报错的不存在的object的id，这两个命令配合起来，可以解决[xxx]Object does not exist on the server的问题

## Share
[详解 Git 大文件存储（Git LFS）](https://zhuanlan.zhihu.com/p/146683392)
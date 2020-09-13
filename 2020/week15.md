

## Algorithm

```
// 74. 搜索二维矩阵 见过的最复杂的边界条件问题
    func searchMatrix(_ matrix: [[Int]], _ target: Int) -> Bool {
        let m = matrix.count
        if m == 0 { return false }
        let n = matrix[0].count
        if n == 0 { return false }
        var colum = [Int]()
        for array in matrix {
            colum.append(array[0])
        }
        
        var left = 0
        var right = colum.count - 1
        var row = 0
        while left <= right {
            // Prevent (left + right) overflow
            let mid = left + (right - left) / 2
            if colum[mid] == target {
                return true
            } else if colum[mid] > target {
                right = mid - 1
            } else {
                left = mid + 1
            }
        }
        row = min(left, right)
        if row < 0 { return false }
        
        
        let array = matrix[row]
        if array.count == 1 {
            return array[0] == target
        }
        left = 0
        right = array.count - 1
        while left <= right {
            // Prevent (left + right) overflow
            let mid = left + (right - left) / 2
            if array[mid] == target {
                return true
            } else if array[mid] > target {
                right = mid - 1
            } else {
                left = mid + 1
            }
        }
        return false
        
    }

```

## Review
[Extended File Attributes](https://nshipster.com/extended-file-attributes/)    
介绍metadata的，感觉用处不大


## Tip    
UICollectionView 的 `- (void)reloadItemsAtIndexPaths:(NSArray<NSIndexPath *> *)indexPaths;`方法和`- (void)reloadData;`的机制并不一样；    
他们都会触发cellForRow方法，但`reloadItemsAtIndexPaths`会触发系统的隐式动画，导致写在cellForRow中的UIView动画不会执行，    
而`reloadData`不会触发系统的隐式动画，写在cellForRow中的UIView动画可以执行。    

```
    // 关闭系统的隐式动画
    [UIView performWithoutAnimation:^{
        [self.collectionView reloadItemsAtIndexPaths:@[[NSIndexPath indexPathForItem:model.index inSection:0]]];
    }];

    // 用UIView动画覆盖collectionView的隐式动画，貌似只能修改时间
    [UIView animateWithDuration:1 animations:^{
        [self.collectionView reloadItemsAtIndexPaths:@[[NSIndexPath indexPathForItem:model.index inSection:0]]];
    }];
```
如果想要自定义动画，就不能使用UIView动画，可以在cellForRow的时候，添加一个CAAnimation动画；

## Share
https://www.kancloud.cn/digest/xing-designpattern/143719








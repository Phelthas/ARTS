## Algorithm

```
/*
四数之和，算法同三数之和类似，关键是左右两个指针的前后移动
*/
func fourSum(_ nums: [Int], _ target: Int) -> [[Int]] {
        
        var array = nums.sorted()
        var result = [[Int]]()
        guard nums.count >= 4 else { return result }
        
        for i in 0 ..< nums.count - 3 {
            for j in i + 1 ..< nums.count - 2 {
                var left = j + 1
                var right = nums.count - 1
                while left < right {
                    let sum = array[i] + array[j] + array[left] + array[right]
                    if sum == target {
                        let temp = [array[i], array[j], array[left], array[right]]
                        if !result.contains(temp) {
                            result.append(temp)
                        }
                        left += 1
                        right -= 1
                    } else if sum > target {
                        right -= 1
                    } else {
                        left += 1
                    }
                }
            }
        }
        
        return result
    }
```

## Review
https://nshipster.com/at-compiler-directives/
介绍了一些@指令，貌似用处不是很大

## Tip
@compatibility_alias：允许现有类有不同的名称作为别名。
比如 PSTCollectionView 使用了 @compatibility_alias 来显著提高对 UICollectionView 向后兼容的直接替换的使用体验：

// 允许代码使用 UICollectionView 如同它可以在iOS SDK 5使用一样。
// https://developer.apple.com/legacy/mac/library/#documentation/DeveloperTools/gcc-3.3/gcc/compatibility_005falias.html
#if __IPHONE_OS_VERSION_MAX_ALLOWED < 60000
@compatibility_alias UICollectionViewController PSTCollectionViewController;
@compatibility_alias UICollectionView PSTCollectionView;
@compatibility_alias UICollectionReusableView PSTCollectionReusableView;
@compatibility_alias UICollectionViewCell PSTCollectionViewCell;
@compatibility_alias UICollectionViewLayout PSTCollectionViewLayout;
@compatibility_alias UICollectionViewFlowLayout PSTCollectionViewFlowLayout;
@compatibility_alias UICollectionViewLayoutAttributes     PSTCollectionViewLayoutAttributes;
@protocol UICollectionViewDataSource <PSTCollectionViewDataSource> @end
@protocol UICollectionViewDelegate <PSTCollectionViewDelegate> @end
#endif

## Share
http://www.52im.net/thread-232-1-1.html


## Algorithm

```
/// 64. 最小路径和
    func minPathSum(_ grid: [[Int]]) -> Int {
        let m = grid.count
        if m == 0 { return 0 }
        let n = grid[0].count
        if n == 0 { return 0 }
        var matrix = grid
        for i in 1 ..< m {
            matrix[i][0] = matrix[i - 1][0] + matrix[i][0]
        }
        for j in 1 ..< n {
            matrix[0][j] = matrix[0][j - 1] + matrix[0][j]
        }
        
        for i in 1 ..< m {
            for j in 1 ..< n {
                matrix[i][j] = min(matrix[i - 1][j], matrix[i][j - 1]) + matrix[i][j]
            }
        }
        return matrix[m - 1][n - 1]
    }
```

## Review
[Equality](https://nshipster.com/equality/)


## Tip    
待补充

## Share
[程序员如何把控自己的职业](https://coolshell.cn/articles/20977.html)









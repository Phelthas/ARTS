## Algorithm

```
/// 89. 格雷编码 
    func grayCode(_ n: Int) -> [Int] {
        var matrix = [[Int]]()
        var temp = [Int](repeating: 0, count: n)
        matrix.append(temp)
        
        func helper(array: [Int]) -> [Int] {
            
            for i in (0 ..< array.count).reversed() {
                let current = array[i]
                var result = array
                result[i] = current == 0 ? 1 : 0
                if !matrix.contains(result) {
                    matrix.append(result)
                    return result
                }
            }
            return [Int]()
        }
        
        while temp.count != 0 {
            temp = helper(array: temp)
        }
        var result = [Int]()
        for array in matrix {
            var temp = 0
            for i in 0 ..< array.count {
                temp += array[i] * 1 << i
            }
            result.append(temp)
        }
        return result
        
    }
```

## Review
[Object Subscripting](https://nshipster.com/object-subscripting/)

## Tip    
待补充

## Share
[Objective-C Direct Methods](https://nshipster.com/direct/)    
[Dissecting objc_msgSend on ARM64](https://www.mikeash.com/pyblog/friday-qa-2017-06-30-dissecting-objc_msgsend-on-arm64.html)
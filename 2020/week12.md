
## Algorithm

```
/// 59. 螺旋矩阵 II
    func generateMatrix(_ n: Int) -> [[Int]] {
        var result = [[Int]]()
        for _ in 0 ..< n {
            let temp = [Int](repeating: 0, count: n)
            result.append(temp)
        }
        
        var k = 0
        var i = 0
        var j = 0
        var current = 1
        
        while k <= (n - 1) / 2 {
            i = k
            for temp in k ..< n - k {
                result[i][temp] = current
                current += 1
            }
            if current > n * n {
                break
            }
            
            j = n - 1 - k
            for temp in k + 1 ..< n - k {
                result[temp][j] = current
                current += 1
            }
            if current > n * n {
                break
            }
            
            i = n - 1 - k
            for temp in (k ..< n - 1 - k).reversed() {
                result[i][temp] = current
                current += 1
            }
            if current > n * n {
                break
            }
            
            j = k
            for temp in (k + 1 ..< n - 1 - k).reversed() {
                result[temp][j] = current
                current += 1
            }
            if current > n * n {
                break
            }
            k += 1
        }
        return result
        
    }
```

## Review
[C Storage Classes](https://nshipster.com/c-storage-classes/)        
A static variable inside a method or function retains its value between invocations.
A static variable declared globally can be called by any function or method, so long as those functions appear in the same file as the static variable. The same goes for static functions.    
`objects that may be expensive to create, such as formatters`    
Whereas static makes functions and variables globally visible within a particular file, extern makes them visible globally to all files.
```
AppDelegate.h
extern NSString * const kAppErrorDomain;
AppDelegate.m
NSString * const kAppErrorDomain = @"com.example.yourapp.error";
```

```
TransactionStateMachine.h
typedef NS_ENUM(NSUInteger, TransactionState) {
    TransactionOpened,
    TransactionPending,
    TransactionClosed,
};

extern NSString * NSStringFromTransactionState(TransactionState state);
TransactionStateMachine.m
NSString * NSStringFromTransactionState(TransactionState state) {
  switch (state) {
    case TransactionOpened:
      return @"Opened";
    case TransactionPending:
      return @"Pending";
    case TransactionClosed:
      return @"Closed";
    default:
      return nil;
  }
}

```

## Tip    
待补充

## Share
https://charlesliuyx.github.io/2018/02/18/%E3%80%90%E7%9B%B4%E8%A7%82%E8%AF%A6%E8%A7%A3%E3%80%91%E8%AE%A9%E4%BD%A0%E6%B0%B8%E8%BF%9C%E5%BF%98%E4%B8%8D%E4%BA%86%E7%9A%84%E5%82%85%E9%87%8C%E5%8F%B6%E5%8F%98%E6%8D%A2%E8%A7%A3%E6%9E%90/









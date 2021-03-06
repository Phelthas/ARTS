## Algorithm

```
/// 39. 组合总和 
    func combinationSum(_ candidates: [Int], _ target: Int) -> [[Int]] {
        
        var result = [[Int]]()
        var array = candidates.sorted()
        
        func helper(array:[Int], start: Int, temp: [Int], sum: Int) {
            if sum == target {
                result.append(temp)
                return
            } else if sum > target {
                return
            } else {
                for i in start ..< array.count {
                    var temp = temp
                    temp.append(array[i])
                    helper(array: array, start: i, temp: temp, sum: sum + array[i])
                }
            }
            
        }
        helper(array: array, start: 0, temp: [Int](), sum: 0)
        return result
    }
```

## Review
待补充

## Tip
待补充

## Share
[排名在前 1% 的高中生是靠天赋还是靠努力](https://daily.zhihu.com/story/9725797)    
这篇文章比较长，最后才知道这是作者大一大二的时候写的，有些观点跟我最近一些自己的想法有些不谋而合的感觉，而我现在大学毕业都10年了。。。    

小时候爸妈或邻近都说我很聪明，但小学的时候我的成绩基本一直是中游水平而已，印象中班里前几名经常都是双100的，而我貌似从来没考过100分，都是90分左右。但我是比较听话的那种，老师让上课认真听讲，我就认真听讲，让按时做作业，我就按时做作业，其他也没怎么努力过，到四五年级的时候，我大概是前20名的成绩吧（那时候一个班貌似80人来着？记不太清了)。    

初中我也一样，只是各门课都认真听讲，按时做完作业而已，然后考试的时候也是跟小学一样，各门课90分左右，但没想到的是，就这我已经是班里前10名了。。。因为初中学的科目多了点，语数外理化生政史地，具体是啥已经忘了，我各门课成绩比较平均，总分就上去了，而有些小学时候能考双100的同学，可能某一门课拖后腿，总分就下去了。。。初中三年，我还是听话的度过，上课认真听讲，下课完成作业，老师让买辅导书就买，也没参加过什么辅导班，我也成绩也基本稳定在前10，印象中我的最好成绩是第三名。    

高中我勉强进了我们县最好的高中，大家都是原来初中的佼佼者，我入学成绩在班里面好像排20+来着，我的学习方式一直没变，一个学期过去，我大概到了前20的名次，但后半学期开始有点因为玩而分心。（慢慢的我感觉自己的数学学起来有点吃力了，没之前那么轻松。有些东西老师上课时没讲明白，我没能完全搞懂，然后课后我又没有去复习把它搞透彻，日积月累下来，就有点吃不消了；然后高中老师也不再布置必须完成的作业了，要靠自觉去做辅导书上的题，我一直以来完作业就去玩的习惯就受到了不小的挑战，把所有科目所有习题都做完貌似不太可能，但只挑一部分我又不知道该怎么挑）高二延续了高一的状态，分心更厉害了一些。等到高二结束的时候，我的成绩还是前20。高三大家貌似都很拼命，我的努力程度跟其他比起来估计也只是中等水平，成绩的话波动就比较大了，好的时候能到前10，差的时候貌似也到过30左右。   
最后高考考的比较差，就不说了。
然后大学四年平淡无奇，又读了三年研究生，这就是后话了。    

回头想想自己这些年上学的经历的话，论智商，我肯定不是最顶尖的那种，高中的时候我已经隐约能感觉出来，有些同学比确实我聪明，有些同学就没我聪明，这里说的聪明不是指成绩，而就是我自己的感觉，应该是很多微小的事件积累出来的一种总的印象。论成绩，我初中可以算优秀，高中只能算中等偏上。而且高中因为我贪玩分心（大话西游，CS，魔兽争霸~因为这些影响了学习，也是因为这些后来成了程序猿，难道这是命运石之门的安排？），没能一心一意放到学习上，所以我自我感觉如果我高中能更专心一些，成绩应该也能达到优秀的水准。    
以我为参照的话，我身边的比我成绩好的人，大部分是两种情况，一种是我感觉比我聪明，努力程度跟我差不多的，一种是跟我聪明程度差不多，但比我努力或者比我专心的。那种明显比我聪明但不怎么努力就比我成绩好的我印象中是没有，那种比我聪明一点但成绩比我差很多的倒是大把。。。  

扯了这么多，总的来说，我感觉自己还是受益于一个比较好的学习习惯。而且现在工作的时间越长，越感觉到习惯的重要性。在职场中，有没有主动去学习的习惯，完全就是两个发展方向。所以，我还是比较认同上文中的一些观点的。









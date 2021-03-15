## 信息卡片
- 题目编号：38. 
- 题目名称：字符串的排列
- 更新时间：2021-03-15
- 原题链接：[https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)
- Tag：回溯算法dfs



### 中文题目
```
输入一个字符串，打印出该字符串中字符的所有排列。

 

你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。

 

示例:

输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]
 

限制：

1 <= s 的长度 <= 8

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```


## 回溯算法
**参考代码**
```java
class Solution {

    List<String> list;
    char[] c;

    public String[] permutation(String s) {
        list=new  ArrayList<>();
        c=s.toCharArray();
        dfs(0);
        return list.toArray(new String[list.size()]);
    }

    private void dfs(int idx){
        if(idx==c.length){
            // 终止条件
            list.add(String.valueOf(c));
            return;
        }
        Set<Character> set=new HashSet<>();
        for(int i=idx;i<c.length;i++){
            if(set.contains(c[i])) continue;// 剪枝
            
            set.add(c[i]);//新枝
            swap(i,idx);//交换尝试
            dfs(idx+1);//下层递归
            swap(i,idx);//还原
        }
    }

    private void swap(int a,int b){
        char temp=c[a];
        c[a]=c[b];
        c[b]=temp;
    }

}
```



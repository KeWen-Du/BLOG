# 剑指OFFER
花了一周的时间在牛客上刷完了剑指offer，每天复习两道直到刷完第二次
### 1.二叉搜索树的后序遍历序列
> 输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历的结果。如果是则输出Yes,否则输出No。假设输入的数组的任意两个数字都互不相同。

```java
public class Solution {
    //递归
    public boolean VerifySquenceOfBST(int [] sequence) {
        if(sequence==null|sequence.length==0)return false;
        return verify(sequence,0,sequence.length-1);
    }
    private boolean verify(int[] seq,int i,int j){
        if(j-i<=1)return true;
        //记录节点值
        int rootVal = seq[j];
        int index = i;
        //确定左子树的序列，index移动到右子树最左边
        while(index<j&&seq[index]<rootVal)
            index++;
        //遍历右子树，确定是否都大于该节点值
        for(int k = index;k<j;++k)
            if(seq[k]<rootVal)return false;
        //递归遍历左右子树
        return verify(seq,0,index-1)&&verify(seq,index,j-1);
    } 
}
```
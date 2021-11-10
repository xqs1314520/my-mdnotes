# 最长公共子序列

问题描述：输入两个序列，比较两个序列并输出最长公共子序列，且不要求连续元素。

利用动态规划，有一个公式。L[i][j]需要一个二维数组。记录公共子序列的个数。

```python

def longest_common_subsequence(x:str,y:str):
    assert x is not None
    assert y is not None
    #获取xy的长度，并在后续的循环中使用
    m=len(x)
    n=len(y)
    L=[[0]*(n+1) for _ in range(m+1)]  #创建一个二维数组，创建方式
    for i in range(1,m+1):
        for j in range(1,n+1):
            if x[i-1]==y[j-1]:
                match=1
            else:
                match=0
            L[i][j]=max(L[i-1][j],L[i][j-1],L[i-1][j-1]+match)   #注意位置，在及时更像Lij

    return L[m][n]  #注意返回值

a='abcdef'
b='cdefg'
ln=longest_common_subsequence(a,b)
print(ln)

```

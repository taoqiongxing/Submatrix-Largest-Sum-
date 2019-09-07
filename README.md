# Submatrix-Largest-Sum-
最大子矩阵

牛课网题目链接：https://www.nowcoder.com/questionTerminal/a5a0b05f0505406ca837a3a76a5419b3

思路：每读取一个输入，假设当前mij元素位于i行j列，则计算i*j的矩阵内的虽大子矩阵的和。

数据读取完毕即求的最大和。

    n=int(input())#矩阵大小为n*n
    matrix1=[[0]*n for _ in range(n)]#构造行与行之间的求和矩阵matrix1，大小为n*n，初始化为0
    res=-127
    for i in range(n):
        line=list(map(int,input().split()))#读取矩阵第i行
       temp=[]
        for j in range(i+1):#第0行到当前行i
            t=[]
            for k in range(n):
              matrix1[j][k]+=line[k]#求和矩阵matrix1中，每个元素等于从当前元素开始到到该列最后一个元素的和sum(matrix[i:][j])
                if k==0:
                 t.append(matrix1[j][k])
                else:
                    t.append(max(matrix1[j][k],matrix1[j][k]+t[k-1]))
          temp.append(max(t))#矩阵matrix1中每行的最连续元素和
      res=max(res,max(temp))#当前i*n矩阵中的最大子矩阵和
    print(res)

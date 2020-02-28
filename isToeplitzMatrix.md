如果一个矩阵的每一方向由左上到右下的对角线上具有相同元素，那么这个矩阵是托普利茨矩阵。

给定一个 M x N 的矩阵，当且仅当它是托普利茨矩阵时返回 True。

示例 1:

输入: 
matrix = [
  [1,2,3,4],
  [5,1,2,3],
  [9,5,1,2]
]
输出: True
解释:
在上述矩阵中, 其对角线为:
"[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]"。
各条对角线上的所有元素均相同, 因此答案是True。

示例 2:

输入:
matrix = [
  [1,2],
  [2,2]
]
输出: False
解释: 
对角线"[1, 2]"上的元素不同。

说明:

     matrix 是一个包含整数的二维数组。
    matrix 的行数和列数均在 [1, 20]范围内。
    matrix[i][j] 包含的整数在 [0, 99]范围内。

进阶:

    如果矩阵存储在磁盘上，并且磁盘内存是有限的，因此一次最多只能将一行矩阵加载到内存中，该怎么办？
    如果矩阵太大以至于只能一次将部分行加载到内存中，该怎么办？

int compare(const void* min, const void* max){
    return (*(int*)max > *(int*)min);
}
bool isToeplitzMatrix(int** matrix, int matrixSize, int* matrixColSize){
    int a[matrixSize+*matrixColSize];
    int u=0,p=0,i,j,m,l;
    memset(a,-1,matrixSize+*matrixColSize);
/*    for(int k=0;k<matrixSize+*matrixColSize;k++){
    printf("%d\n",a[0]);
    }*/
    while(p<*matrixColSize){
        i=0;
        j=p;
        m=0;
        u=0;
        l=0;
        while(i<matrixSize&&j<*matrixColSize){
            a[m]=matrix[i][j];
            i++;
            j++;
            m++;
        }
        printf("%d\n",a[0]);
        qsort(a,m,sizeof(a[0]),compare);
        printf("%d\n",a[0]);
        for(int k=0;k<m-1;k++){
            if(a[k]==a[k+1]){
                l++;
            }
        }
        if(m==1||l==m-1){
            u=1;
        }
        if(u==0){
//            printf("%d %d\n",p,a[0]);
            return false;
        }
        p++;
    }
    p=0;
    u=0;
    memset(a,-1,matrixSize+*matrixColSize);
    while(p<matrixSize){
        i=p;
        j=0;
        m=0;
        u=0;
        l=0;
        while(i<matrixSize&&j<*matrixColSize){
            a[m]=matrix[i][j];
            i++;
            j++;
            m++;
        }
        qsort(a,m,sizeof(a[0]),compare);
        for(int k=0;k<m-1;k++){
            if(a[k]==a[k+1]){
                l++;
            }
        }
        if(m==1||l==m-1){
            u=1;
        }
        if(u==0){
//            printf("m\n");
            return false;
        }
        p++;
    }
    return true;
}

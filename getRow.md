给定一个非负索引 k，其中 k ≤ 33，返回杨辉三角的第 k 行。

在杨辉三角中，每个数是它左上方和右上方的数的和。

示例:

输入: 3
输出: [1,3,3,1]

/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* getRow(int rowIndex, int* returnSize){
    *returnSize=rowIndex+1;
    int** a=(int**)malloc(sizeof(int*)*(rowIndex+1));
    for(int i=0;i<=rowIndex;i++){
        a[i]=(int*)malloc(sizeof(int)*(i+1));
    }
    int *b=(int*)malloc(sizeof(int)*(rowIndex+1));
    int j=0;
    while(j!=rowIndex+1){
        if(j!=0&&j!=1){
        for(int i=1;i<j;i++){
            a[j][i]=a[j-1][i]+a[j-1][i-1];
            a[j][0]=1;
            a[j][j]=1;
        }
    }
    else{
        a[j][0]=1;
        a[j][j]=1;
    }
    j++;
    }
    for(int i=0;i<=rowIndex;i++){
        b[i]=a[rowIndex][i];
    }
    return b;
}

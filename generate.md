给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。

在杨辉三角中，每个数是它左上方和右上方的数的和。

示例:

输入: 5
输出:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]

/**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *returnColumnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** generate(int numRows, int* returnSize, int** returnColumnSizes){
    int** a=(int**)malloc(sizeof(int*)*numRows);
    *returnSize = numRows;
    *returnColumnSizes = (int *)malloc(sizeof(int)*numRows);
    for (int i = 0; i < numRows; i++) {
        (*returnColumnSizes)[i] = i+1;
        a[i] = (int*)malloc(sizeof(int)*(i+1));
    }
    int j=2;
    if(numRows==0){
        return a;
    }
    else if(numRows==1){
        a[0][0]=1;
        return a;
    }
    else if(numRows==2){
        a[0][0]=1;
        a[1][0]=1;
        a[1][1]=1;
        return a;
    }
    else{
        a[0][0]=1;
        a[1][0]=1;
        a[1][1]=1;
        while(1){
            a[j][0]=1;
            a[j][j]=1;
            for(int i=1;i<j;i++){
                a[j][i]=a[j-1][i]+a[j-1][i-1];
            }
            j++;
            if(j>numRows-1){
                break;
            }
        }
        return a;
    }
}

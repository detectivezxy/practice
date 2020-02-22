包含整数的二维矩阵 M 表示一个图片的灰度。你需要设计一个平滑器来让每一个单元的灰度成为平均灰度 (向下舍入) ，平均灰度的计算是周围的8个单元和它本身的值求平均，如果周围的单元格不足八个，则尽可能多的利用它们。

示例 1:

输入:
[[1,1,1],
 [1,0,1],
 [1,1,1]]
输出:
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]
解释:
对于点 (0,0), (0,2), (2,0), (2,2): 平均(3/4) = 平均(0.75) = 0
对于点 (0,1), (1,0), (1,2), (2,1): 平均(5/6) = 平均(0.83333333) = 0
对于点 (1,1): 平均(8/9) = 平均(0.88888889) = 0

注意:

    给定矩阵中的整数范围为 [0, 255]。
    矩阵的长和宽的范围均为 [1, 150]。

/**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *returnColumnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** imageSmoother(int** M, int MSize, int* MColSize, int* returnSize, int** returnColumnSizes){
    *returnSize=MSize;
    *returnColumnSizes=(int*)malloc(sizeof(int)*MSize);
    int**a=(int**)malloc(sizeof(int*)*MSize);
    for(int i=0;i<MSize;i++){
        (*returnColumnSizes)[i]=*MColSize;
        a[i]=(int*)malloc(sizeof(int)**MColSize);
    }
    int m=0,p=0;
    for(int i=0;i<MSize;i++){
        for(int j=0;j<*MColSize;j++){
            if(i-1>=0&&j-1>=0){
                m=m+M[i-1][j-1];
                p++;
            }
            if(i+1<MSize&&j-1>=0){
                m=m+M[i+1][j-1];
                p++;
            }
            if(j-1>=0){
                m=m+M[i][j-1];
                p++;
            }
            if(i-1>=0){
                m=m+M[i-1][j];
                p++;
            }
            if(i-1>=0&&j+1<*MColSize){
                m=m+M[i-1][j+1];
                p++;
            }
            if(i+1<MSize&&j+1<*MColSize){
                m=m+M[i+1][j+1];
                p++;
            }
            if(i+1<MSize){
                m=m+M[i+1][j];
                p++;
            }
            if(j+1<*MColSize){
                m=m+M[i][j+1];
                p++;
            }
            a[i][j]=(m+M[i][j])/(p+1);
            m=0;
            p=0;
        }
    }
    return a;
}

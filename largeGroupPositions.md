在一个由小写字母构成的字符串 S 中，包含由一些连续的相同字符所构成的分组。

例如，在字符串 S = "abbxxxxzyy" 中，就含有 "a", "bb", "xxxx", "z" 和 "yy" 这样的一些分组。

我们称所有包含大于或等于三个连续字符的分组为较大分组。找到每一个较大分组的起始和终止位置。

最终结果按照字典顺序输出。

示例 1:

输入: "abbxxxxzzy"
输出: [[3,6]]
解释: "xxxx" 是一个起始于 3 且终止于 6 的较大分组。

示例 2:

输入: "abc"
输出: []
解释: "a","b" 和 "c" 均不是符合要求的较大分组。

示例 3:

输入: "abcdddeeeeaabbbcd"
输出: [[3,5],[6,9],[12,14]]

说明:  1 <= S.length <= 1000

/**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *returnColumnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** largeGroupPositions(char * S, int* returnSize, int** returnColumnSizes){
    int number=0; 
    while((int)S[number]<=122&&(int)S[number]>=97){
        number++;
    }
    int b[1000],c[1000],p=0,i=0,m=0;
    for(int j=1;j<number;j++){
        while(S[i]==S[j]){
            m++;
            j++;
        }
        if(m>=2){
            b[p]=j-1-m;
            c[p]=j-1;
            p++;
        }
        m=0;
        i++;
        S[i]=S[j];
    }
//    printf("%d\n",p);
    int **x=(int**)malloc(sizeof(int*)*p);
    *returnSize=p;
    *returnColumnSizes=(int*)malloc(sizeof(int)*p);
    for(int j=0;j<*returnSize;j++){
        x[j]=(int*)malloc(sizeof(int)*2);
        (*returnColumnSizes)[j]=2;
    }
    for(int k=0;k<p;k++){
        x[k][0]=b[k];
        x[k][1]=c[k];
    }
    return x;
}

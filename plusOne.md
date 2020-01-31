给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。

最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。

示例 1:

输入: [1,2,3]
输出: [1,2,4]
解释: 输入数组表示数字 123。

示例 2:

输入: [4,3,2,1]
输出: [4,3,2,2]
解释: 输入数组表示数字 4321。

/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
        void g(int*digits,int *a,int j){
            if(digits[j]==9){
                a[j]=0;
                j--;
                g(digits,a,j);
            }
            else{
                digits[j]++;
                for(int i=0;i<=j;i++){
                    a[i]=digits[i];
                    }
            }
        }
int* plusOne(int* digits, int digitsSize, int* returnSize){
    int p=0;
    for(int i=0;i<digitsSize;i++){
        if(digits[i]==9){
            p++;
        }
    }
    if(p==digitsSize){
        *returnSize=digitsSize+1;
    }
    else{
        *returnSize=digitsSize;
    }
    int *a=(int*)malloc(sizeof(int)**returnSize);
    if(*returnSize==digitsSize+1){
        for(int i=0;i<*returnSize;i++){
            a[i]=0;
        }
        a[0]=1;
        return a;
    }
        else{
        int j=digitsSize-1;
        g(digits,a,j);
        return a;
    }
}

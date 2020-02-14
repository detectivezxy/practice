给定一个二进制数组， 计算其中最大连续1的个数。

示例 1:

输入: [1,1,0,1,1,1]
输出: 3
解释: 开头的两位和最后的三位都是连续1，所以最大连续1的个数是 3.

注意：

    输入的数组只包含 0 和1。
    输入数组的长度是正整数，且不超过 10,000。

int findMaxConsecutiveOnes(int* nums, int numsSize){
    int p=0,compar,max=0,m=0;
    for(int i=0;i<numsSize;i++){
        if(nums[i]==0){
            m++;
            compar=i-p;
            p=i;
            if(compar>max){
                max=compar;
            }
        }
    }
    if(m==0){
        max=numsSize+1;
    }
    if(numsSize-1-p>max&&m==1){
        max=numsSize-1-p;
    }
    else if(numsSize-1-p>max&&m!=1){
        max=numsSize-p;
    }
    if(numsSize==1&&nums[0]==1){
        return 1;
    }
    if(m==1){
        return max;
    }
    return max-1;
}

给定一个整数数组和一个整数 k, 你需要在数组里找到不同的 k-diff 数对。这里将 k-diff 数对定义为一个整数对 (i, j), 其中 i 和 j 都是数组中的数字，且两数之差的绝对值是 k.

示例 1:

输入: [3, 1, 4, 1, 5], k = 2
输出: 2
解释: 数组中有两个 2-diff 数对, (1, 3) 和 (3, 5)。
尽管数组中有两个1，但我们只应返回不同的数对的数量。

示例 2:

输入:[1, 2, 3, 4, 5], k = 1
输出: 4
解释: 数组中有四个 1-diff 数对, (1, 2), (2, 3), (3, 4) 和 (4, 5)。

示例 3:

输入: [1, 3, 1, 5, 4], k = 0
输出: 1
解释: 数组中只有一个 0-diff 数对，(1, 1)。

注意:

    数对 (i, j) 和数对 (j, i) 被算作同一数对。
    数组的长度不超过10,000。
    所有输入的整数的范围在 [-1e7, 1e7]。

int compar(const void*max,const void*min){
    return (*(int*)min < *(int*)max);
}
int findPairs(int* nums, int numsSize, int k){
    if(numsSize==0){
        return 0;
    }
    qsort(nums,numsSize,4,compar);
    int i=0,m=0,b[10000],o=0,u=0,a[10000];
    a[0]=nums[0];
    memset(b,0,sizeof(b));
    for(int j=1;j<numsSize;j++){
        if(nums[i]!=nums[j]){
            i++;
            o++;
            nums[i]=nums[j];
            a[i]=nums[i];
        }
        else
        {
            b[o]=1;
        }
    }
    for(int j=0;j<=o;j++){
        if(b[j]!=0){
            u++;
        }
    }
    for(int j=0;j<=i;j++){
        for(int l=j+1;l<=i;l++){
            if(a[j]+k==a[l]){
                m++;
                break;
            }
        }
    }
    if(k==0){
        m=u;
    }
    return m;
}

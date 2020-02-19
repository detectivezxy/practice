给定 n 个整数，找出平均数最大且长度为 k 的连续子数组，并输出该最大平均数。

示例 1:

输入: [1,12,-5,-6,50,3], k = 4
输出: 12.75
解释: 最大平均数 (12-5-6+50)/4 = 51/4 = 12.75

 

注意:

    1 <= k <= n <= 30,000。
    所给数据范围 [-10,000，10,000]。

double findMaxAverage(int* nums, int numsSize, int k){
    double p=0;
    for(int i=0;i<k;i++){
        p=p+nums[i];
    }
    double max=p;
    for(int i=1;i<=numsSize-k;i++){
        p=p-nums[i-1]+nums[i+k-1];
        if(p>max){
            max=p;
        }
    }
    max=max/k;
    return max;
}

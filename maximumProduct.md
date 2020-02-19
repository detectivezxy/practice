给定一个整型数组，在数组中找出由三个数组成的最大乘积，并输出这个乘积。

示例 1:

输入: [1,2,3]
输出: 6

示例 2:

输入: [1,2,3,4]
输出: 24

注意:

    给定的整型数组长度范围是[3,104]，数组中所有的元素范围是[-1000, 1000]。
    输入的数组中任意三个数的乘积不会超出32位有符号整数的范围。

int compare(const void *min, const void *max){
    return (*(int*)max > *(int*)min);
}
int compar(const void*maxd,const void*mind){
    return (*(int *)mind < *(int*)maxd);
}
int maximumProduct(int* nums, int numsSize){
    qsort(nums,numsSize,4,compare);
    int k=nums[0];
    int p=nums[0]*nums[1]*nums[2];
    qsort(nums,numsSize,4,compar);
    int u=k*nums[0]*nums[1];
    if(p>u){
        return p;
    }
    return u;
}

给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

示例 1:

输入: [3,2,3]
输出: 3

示例 2:

输入: [2,2,1,1,1,2,2]
输出: 2

int majorityElement(int* nums, int numsSize){
    int p=nums[0];
    int k=0;
    for(int i=0;i<numsSize;i++){
        if(nums[i]==p){
            k++;
        }
        else{
            k--;
        }
        if(k==0){
            p=nums[i+1];
        }
    }
    return p;
}

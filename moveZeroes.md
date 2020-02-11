给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

示例:

输入: [0,1,0,3,12]
输出: [1,3,12,0,0]

void moveZeroes(int* nums, int numsSize){
    int m=0;
    for(int i=0;i<numsSize;i++){
        if(nums[i]!=0){
            nums[m]=nums[i];
            m++;
        }
    }
    for(int i=m;i<numsSize;i++){
        nums[i]=0;
    }
}

给定一个包含 0, 1, 2, ..., n 中 n 个数的序列，找出 0 .. n 中没有出现在序列中的那个数。

示例 1:

输入: [3,0,1]
输出: 2

示例 2:

输入: [9,6,4,2,3,5,7,0,1]
输出: 8

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/missing-number
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
int missingNumber(int* nums, int numsSize){
    int a[numsSize+1];
    memset(a,-1,4*numsSize+1);
    for(int i=0;i<numsSize;i++){
        a[nums[i]]=0;
    }
    int p=-1;
    for(int i=0;i<numsSize+1;i++){
        if(a[i]==-1){
            p=i;
            break;
        }
    }
    if(p==-1){
        return numsSize;
    }
    else{
        return p;
    }
}

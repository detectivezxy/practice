给定一个非空且只包含非负数的整数数组 nums, 数组的度的定义是指数组里任一元素出现频数的最大值。

你的任务是找到与 nums 拥有相同大小的度的最短连续子数组，返回其长度。

示例 1:

输入: [1, 2, 2, 3, 1]
输出: 2
解释: 
输入数组的度是2，因为元素1和2的出现频数最大，均为2.
连续子数组里面拥有相同度的有如下所示:
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]
最短连续子数组[2, 2]的长度为2，所以返回2.

示例 2:

输入: [1,2,2,3,1,4,2]
输出: 6

注意:

    nums.length 在1到50,000区间范围内。
    nums[i] 是一个在0到49,999范围内的整数。

int compare(const void*max,const void*min){
    return *(int*)min < *(int*)max;
}
int findShortestSubArray(int* nums, int numsSize){
    int a[numsSize+1],u=2,y=0,last=4,first=0,m=0,max=0;
    for(int i=0;i<numsSize;i++){
        a[i]=nums[i];
    }
    a[numsSize]=50001;
    qsort(a,numsSize+1,4,compare);
    int p=a[0];
    for(int i=0;i<numsSize+1;i++){
        if(a[i]!=p){
            if(m>=max){
                last=3;
                first=0;
                for(int j=0;j<numsSize;j++){
                    if(nums[j]==p){
                        first=j;
                        break;
                    }
                }
                if(m>=max){
                    for(int j=numsSize-1;j>=0;j--){
                        if(nums[j]==p){
                        last=j;
                        break;
                        }
                    }
                }
                y=(last-first+1);
                if(m>max){
                    u=y;
                }
                if(m==max&&y<u){
                    u=y;
                }
                max=m;
            }
            p=a[i];
            m=0;
        }
        m++;
    }
    printf("%d %d %d %d\n",first,last,max,m);
    if(numsSize==1||max==1){
        u=1;
    }
    return u;
}

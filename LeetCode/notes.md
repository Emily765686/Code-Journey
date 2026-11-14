关于刷力扣的事
1.两数之和：
给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。
你可以假设每种输入只会对应一个答案，并且你不能使用两次相同的元素。
你可以按任意顺序返回答案。
示例 1：
输入：nums = [2,7,11,15], target = 9
输出：[0,1]      
解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。 

示例 2：
输入：nums = [3,2,4], target = 6
输出：[1,2]

示例 3：
输入：nums = [3,3], target = 6
输出：[0,1]

看到的第一眼，只会for循环的暴力拆解，高级的方法想不了一点
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target, int* returnSize) {
    int *result=(int*)malloc(2*sizeof(int));   
//int*result为指针，malloc用于申请两块连续int大小堆内存，                                                                       //（int*）用于将malloc返回的无类型的指针强制转换为int类型指针。

   for(int i=0;i<numsSize;i++){              
        for (int a=1+i;a<numsSize;a++){        
        //开始写成了a=0,后来发现它遍历了两遍，会造成类似nums[1]+nums[1]，                                                                //取了相同的值，与题意不符。

             if(nums[i]+nums[a]==target){       
                result[0]=i;
                result[1]=a;
                *returnSize=2;                    
            }
        }
    }
    return result;                              //开始忘记返回值了
}
```
看到有大佬用哈希表，完全没听过，看答案发现C语言的哈希表最复杂（痛苦），
还有，两数之和不应该是int a，b； printf（"%d",a+b)吗

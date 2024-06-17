# [80. 删除有序数组的重复项II](https://leetcode.cn/problems/remove-duplicates-from-sorted-array-ii/description/)
``` java
给你一个有序数组 nums ，请你 原地 删除重复出现的元素，使得出现次数超过两次的元素只出现两次 ，返回删除后数组的新长度。

不要使用额外的数组空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成。
```
## 示例 1：
``` java
输入：nums = [1,1,1,2,2,3]
输出：5, nums = [1,1,2,2,3]
解释：函数应返回新长度 length = 5, 并且原数组的前五个元素被修改为 1, 1, 2, 2, 3。 不需要考虑数组中超出新长度后面的元素。
```
## 示例 2：
``` java
输入：nums = [0,0,1,1,1,1,2,3,3]
输出：7, nums = [0,0,1,1,2,3,3]
解释：函数应返回新长度 length = 7, 并且原数组的前七个元素被修改为 0, 0, 1, 1, 2, 3, 3。不需要考虑数组中超出新长度后面的元素。
```
## 提示：
``` java
1 <= nums.length <= 3 * 10^4
-10^4 <= nums[i] <= 10^4
nums 已按升序排列
```
## 实现思路：
``` java
覆盖原数组的方法，引入一个变量记录重复出现的值，只重复覆盖在第一次出现该值的后一位
```
## 实现代码：
``` java
class Solution {
    public int removeDuplicates(int[] nums) {
        int k=0;
        Integer temp=null;
        for(int i=1;i<nums.length;i++){
            if(nums[i]==nums[k]){
                temp=nums[i];
                nums[k+1]=temp;
            }else{
                if(temp !=null&&temp==nums[k]){
                    nums[k+2]=nums[i];
                    k=k+2;
                }else{
                    nums[k+1]=nums[i];
                    k++;
                }
            }
        }
        k=temp!=null&&temp==nums[k]?k+2:k+1;
        return k;
    }
}
```

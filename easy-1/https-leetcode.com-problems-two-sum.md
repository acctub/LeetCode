---
description: '[2,7,13,19]寻找顺序数组中和为X的两个数，并且给出下标'
---

# 01Two Sum

### Two Sum I

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        
        System.out.print("nums.length=");
        System.out.println(nums.length);
        if (nums.length < 2){
            throw new IllegalArgumentException("lengths is too short!");
        }
        else{
            for (int i = 0; i < nums.length; i++){
                for (int j = i+1; j < nums.length; j++){
                    if(nums[i]+nums[j] == target){
                        return new int[]{i,j};
                    }
                }   
             }   
            throw new IllegalArgumentException("No Solution");   
        }
    }
}
```

### Two Sum II

```javascript
class Solution {
    
    public int[] twoSum(int[] numbers, int target) {
        int left = 0;
        int right = numbers.length-1;
        
        while(left != right){//根据结果左右指针适当的缩减
            if(numbers[left]+numbers[right] == target)
                return new int[]{left+1,right+1};
            if(numbers[left]+numbers[right] < target)
                left++;
            if(numbers[left]+numbers[right] > target)
                right--;
            }
        throw new IllegalArgumentException(" no Solution !");
    }
}
```


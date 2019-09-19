# 15. 3Sum

Solution

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(nums);
        
        for (int i = 0; i + 2 < nums.length; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) {              // skip same result???
                continue;
            }
            int j = i + 1, k = nums.length - 1;  
            int target = -nums[i];
            while (j < k) {
                if (nums[j] + nums[k] == target) {
                    res.add(Arrays.asList(nums[i], nums[j], nums[k]));
                    j++;
                    k--;
                    while (j < k && nums[j] == nums[j - 1]) j++;  // skip same result
                    while (j < k && nums[k] == nums[k + 1]) k--;  // skip same result
                } else if (nums[j] + nums[k] > target) {
                    k--;
                } else {
                    j++;
                }
            }
        }
        return res;
    }
}
```

```java
Arrays.asList的用法
Arrays.asList的作用是将数组转化为list。设置几个值进去，简化代码，省去add的部分。

String[] s = {"aa","bb","cc"};
List<String> strlist = Arrays.asList(s);

//等同于
strlist.add("aa");strlist.add("bb");strlist.add("cc");

```


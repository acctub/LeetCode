# 15. 3Sum

Solution

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();//二次元配列の宣言
        int n = nums.length;
        Arrays.sort(nums);//Arrays.sort(配列)!!!!ここがポイント！
        for(int i = 0; i < nums.length;i++){
            if(i > 0 && nums[i] == nums[i-1])
                continue;//以降を回さない
            int tar = -nums[i];
            for(int j=i+1,k=n-1; j<k; ){
                if(nums[j]+nums[k]==tar){
                    res.add(Arrays.asList(nums[i],nums[j++],nums[k--]));
                    while(j < k && nums[j] == nums[j-1]) j++;//先のステップでj>kの可能性がある
                    while(j < k && nums[k] == nums[k+1]) k--;
                }
                else if(nums[j]+nums[k] > tar) k--;
                else j++;
            }
        }
        return res;
    }
}
/*hint
STEP1--元の配列を昇順に並べ替える
STEP2--先頭の数字の負数をtargetにし、後ろから足したらtargetに等しい二つの数字LとRを探す
LとRの挟む範囲は徐々に縮小し、LのindexがRのを上回ったときloop終了
[(-4),-1,-1,0,1,2] target=4 L=-1,R=2
[(-4),-1,-1,0,1,2] target=4 L=0,R=1
...
[-4,(-1),-1,0,1,2] target=1 L=-1,R=2 (OK)見つかったらリストに入れる
[-4,(-1),-1,0,1,2] target=1 L=0,R=1 (OK)
...
*/
```

```java
Arrays.asList的用法
Arrays.asList的作用是将数组转化为list。设置几个值进去，简化代码，省去add的部分。

String[] s = {"aa","bb","cc"};
List<String> strlist = Arrays.asList(s);

//等同于
strlist.add("aa");strlist.add("bb");strlist.add("cc");

```


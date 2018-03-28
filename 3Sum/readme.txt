Question:Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

For example, given array S = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]


class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);								//排序的复杂度是O(nlogn)
        List<List<Integer>> result = new LinkedList<>();
        for(int i=0;i<nums.length-2;i++){				//对每一个nums[i]从其后和最后开始找
            if(i==0||nums[i]!=nums[i-1]){
                int lo = i+1,hi = nums.length-1,sum = -nums[i];	//lo为i后（比i大） hi 为最后（最大）
                while(lo<hi){
                    if(nums[lo]+nums[hi]==sum){						//找到了
                        result.add(Arrays.asList(nums[i],nums[lo],nums[hi]));
                        while(lo<hi&&nums[lo]==nums[lo+1]) lo++;	//去重，因为i已经确定了，因此lo或hi如果重复另一个也一定重复
                        while(lo<hi&&nums[hi]==nums[hi-1]) hi--;
                        lo++;hi--;
                    }else if(nums[lo]+nums[hi]<sum){
                        lo++;							//如果小于 lo增大，则更接近target-nums[i]
                    }else{
                        hi--;
                    }
                }                  
            }           
        }
     return result;  
    }
}

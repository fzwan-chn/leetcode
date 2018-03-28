Question:Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

For example, given array S = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]


class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);								//����ĸ��Ӷ���O(nlogn)
        List<List<Integer>> result = new LinkedList<>();
        for(int i=0;i<nums.length-2;i++){				//��ÿһ��nums[i]���������ʼ��
            if(i==0||nums[i]!=nums[i-1]){
                int lo = i+1,hi = nums.length-1,sum = -nums[i];	//loΪi�󣨱�i�� hi Ϊ������
                while(lo<hi){
                    if(nums[lo]+nums[hi]==sum){						//�ҵ���
                        result.add(Arrays.asList(nums[i],nums[lo],nums[hi]));
                        while(lo<hi&&nums[lo]==nums[lo+1]) lo++;	//ȥ�أ���Ϊi�Ѿ�ȷ���ˣ����lo��hi����ظ���һ��Ҳһ���ظ�
                        while(lo<hi&&nums[hi]==nums[hi-1]) hi--;
                        lo++;hi--;
                    }else if(nums[lo]+nums[hi]<sum){
                        lo++;							//���С�� lo��������ӽ�target-nums[i]
                    }else{
                        hi--;
                    }
                }                  
            }           
        }
     return result;  
    }
}

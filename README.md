class Solution {
    public int rob(int[] nums) {
        int[] dp = new int[nums.length];
        Arrays.fill(dp,-1);
        return robFrom(0 , nums , dp);
    }

    private static int robFrom(int i , int[] nums , int[] dp){
        if(i >= nums.length){
            return 0;
        }

        if(dp[i] != -1){   // if the numner is already considered
            return dp[i];
        }

        int rob = nums[i] + robFrom(i + 2 , nums , dp); // take
        int skip = robFrom(i + 1 , nums, dp); // not take

        dp[i] = Math.max(rob , skip);
        return dp[i];
    }
}

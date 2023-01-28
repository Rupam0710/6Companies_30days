class Solution {
    public int maxSum(int[][] grid) {
        int n = grid.length;
        int m = grid[0].length;

        int maxi = 0;
        for(int i=1;i+1<n;i++){
            for(int j=1;j+1<m;j++){
                int sum = grid[i][j]+grid[i-1][j-1]+grid[i-1][j]+grid[i-1][j+1]+grid[i+1][j-1]+grid[i+1][j]+grid[i+1][j+1];
                maxi = Math.max(maxi,sum);
            }
        }
        return maxi;
    }
}
# Largest-Square-in-Matrix
A dynamic programming problem, in which we have to tell the biggest square formed
Well coming to this problem, I picked this problem from the website geeks of geeks.

https://practice.geeksforgeeks.org/problems/largest-square-formed-in-a-matrix0806/1

Solution: For this problem, it is very clear that the any block can be the part of the max square formed, so i checked the size of the max square formed if the cell is being considered. For this i used a table having n rows and m columns , if the (i,j) block is considered then to check the max square formed, I used the (i-1,j-1),(i,j-1),(i-1,j) blocks.
 let's say max_square_formed from any (i,j) block = dp[i][j];
 if(curr_block is 1)
   Max Square Formed = Math.min( dp[i-1][j] ,Math.min(dp[i-1][j-1], dp[i][j-1]) )+1;
 else
   Max Square Formed = 1;
 
 dp will be a 2d array and at the end of for loops one block will be having the max value. I used an optimised approah, rather than again loopping n2 times, i found the max in the previous loop .
 
 Sharing my coding approach: 

class Solution{
    static int maxSquare(int n, int m, int mat[][]){
        // code here
        
        int[][] dp = new int[n][m];
        int max=0;
        for(int i=0;i<m;i++){
            if(mat[0][i]==1){
              dp[0][i]=1;
              max=1;
            }
        }
        for(int i=0;i<n;i++){
            if(mat[i][0]==1){
              dp[i][0]=1;
              max = 1;
            }
        }
        
        for(int i=1;i<n;i++){
            for(int j=1;j<m;j++){
                if(mat[i][j]==0){
                    dp[i][j] = 0;
                }
                else{
                    dp[i][j]=Math.min( dp[i-1][j] ,Math.min(dp[i-1][j-1], dp[i][j-1]) )+1;
                }
                //System.out.print(dp[i][j]+" ");
                max = Math.max(max,dp[i][j]);
                
            }
            //System.out.println();
        }
        return max;
    }
}

I hope you find the solution nice and interesting.
Time Complexity : O(N^2)
Space Complexity : O(N^2)
 
 

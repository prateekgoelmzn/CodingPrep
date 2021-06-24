# CodingPrep
## Day-1 (15/06/2021)
### Algorithms
#### 1) Kadane

![alt text](https://github.com/prateekgoelmzn/CodingPrep/blob/main/kadane_algo.jpeg)

In Case, all the elements present in array is negative then below is the modification in the kadane algorithm.
```java
// Input : [-1,-2,-3,-4,-5] -> output : -1
    int maxSubarraySum(int arr[], int n){
        
        // Your code here
        int curr_sum = 0;  // keep track of the current sum
        int best_sum = Integer.MIN_VALUE;
        int max = Integer.MIN_VALUE;
        
        for(int ele : arr){
            curr_sum = Math.max(curr_sum+ele,0);
            best_sum = Math.max(curr_sum,best_sum);
            max = Math.max(max,ele);
        }
        
        return max<0?max:best_sum;
    }
```

Resources
* https://youtu.be/HCL4_bOd3-4
* [wikipedia article on kadane algo.](https://en.wikipedia.org/wiki/Maximum_subarray_problem)

#### 2) Subset of a Set

![alt text](https://github.com/prateekgoelmzn/CodingPrep/blob/main/subsetOfSet_algo.jpeg)

Subset printing using bitwise approach

![alt text](https://github.com/prateekgoelmzn/CodingPrep/blob/main/print_all_subset_bitwise.png)

Resources
* https://youtu.be/u0e29JIdxZU
#### 3) BFS and DFS on Graph

![alt text](https://github.com/prateekgoelmzn/CodingPrep/blob/main/bfsAndDfs_algo.jpeg)

Resources
* [BFS](https://youtu.be/geOBaNYYInc)
* [DFS](https://youtu.be/GmZNp9_-imM)
* [GFG BFS Code](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/)
* [GFG DFS Code](https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/)


## Day-2 (17/06/2021)
### Binary Tree
#### DFS approach to traverse on Binary Tree. Also, it helps to solve most of the problem related to binary tree.
```
* Base case nikalo
* Recursion call krdo left and right pr
* And finally jo krna hai wo main root node s krdo
```
e.g
```java
/* 
 * Program to find sum of all nodes of a binary tree. 
 **/
int sum(TreeNode root){
    if(root==null){
        return 0;
    }
    int left = dfs(root.left);
    int right = dfs(root.right);
    return root.val + left + right;
}


/* 
 * Program to find max value node among all nodes of a binary tree. 
 **/
int max(TreeNode root){
    if(root==null){
        return 0;
    }
    int left = max(root.left);
    int right = max(root.right);
    return Math.max(root.val + left + right);
}
```
## Day-3 (18/06/2021)
### Segment Tree
#### Segment Tree : it helps to solve questions related to range sum query.
Resources
* [Segment Tree Java Code](https://github.com/Sunchit/Coding-Decoded/blob/master/June2021/RangeSumMutable.java)
* [Segment Tree Explaination YouTube Video](https://youtu.be/dUkRI0R3sg8)

## Day-4 (19/06/2021)
### Some question tricks
#### 1. Kth Smallest Element in a BST | LeetCode - 230
Approach:
* The fact that inorder traversal on BST gives values of nodes in increasing order.
* So using above fact. we can do inorder traversal on BST along with it we have to store traversed node in a list.
* Now return k-1 index element from the list, it is our ans.
```java
class Solution {
    List<Integer> list;
    public int kthSmallest(TreeNode root, int k) {
        list = new ArrayList<Integer>();
        inorderTraversal(root);
        return list.get(k-1);
    }
    
    public void inorderTraversal(TreeNode root){
        if(root==null){
            return;
        }
        
        inorderTraversal(root.left);
        list.add(root.val);
        inorderTraversal(root.right);
    }
}
```

#### 2. Given an array, rotate the array clockwise k places. without using extra space and TC should be O(n)
* Input : 1 2 3 4 5 6 7 and k=2 
* Output : 7 6 1 2 3 4 5

Approach:
* reverse(arr,0,arr.length-k-1) // 5 4 3 2 1 6 7
* reverse(arr,arr.length-k,arr.length-1) // 5 4 3 2 1 7 6
* reverse(arr,0,arr.length-1) // 6 7 1 2 3 4 5


## Day-5 (20/06/2021)
### Some question tricks
#### 1. Palindromic Substrings | Leetcode: 647
Approach : [Manacher Algorithm](https://www.geeksforgeeks.org/manachers-algorithm-linear-time-longest-palindromic-substring-part-1/)
```java
int numPalindromic(String str){
	
	int ans = 0;
	
	// find count of odd length substring
	for(int i=0;i<str.length;i++){
		for(int j=0;j+i<str.length()&&i-j>=0;j++){
			if(str[i+j]!=str[i-j]){
				break;
			}
			else{
				ans++;
			}
		}
	}
	
	// find count of even length substring
	for(int i=0;i<str.length;i++){
		for(int j=0;j+i+1<str.length()&&i-j>=0;j++){
			if(str[i+j+1]!=str[i-j]){
				break;
			}
			else{
				ans++;
			}
		}
	}
	
	return ans;	
}
```
* [Coding Ninja YT video explaination](https://youtu.be/lIV-IXhpqtU)

## Day-6 (21/06/2021)
#### 1. Pascal triangle | Leetcode: 118
![pascal triangle](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

code :
```java
class Solution {
    
    public static List<List<Integer>> pascalTriangle;
    
    public static void pascalSolve(int n){
    
        if(n == 1){
            pascalTriangle.add(Arrays.asList(1));
            return;
        }
        if(n == 2){
            pascalSolve(n-1);
            pascalTriangle.add(Arrays.asList(1,1));
            return; 
        }
    
        pascalSolve(n-1);
        
        List<Integer> oldPascalRow = pascalTriangle.get(pascalTriangle.size()-1);
    
        List<Integer> result = new ArrayList<>();
        result.add(1);
        for(int i=1;i<oldPascalRow.size();i++){
            result.add(oldPascalRow.get(i) + oldPascalRow.get(i-1));
        }
        result.add(1);
    
        pascalTriangle.add(result);
    }    
    
    public List<List<Integer>> generate(int numRows) {
        pascalTriangle = new ArrayList<>();
        pascalSolve(numRows);
        return pascalTriangle;
    }
    
}
```
#### 2. Top k frequent elements | Leetcode : 347
Approach : 
* First find the frequency of every element present in given array.
* Use heap, we can use any either min heap or max heap.
* 1) if we are using max heap, we have to store element in pair form e.g. <element, frequency> and max heap compare element on the basis of frequency. greater the frequency the element will be at top. At last, we have to pop k elements from heap and that will be our answer.
* 2) if we are using min heap, we have to fix the size of heap as k. now we have to insert the element in pair form e.g. <element, frequency>. once it get filled by k element and we still have elements to fill then we pop the top element and insert new element.this way at last we have k element in the heap whose frequency will be most frequent.

## Day-7 (24/06/2021)
#### 1. [Unique Paths](https://leetcode.com/problems/unique-paths/) | Leetcode: 62
Approach :
* Apply DFS along with memoization

```java
class Solution {
    Integer memo[][] = null;
    public int uniquePaths(int m, int n) {
        memo = new Integer[m][n];
        return dfs(m-1,n-1);
    }
    
    public int dfs(int m , int n){
        if(m<0 || n<0){
            return 0;
        }
        
        if(m==0 && n==0){
            return 1;
        }
        
        if(memo[m][n]!=null){
            return memo[m][n];
        }
        
        int down = dfs(m-1,n);
        int right = dfs(m,n-1);
        
        return memo[m][n] = down+right;
    }
}
```
#### 2. [Out of Boundary Paths](https://leetcode.com/problems/out-of-boundary-paths/) | Leetcode : 576 
Approach : it is similar to above one i.e. unique paths. DFS with Memoization
```java
class Solution {
    // TC : O(n * m * maxMoves)
    private Long memo[][][] = null;
    private int mod = 1000000007;
    
    public int findPaths(int m, int n, int maxMove, int startRow, int startColumn) {
        memo = new Long[m+1][n+1][maxMove+1];
        return (int)(findPathsMemoHelper(m,n,maxMove,startRow,startColumn));
    }
    
    public long findPathsMemoHelper(int m,int n,int maxMove,int srow,int scol){
        if(maxMove<0){
            return 0;
        }
        
        if(srow<0 || srow>=m || scol<0 || scol>=n){
            return 1;
        }
        
        if(memo[srow][scol][maxMove]!=null){
            return memo[srow][scol][maxMove];
        }
        
        long total = 0;
        long left = findPathsMemoHelper(m,n,maxMove-1,srow,scol-1);
        long right = findPathsMemoHelper(m,n,maxMove-1,srow,scol+1);
        long up = findPathsMemoHelper(m,n,maxMove-1,srow-1,scol);
        long down = findPathsMemoHelper(m,n,maxMove-1,srow+1,scol);
        
        total = ((left+right+up+down)%mod);
        return memo[srow][scol][maxMove] = total;
        
    }
```
#### 3. Catalan Number
* LeetCode problem : [96. Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/)
```java
class Solution {
    long catalan(int n)
    {
        long catNum = 1;
     
        if(n==1){
            return catNum;
        }
    
        for (int i = 1; i <=n; i++)
        {
            catNum *= (4 * i - 2);
            catNum /= (i + 1);
        }
        
        return catNum;
    }
    
    public int numTrees(int n) {
        return (int)catalan(n);
    }
}
```
* [Applications of Catalan Number](https://www.geeksforgeeks.org/applications-of-catalan-numbers/)

# Resources
* [DS and Algo basic overview](https://github.com/kdn251/interviews)
* [Leetcode 75 questions DSA Sheet](https://docs.google.com/spreadsheets/d/1A2PaQKcdwO_lwxz9bAnxXnIQayCouZP6d-ENrBz_NXc/edit#gid=0)

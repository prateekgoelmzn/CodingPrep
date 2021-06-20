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


# Resources
* [DS and Algo basic overview](https://github.com/kdn251/interviews)
* [Leetcode DSA Sheet](https://docs.google.com/spreadsheets/d/1A2PaQKcdwO_lwxz9bAnxXnIQayCouZP6d-ENrBz_NXc/edit#gid=0)

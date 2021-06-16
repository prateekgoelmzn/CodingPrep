# CodingPrep
## Day-1 (15/06/2021)
### Algorithms
#### 1) Kadane

![alt text](https://github.com/prateekgoelmzn/CodingPrep/blob/main/kadane_algo.jpeg)

In Case, all the elements present in array is negative then below is the modification in the kadane algorithm.
```
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

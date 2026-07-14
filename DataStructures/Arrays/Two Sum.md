# Two Sum

## Approach

### Approach
The solution uses a **single-pass hash map** to trade space for time. As we iterate through the array, we calculate the complement ($target - nums[i]$) for each element. If this complement already exists in the hash map, we have found the target pair and immediately return their indices. Otherwise, we map the current element's value to its index and store it in the hash map for future lookups.

### Why It Works
Instead of using a brute-force nested loop to find the complement, storing visited elements in a hash map allows us to check for the complement's existence in $\mathcal{O}(1)$ amortized time. Because a unique solution is guaranteed to exist, the second element of the pair will always find its corresponding complement (the first element, which was processed and stored earlier) in the map.

### Complexity
* **Time Complexity:** $\mathcal{O}(n)$, where $n$ is the length of the `nums` array. We traverse the array exactly once, performing $\mathcal{O}(1)$ average-time lookup and insertion operations on the hash map at each step.
* **Space Complexity:** $\mathcal{O}(n)$, as we may need to store up to $n$ elements in the hash map in the worst-case scenario (e.g., when the matching pair is located at the very end of the array).

## Code

```Java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        HashMap<Integer, Integer> hash = new HashMap<>();
        for(int i = 0; i < n; i++) {
            int comp = target - nums[i];
            if(hash.containsKey(comp)) {
                return new int[]{hash.get(comp), i};
            } hash.put(nums[i], i);
        }
        return new int[]{};
    }
}
```

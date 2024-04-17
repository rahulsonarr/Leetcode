Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

 

Example 1:

Input: nums = [3,2,3]
Output: 3
Example 2:

Input: nums = [2,2,1,1,1,2,2]
Output: 2
 

Constraints:

n == nums.length
1 <= n <= 5 * 104
-109 <= nums[i] <= 109
 

Follow-up: Could you solve the problem in linear time and in O(1) space?

```bash
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        # Initialize candidate and count
        candidate = None
        count = 0
        
        # Step 1: Find the candidate
        for num in nums:
            if count == 0:
                candidate = num
            count += (1 if num == candidate else -1)
        
        # Step 2: Validate the candidate
        count = 0
        for num in nums:
            if num == candidate:
                count += 1
        
        # If the candidate is indeed the majority element, return it
        if count > len(nums) // 2:
            return candidate

```

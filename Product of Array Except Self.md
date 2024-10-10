Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

 

Example 1:

Input: nums = [1,2,3,4]
Output: [24,12,8,6]
Example 2:

Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
 

Constraints:

2 <= nums.length <= 105
-30 <= nums[i] <= 30
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
 

Follow up: Can you solve the problem in O(1) extra space complexity? (The output array does not count as extra space for space complexity analysis.)

###Solution
To solve the "Product of Array Except Self" problem without using division and with O(n) time complexity, you can approach it by calculating two products for each element:

Left Product: The product of all elements to the left of the current index.
Right Product: The product of all elements to the right of the current index.
Then, for each element, multiply the left product and right product to get the result.

Approach:
Left Products Array: Iterate through the array and store the cumulative product of elements to the left of the current index.
Right Products Array: Iterate through the array from the end and store the cumulative product of elements to the right of the current index.
Final Output: For each element, multiply its left product and right product.
Steps:
Initialize an output array answer of the same length as nums and fill it with 1's.
Compute the left products and store them directly in answer.
Traverse from the end of the array and compute the right products on the fly, updating the output array accordingly.

##Solution in Python:
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        answer = [1] * n
        
        # Calculate left products
        left_product = 1
        for i in range(n):
            answer[i] = left_product
            left_product *= nums[i]
        
        # Calculate right products and update the answer array
        right_product = 1
        for i in range(n - 1, -1, -1):
            answer[i] *= right_product
            right_product *= nums[i]
        
        return answer

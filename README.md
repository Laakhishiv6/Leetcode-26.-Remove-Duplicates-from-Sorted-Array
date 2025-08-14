# Leetcode-26.-Remove-Duplicates-from-Sorted-Array
# Description
Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.

Consider the number of unique elements of nums to be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the unique elements in the order they were present in nums initially. The remaining elements of nums are not important as well as the size of nums.
Return k.
# Solution
In the given problem we have been given a sorted array nums .We have to return the length of the array with no duplicates at all. But this has to be done without returning or creating any extra memory.

This can be done by using two-pointer technique , we will take 2 pointers left and right . The left pointer will be used to keep track of the no duplicates in the array , meanwhile the right pointer will be looping through the array and check if any unique value is found then replace it with the left value and increment the left pointer to check for other unique values.

Example 1:

Input: nums = [1,1,2]

Output: 2, nums = [1,2,_]

Example 2:

Input: nums = [0,0,1,1,1,2,2,3,3,4]

Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]

# Algorithm
1. Create a left pointer to track the position of the unique element , since we know that the first element in the array will always be unique hence we will start the operation to check for unique numbers from the second element of the array , hence initiliase left as 1.
2. Loop through the array using right pointer and check if the current value of right pointer and that of the its previous value are the same or not.
3. If they are not same , we can say that the value found is a unique one .Therefore, assign the left pointer value the right pointer's value (which is the unique value).
4. Now, if the current right value and its previous value are the same , then ignore and move on to the next value since the value is not duplicate .
5. Increment the left pointer to check for other unique values.
6. Return the length of the array ,by returning the pointer value of left after this operation.
# Code
class Solution:

    def removeDuplicates(self, nums: List[int]) -> int:
        left=1
        for right in range(1,len(nums)):
            if nums[right]!=nums[right-1]:
                nums[left]=nums[right]
                left+=1
        return left
# Compelxity
Time Complexity: O(n²) — the nested loop checks each element for duplicates.

Space Complexity: O(1) — no extra data structures are used except a few variables.

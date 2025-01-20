# Cheatsheet

High level overview of the patterns, and when to use them

## Two Pointers Pattern

* INPUT: an array or sorted linked list
* PROBLEM: find a set of elements in the array/list that meet certain constraints
* PATTERN: you use two pointers to iterate through the array/list to find sets of values that meet the constraints
* EXAMPLES:
  * target sum: given an array of numbers, find a pair in the array whose sum is equal to the target
    * one pointer starts at the left most index, one at the right most. add. if the addition is > target, move right pointer back. if addition is < target, move left pointer forward.
  * non duplicate numbers: given an array of numbers, find all the non duplicate numbers
    * you can sort the array, and use two pointers. one that stays at the start of the duplicate numbers, one that interates though the dupes until the next non dupe is found.
    * and thus my gripe with leet code...because IRL you'd just use `new Set([...myArr])`, but whatever

## Fast and Slow Pointers

* INPUT: an array or linked list
* PROBLEM: detect a cycle, find the middle of a linked list, find the length of a cycle, split a linked list
* PATTERN: you use a fast pointer that iterates through the list faster than the slow pointer. typically fast iterates through two nodes, while slow iterates through one at a time
* EXAMPLES:
  * linked list cycle: given a singly linked list, determine if the list has a cycle
    * fast pointer moves twice as fast as slow pointer. if at some point the pointers meet, there is a cycle. if the fast pointer reaches the end, there is not a cycle
  * middle of a linked list: given a linked list, find the middle
    * fast pointer moves twice as fast. if fast pointer reaches the end, the slow pointer will be at the middle of the list.
  * linked list palindrome: given a linked list, find if it's a palindrome
    * find the middle of the linked list. reverse the second half of the linked list. move through the first half, and second half of the linked list in order checking for equality

## Sliding Window

* INPUT: an array or linked list
* PROBLEM: calculate something along all the subarrays of a given size
* PATTERN: you define a sub-array window. you can use this window to calculate things in the subarray. you move the window along the array, at each move, you can add/subtract the new elements in the window. prevents you from calculating the entire window each time it's moved.
* EXAMPLES:
  * given an array, and a number 'k', find the maximum sum of any contiguous subarray of size 'k'
    * you define a windowStart, windowEnd, and windowSum. you add all elements in the window, then bump the position of the window by one. when you do this, you subtract the first element of the old window, and add the last element of the new window, then store the sum

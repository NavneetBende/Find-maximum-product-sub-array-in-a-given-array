Maximum product of sub-array in Python
Here, in this page we will discuss the program to find the maximum product of sub-array in python programming language. We are given with an array and need to return the maximum value of the product of the sub-array.

Maximum product of sub-array in Python
Example
Input : arr = [ 1, -2, -3, 0, 7, -8, -2 ]
Output : Maximum product sub-array is 112
Method Discussed
Method 1 : Brute Force solution
Method 2 : Efficient solution
Let’s discuss above two methods in brief.

Method 1 :
Create a variable say result, set result = arr[0], this variable hold the required maximum product.
Run a loop for range(n)
Create a variable mul = arr[i], this variable hold the product of sub-array.
Run a inner loop, set result = max(result, mul)
And, mul *= arr[j]
Update, result = max(result, mul)
Return result.
Time and Space Complexity :
Time Complexity : O(n2)
Space Complexity : O(1)
Method 1 : Code in Python
Run
def maxSubarrayProduct(arr, n):
 
    # Initializing result
    result = arr[0]
 
    for i in range(n):
     
        mul = arr[i]
       
        # traversing in current subarray
        for j in range(i + 1, n):
            result = max(result, mul)
            mul *= arr[j]
         
        # updating the result for (n-1)th index.
        result = max(result, mul)
     
    return result
 
arr = [ 1, -2, -3, 0, 7, -8, -2 ]
n = len(arr)
print("Maximum sub-array product is" , maxSubarrayProduct(arr, n))
Output
Maximum sub-array product is 112
Related Pages
Counting the number of even and odd elements in an array

Find all Symmetric pairs in an array

Finding Arrays are disjoint or not

Determine Array is a subset of another array or not

Determine can all numbers of an array be made equal

Method 2 :
This is the efficient solution and is also similar to Largest Sum Contiguous Subarray problem which uses Kadane’s algorithm.

Declare three variables say max_so_far, max_ending_here & min_ending_here.
For every index the maximum number ending at that index will be the maximum(arr[i], max_ending_here * arr[i], min_ending_here[i]*arr[i]).
Similarly the minimum number ending here will be the minimum of these 3.
Thus we get the final value for maximum product subarray.
Time and Space Complexity :
Time Complexity : O(n)
Space Complexity : O(1)
Method 2 : Code in Python
def maxSubarrayProduct(arr, n):
    max_ending_here = arr[0];
    min_ending_here = arr[0];
    max_so_far = arr[0];
    
    for i in range(n):
        temp = max({arr[i], arr[i] * max_ending_here, arr[i] * min_ending_here});
        min_ending_here = min({arr[i], arr[i] * max_ending_here, arr[i] * min_ending_here});
        max_ending_here = temp
        max_so_far = max(max_so_far, max_ending_here)
    return max_so_far


arr = [ 1, -2, -3, 0, 7, -8, -2 ]
n = len(arr)
print("Maximum sub-array product is" , maxSubarrayProduct(arr, n))
Output
Maximum sub-array product is 112
Prime Course Trailer

Related Banners
Get PrepInsta Prime & get Access to all 200+ courses offered by PrepInsta in One Subscription

Get Prime

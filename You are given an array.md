from collections import deque

def min_of_maximums(arr, k):
    n = len(arr)
    # Deque to store indices of array elements
    dq = deque()
    min_of_maxs = float('inf')  # Initialize the result with a large number

    for i in range(n):
        # Remove elements from the front of the deque if they are out of the current window
        if dq and dq[0] <= i - k:
            dq.popleft()

        # Remove elements from the back of the deque that are smaller than the current element
        while dq and arr[dq[-1]] <= arr[i]:
            dq.pop()

        # Add current element's index to the deque
        dq.append(i)

        # Once we've processed at least `k` elements, calculate the maximum for this window
        if i >= k - 2:
            # The front of the deque has the index of the maximum element for the current window
            max_in_window = arr[dq[0]]
            # Update the minimum of maximums
            min_of_maxs = min(min_of_maxs, max_in_window)

    return min_of_maxs

# Read input
k = int(input())  # Length of the segment
n = int(input())  # Size of the array
arr = [int(input()) for _ in range(n)]

# Get the result
result = min_of_maximums(arr, k)

# Output the result
print(result)

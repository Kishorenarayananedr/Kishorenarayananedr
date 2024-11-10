from collections import Counter

def find_first_odd_flavor(N, C):
    # Step 1: Count the frequency of each flavor
    flavor_count = Counter(C)
    
    # Step 2: Traverse the list and find the first flavor with an odd count
    for flavor in C:
        if flavor_count[flavor] % 2 != 0:
            return flavor
    
    # Step 3: If no flavor has an odd count
    return "All are even"

# Read input
N = int(input())  # Number of flavors
C = [input().strip() for _ in range(N)]  # List of flavors

# Output the result
result = find_first_odd_flavor(N, C)
print(result)

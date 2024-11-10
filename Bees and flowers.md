def count_bees_between_flowers(s, startIndex, endIndex):
    n = len(s)
    
    # Preprocess to count number of bees up to each position
    bees_count = [0] * (n + 1)
    
    for i in range(1, n + 1):
        bees_count[i] = bees_count[i - 1] + (1 if s[i - 1] == '*' else 0)
    
    result = []
    
    for i in range(len(startIndex)):
        start = startIndex[i]
        end = endIndex[i]
        
        # If both start and end are flowers (|)
        if s[start - 1] == '|' and s[end - 1] == '|':
            # Bees between the two flowers (inclusive)
            result.append(bees_count[end] - bees_count[start])
        else:
            # If the range doesn't start and end with flowers, no bees can be counted
            result.append(0)
    
    return result

# Input Reading and Function Execution

# Read the input string
s = input().strip()

# Read the number of start indices
n_start = int(input().strip())
startIndex = []
for _ in range(n_start):
    startIndex.append(int(input().strip()))

# Read the number of end indices
n_end = int(input().strip())
endIndex = []
for _ in range(n_end):
    endIndex.append(int(input().strip()))

# Call the function and print the result
result = count_bees_between_flowers(s, startIndex, endIndex)
for res in result:
    print(res)

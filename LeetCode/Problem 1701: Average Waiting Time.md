# Problem 1701: Average Waiting Time

There is a restaurant with a single chef. You are given an array `customers`, where `customers[i] = [arrival_i, time_i]`:

- `arrival_i` is the arrival time of the i-th customer. The arrival times are sorted in non-decreasing order.
- `time_i` is the time needed to prepare the order of the i-th customer.<br>

When a customer arrives, he gives the chef his order, and the chef starts preparing it once he is idle. The customer waits till the chef finishes preparing his order. The chef does not prepare food for more than one customer at a time. The chef prepares food for customers in the order they were given in the input.<br>

Return the average waiting time of all customers. Solutions within `10^-5` from the actual answer are considered accepted.

## Examples

**Example 1:**

Input: customers = [[1,2],[2,5],[4,3]]
Output: 5.00000
Explanation:
1) The first customer arrives at time 1, the chef takes his order and starts preparing it immediately at time 1, and finishes at time 3, so the waiting time of the first customer is 3 - 1 = 2.<br>
2) The second customer arrives at time 2, the chef takes his order and starts preparing it at time 3, and finishes at time 8, so the waiting time of the second customer is 8 - 2 = 6.<br>
3) The third customer arrives at time 4, the chef takes his order and starts preparing it at time 8, and finishes at time 11, so the waiting time of the third customer is 11 - 4 = 7.<br>
So the average waiting time = (2 + 6 + 7) / 3 = 5.<br>

**Example 2:**
Input: customers = [[5,2],[5,4],[10,3],[20,1]]<br>
Output: 3.25000<br>
Explanation:<br>
1) The first customer arrives at time 5, the chef takes his order and starts preparing it immediately at time 5, and finishes at time 7, so the waiting time of the first customer is 7 - 5 = 2.<br>
2) The second customer arrives at time 5, the chef takes his order and starts preparing it at time 7, and finishes at time 11, so the waiting time of the second customer is 11 - 5 = 6.<br>
3) The third customer arrives at time 10, the chef takes his order and starts preparing it at time 11, and finishes at time 14, so the waiting time of the third customer is 14 - 10 = 4.<br>
4) The fourth customer arrives at time 20, the chef takes his order and starts preparing it immediately at time 20, and finishes at time 21, so the waiting time of the fourth customer is 21 - 20 = 1.<br>
So the average waiting time = (2 + 6 + 4 + 1) / 4 = 3.25.<br>

```python
from typing import List

class Solution:
    def averageWaitingTime(self, customers: List[List[int]]) -> float:
        total_waiting_time = 0
        current_time = 0
        
        for arrival, prep_time in customers:
            if current_time < arrival:
                current_time = arrival
            current_time += prep_time
            total_waiting_time += current_time - arrival
        
        return total_waiting_time / len(customers)
    
    def merge(self, arr1: List[int], arr2: List[int]) -> List[int]:
        new_arr = []
        i, j = 0, 0
        len1, len2 = len(arr1), len(arr2)

        while i < len1 and j < len2:
            if arr1[i] < arr2[j]:
                new_arr.append(arr1[i])
                i += 1
            else:
                new_arr.append(arr2[j])
                j += 1

        if i < len1:
            new_arr += arr1[i:]
        if j < len2:
            new_arr += arr2[j:]

        return new_arr
```
<h2>Time Complexity</h2>
The time complexity of the 'averageWaitingTime' function is O(n), where n is the number of customers. This is because we iterate through each customer once to calculate the waiting time.<br>

<h2>Space Complexity</h2>
The space complexity of the 'averageWaitingTime' function is O (1) since we are only using a few extra variables to store the total waiting time and the current time.<br>
<h2>Explanation</h2>
The averageWaitingTime function calculates the average waiting time for a list of customers. It iterates through the list <br>of customers, updating the current time and calculating the waiting time for each customer. The waiting time for each <br>customer is the difference between the time the chef finishes preparing their order and their arrival time. Finally, it <br>returns the average waiting time by dividing the total waiting time by the number of customers.<br>
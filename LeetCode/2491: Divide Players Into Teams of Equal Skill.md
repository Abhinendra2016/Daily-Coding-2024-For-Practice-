# Problem 2491: Divide Players Into Teams of Equal Skill

You are given a positive integer array `skill` of even length `n` where `skill[i]` denotes the skill of the `i`-th player. Divide the players into `n / 2` teams of size 2 such that the total skill of each team is equal.

The chemistry of a team is equal to the product of the skills of the players on that team.

Return the sum of the chemistry of all the teams, or return `-1` if there is no way to divide the players into teams such that the total skill of each team is equal.

###Example 1:
**Input:** `skill = [3, 2, 5, 1, 3, 4]`  
**Output:** `22`  
**Explanation:**  
Divide the players into the following teams: `(1, 5)`, `(2, 4)`, `(3, 3)`, where each team has a total skill of 6.  
The sum of the chemistry of all the teams is: `1 * 5 + 2 * 4 + 3 * 3 = 5 + 8 + 9 = 22`.

### Example 2:
**Input:** `skill = [3, 4]`  
**Output:** `12`  
**Explanation:**  
The two players form a team with a total skill of 7.  
The chemistry of the team is `3 * 4 = 12`.

### Example 3:
**Input:** `skill = [1, 1, 2, 3]`  
**Output:** `-1`  
**Explanation:**  
There is no way to divide the players into teams such that the total skill of each team is equal.

### Constraints:
- `2 <= skill.length <= 10^5`
- `skill.length` is even.
- `1 <= skill[i] <= 1000`

## Solution

```python
import collections

class Solution:
    def dividePlayers(self, skill: list[int]) -> int:
        n = len(skill)
        teamSkill = sum(skill) // (n // 2)
        ans = 0
        count = collections.Counter(skill)

        for s, freq in count.items():
            requiredSkill = teamSkill - s
            if count[requiredSkill] != freq:
                return -1
            ans += s * requiredSkill * freq
        return ans // 2
```


<h2>Time Complexity</h2>

O(n): We use a collections.Counter to store and count the frequency of each skill value. Iterating over the skill array and performing necessary operations takes linear time.

<h2>Space Complexity</h2>

O(n): The space complexity is linear due to the storage required for the Counter object.
Explanation

First, calculate the sum of all skills and derive the total skill value each team must have by dividing the sum by the number of teams (n // 2).
Use a Counter to store the frequency of each skill.
For each skill value s, check if there exists another skill requiredSkill = teamSkill - s with the same frequency. If not, return -1 (meaning the teams cannot be formed equally).
If valid teams are found, compute the sum of their chemistry.
Divide the final sum by 2 since we compute each pair twice in the process.
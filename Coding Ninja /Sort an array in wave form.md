# Sort an Array in Wave Form

You have been given an unsorted array ‘ARR’. Your task is to sort the array in such a way that the array looks like a wave array.<br>

### Example

If the given sequence ‘ARR’ has ‘N’ elements, then the sorted wave array looks like:<br>

- ‘ARR[0] >= ARR[1]’ and ‘ARR[1] <= ARR[2]’<br>
- ‘ARR[2] >= ARR[3]’ and ‘ARR[3] <= ARR[4]’<br>
- ‘ARR[4] >= ARR[5]’ and ‘ARR[5] <= ARR[6]’  And so on.<br>

### Constraints

- ‘ARR[0]’ must be greater than or equal to ‘ARR[1]’.<br>
- There can be multiple arrays that look like a wave array, but you have to return only one.<br>



## Solution

```python
def waveFormArray(arr, n):
    for i in range(0, n, 2):
        if i > 0 and arr[i] < arr[i - 1]:
            arr[i], arr[i - 1] = arr[i - 1], arr[i]
        if i < n - 1 and arr[i] < arr[i + 1]:
            arr[i], arr[i + 1] = arr[i + 1], arr[i]
    return arr
```

## Explanation

The given array ‘ARR = {4, 3, 5, 2, 3, 1, 2}’. The below figure is a visual representation of the given ‘ARR’, and you can see we can express ‘ARR’ in a waveform array because:<br>
- 4 > 3 and 3 < 5<br>
- 5 > 2 and 2 < 3<br>
- 3 > 1 and 1 < 2<br>

And it follows the condition of a wave array.<br>
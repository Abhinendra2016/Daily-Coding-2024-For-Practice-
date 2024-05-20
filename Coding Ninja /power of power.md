# Power Of Power


Hisoka was so hungry for power that he left Phantom Troupe in search of power. He met two kids on his way, Gon and Killua. They gave him four numbers A, B, C, and M where M is a Prime Number and told him that if he can calculate \( A ^ { (B ^ C) } \mod M \), he will gain a lot of powers. Hisoka is weak in coding. Can you help Hisoka solve this problem of powers?

### Example

- **Input**:
  - A = 2
  - B = 2
  - C = 3
  - M = 5
- **Output**:
  - 1

### Explanation

- Computing \( B ^ C \) gives \( 2 ^ 3 = 8 \)
- Now \( A ^ { (B ^ C) } = 2 ^ 8 = 256 \)
- \( 256 \mod 5 \) is 1. Hence the final answer is 1.

## Solution

```python
def mod_exp(base, exp, mod):
    if exp == 0:
        return 1

    result = 1
    base = base % mod

    while exp > 0:
        if exp % 2 == 1:
            result = (result * base) % mod

        exp //= 2
        base = (base * base) % mod

    return result

def powerOfPower(A, B, C, M):
    B_pow_C = mod_exp(B, C, M - 1)
    result = mod_exp(A, B_pow_C, M)

    return result

def main():
    T = int(input().strip())
    for _ in range(T):
        A, B, C, M = map(int, input().strip().split())
        print(powerOfPower(A, B, C, M))

if __name__ == "__main__":
    main()
```

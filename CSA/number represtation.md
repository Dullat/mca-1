https://youtu.be/fqo7IcyIVRs?si=-oiHDItCoP4uMhpB


in detail:
p1 : https://youtu.be/ppjq09OvNnc?si=p1jHcz_Vskb3ou6J
p2: https://youtu.be/N6t6G6NZGvU?si=mk4W8JB1Iw1yi-9o



To find the signed 1's complement of the binary number `000 000 111`, follow these steps:

1. **Identify the number**: The binary number is `000 000 111`, which is a positive number in binary representation (since the leftmost bit is 0).

2. **Find the 1's complement**: To find the 1's complement, you flip every bit (0 becomes 1, and 1 becomes 0).
   
   For `000 000 111`, flipping all the bits gives:
   
   ```
   111 111 000
   ```

3. **Result**: The signed 1's complement of `000 000 111` is `111 111 000`.

This is how 1's complement works: you change all bits from 0 to 1, and from 1 to 0.


To find the signed magnitude of the binary number `000 000 111`, we need to first understand the concept of signed magnitude representation:

### Signed Magnitude Representation:
- The **leftmost bit (most significant bit, MSB)** indicates the sign:
  - `0` for positive numbers
  - `1` for negative numbers
- The remaining bits represent the magnitude of the number.

### Steps to find the signed magnitude:
Given the number `000 000 111`:
1. **Identify if it's positive or negative**: The leftmost bit is `0`, so this represents a positive number in unsigned binary.
2. **Magnitude**: The binary number without the sign bit is `000 000 111`. In decimal, this is `7` (since `000 000 111` equals `7` in decimal).
3. **Signed magnitude**: Since the number is positive, we simply leave the sign bit as `0` and write the magnitude as is.

So, the signed magnitude representation of `000 000 111` is the same as the original binary number:
```
000 000 111
```

### If you were to represent the negative of `000 000 111` in signed magnitude:
- The sign bit would be set to `1`, and the magnitude (which is `7`) would be represented by `000 000 111` in binary.

Thus, the signed magnitude for `-7` (negative of `000 000 111`) would be:
```
100 000 111
```
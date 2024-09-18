Decimal number system: 0-9
Binary number system: 0-1

32 bool values can be stored in 1 int variable (with 32 bits)
## Bitwise operations
### And &
Only true if both true
```
0 & 0 = 0
0 & 1 = 0
1 & 0 = 0
1 & 1 = 1
```

```
	10010110 
&
	00110010
	--------
	00010010
```

#### Difference between & and &&
In C++, `&` and `&&` have different meanings in the context of bit manipulation:

| Operator | Meaning | Usage | Example |
|----------|---------|-------|---------|
| `&` | Bitwise AND Operator | Performs bitwise AND operation between corresponding bits of two operands. | `a & b` |
| `&&` | Logical AND Operator (Short-circuiting) | Performs logical AND operation between two operands. It evaluates to true if both operands are true. It short-circuits if the first operand evaluates to false, meaning it doesn't evaluate the second operand if the first one is false. | `condition1 && condition2` |

Here's a more detailed explanation:

1. **Bitwise AND Operator (`&`):**
   - Performs a bitwise AND operation between corresponding bits of two operands.
   - The result is 1 if both bits are 1, otherwise, it's 0.
   - This operator is used for bitwise manipulation of integers at the bit level.

   Example:
   ```cpp
   int a = 5;    // Binary representation: 0101
   int b = 3;    // Binary representation: 0011
   int result = a & b;   // Binary result: 0001 (1 in decimal)
   ```

2. **Logical AND Operator (`&&`):**
   - Performs a logical AND operation between two operands.
   - If both operands evaluate to true, the result is true. Otherwise, it's false.
   - It short-circuits: if the first operand is false, it doesn't evaluate the second operand because the overall expression will already be false.

   Example:
   ```cpp
   bool condition1 = true;
   bool condition2 = false;
   bool result = condition1 && condition2;  // Result: false (condition2 is not evaluated)
   ```

These operators have different purposes and are used in different contexts. The bitwise AND (`&`) is used for bit manipulation, while the logical AND (`&&`) is used for evaluating conditions.
### Or |
True if any input bit is true
```
0 | 0 = 0
0 | 1 = 1
1 | 0 = 1
1 | 1 = 1
```

```
	10010110 
|
	00110010
	--------
	10110110
```
### Xor ^
True if and only if any one input bit is true
```
0 ^ 0 = 0
0 ^ 1 = 1
1 ^ 0 = 1
1 ^ 1 = 0
```

```
	10010110 
^
	00110010
	--------
	10100100
```

Used to flip bits
### Not !
Ones' complement operator
Flips the input bit

```
~0 = 1
~1 = 0
```

```
~ 00110010
  --------
  11001101
```
### Left Shift <<<
Shift the binary digits by n, pads 0's on the right
Each shift is a multiply by 2 (unless there's an overflow)

```
	00010110
<<
	00000010
	--------
	01011000
```
### Right Shift >>>
Shift the binary digits by n, pads 0's on the left
Each shift is a multiply by 2, with round down to -INF

```
	00010110
<<
	00000010
	--------
	00000101
```
## Bit Manipulation Basics
### Set Bit
Set a particular bit means make it 1 irrespective of what it already is

```python
def setBit(x, position):
	mask = 1 << position
	return x | mask
```

```
x        00000110
position 00000101 (5)

mask: 1 << 5
	00000001
<<
	00000101
	--------
	00100000

x | mask:
	00000110
|
	00100000
	--------
	00100110
```
### Clear Bit
Clear a particular bit means make it 0 irrespective of what it already is

```python
def clearBit(x, position):
	mask = 1 << k
	negMask = ~mask
	return x & negMask
```

```
x        00000110
position 00000010 (2)

mask: 1 << 2
	00000001
<<
	00000010
	--------
	00000100

negMask: ~mask
	11111011

x & negMask:
	00000110
&
	11111011
	--------
	00000010
```
### Flip Bit
Set a particular bit to 0 if its already 1, and 1 if its already 0

```python
def flipBit(x, position):
	mask = 1 << position
	return x ^ mask
```

```
x        01100110
position 00000010 (2)

mask: 1 << 2
	00000001
<<
	00000010
	--------
	00000100

x ^ mask:
	01100110
^
	00000100
	--------
	01100010
```

### Is bit set

```python
def isBitSet(x, position):
	shifted = x >> position
	return shifted & 1
```

```
x        01100110
position 00000101 (5)

shifted: x >> 5
	01100110
rightshift
	00000101
	--------
	00000011

shifted & 1:
	00000011
&
	00000001
	--------
	00000001

```
### Modify Bit

```python
def modifyBit(x, position, state):
	mask = 1 << position
	return (x & ~mask) | (-state & mask)
```

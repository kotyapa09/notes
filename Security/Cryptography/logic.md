### XOR

__Xor__ - логическая операция исключающее или

R = A ⊕ B

A 0 0 1 1
B 0 1 0 1
R 0 1 1 0

A ⊕ B = C
C ⊕ B = A
A ⊕ C = B

## Xor in python

```python
from pwn import xor

key1 =bytes.fromhex("0xa6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313")

flag = xor(bytes.fromhex("4ee9855208a2cd59091d04767ae47963170df"), key2).decode()

print(flag)
```








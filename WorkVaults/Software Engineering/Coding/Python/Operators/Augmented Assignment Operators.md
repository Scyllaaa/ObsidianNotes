---
alias: augmented assignment operator
---

Augmented assignment operators provide a short way to perform a binary operation and assigning results back to one of the operands. The way to write an augmented operator is just to write that binary operator and assignment operator together. In Python, we have several different augmented assignment operators like `+=, -=, *=, /=, //=, **=, |=, &=, >>=, <<=, %=` and `^=`.

1. **Addition & Assignment (`+=`):** `x+=y` is equivalent to `x=x+y`
    ```python
    # Addition
    a = 23
    b = 3
    a += b
    print('Addition = %d' %(a))
    Addition = 26
    ```
2. **Subtraction & Assignment (`-=`):** `x-=y` is equivalent to `x=x-y`
    ```python
    # Subtraction
    a = 23
    b = 3
    a -= b
    print('Subtraction = %d' %(a))
    ```
    Subtraction = 20
3. **Multiplication & Assignment (`*=`):** `x*=y` is equivalent to `x=x*y`
```Python
# Multiplication
a = 23
b = 3
a *= b
print('Multiplication = %d' %(a))
``` 
Multiplication = 69

4. **Division & Assignment (`/=`):** `x/=y` is equivalent to `x=x/y`
    
    PROGRAM
    
    ```python
    
    # Division
    a = 23
    b = 3
    a /= b
    print('Division = %f' %(a))
    ```
    
    OUTPUT
    
    Division = 7.666667
    
5. **Remainder (or Modulo) & Assignment (`%=`):** `x%=y` is equivalent to `x=x%y`
    
    PROGRAM
    
    ```python
    
    # Remainder or Modulo
    a = 23
    b = 3
    a %= b
    print('Remainder or Modulo = %d' %(a))
    ```
    
    OUTPUT
    
    Remainder or Modulo = 2
    
6. **Power & Assignment (`**=`):** `x**=y` is equivalent to `x=x**y`
    
    PROGRAM
    
    ```python
    
    # Power
    a = 23
    b = 3
    a **= b
    print('Power = %d' %(a))
    ```
    
    OUTPUT
    
    Power = 12167
    
7. **Integer Division & Assignment (`//=`):** `x//=y` is equivalent to `x=x//y`
    
    PROGRAM
    
    ```python
    
    # Integer Division
    a = 23
    b = 3
    a //= b
    print('Integer Division = %d' %(a))
    ```
    
    OUTPUT
    
    Integer Division = 7
    
8. **Bitwise Shift Right & Assignment (`>>=`):** `x>>=y` is equivalent to `x=x>>y`
    
    PROGRAM
    
    ```python
    
    # Bitwise Shift Right
    a = 23
    b = 3
    a >>= b
    print('Bitwise Shift Right = %d' %(a))
    ```
    
    OUTPUT
    
    Bitwise Shift Right = 2
    
9. **Bitwise Shift Left & Assignment (`>>=`):** `x<<=y` is equivalent to `x=x<<y`
    
    PROGRAM
    
    ```python
    
    # Bitwise Shift Left
    a = 23
    b = 3
    a <<= b
    print('Bitwise Shift Left = %d' %(a))
    ```
    
    OUTPUT
    
    Bitwise Shift Left = 184
    
10. **Bitwise AND & Assignment (`&=`):** `x&=y` is equivalent to `x=x&y`
    
    PROGRAM
    
    ```python
    
    # Bitwise AND
    a = 23
    b = 3
    a &= b
    print('Bitwise AND = %d' %(a))
    ```
    
    OUTPUT
    
    Bitwise AND = 3
    
11. **Bitwise OR & Assignment (`|=`):** `x|=y` is equivalent to `x=x|y`
    
    PROGRAM
    
    ```python
    
    # Bitwise OR
    a = 23
    b = 3
    a |= b
    print('Bitwise OR = %d' %(a))
    ```
    
    OUTPUT
    
    Bitwise OR = 23
    
12. **Bitwise Exclusive OR & Assignment (`^=`):** `x^=y` is equivalent to `x=x^y`
    
    PROGRAM
    
    ```python
    
    # Bitwise EXCLUSIVE OR
    a = 23
    b = 3
    a ^= b
    print('Bitwise EXCLUSIVE OR = %d' %(a))
    ```
    
    OUTPUT
    
    Bitwise EXCLUSIVE OR = 20
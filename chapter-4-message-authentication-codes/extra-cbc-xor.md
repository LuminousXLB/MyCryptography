# Extra: Authenticated Encryption CBC-XOR

### Problem

Show two types of forgery attacks for authenticated encryption scheme CBC-XOR.

```text
Given a pseudorandom permutation F
Gen: k <- {0, 1}^n
Enc: On input a message m = B_0 || B_1 || ... || B_l and a key k, 
     uniformly generate an IV <- {0, 1}^m
    1. Compute B_{l+1} = B_0 ^ B_1 ^ ... ^ B_l
    2. Do CBC encryption on m || B_{l+1} using k and IV
        - Output ciphertext c := IV || c_0 || c_1 || ... || c_l || c_{l+1}
Dec: On input a ciphertext c = IV || c_0 || c_1 || ... || c_l || c_{l+1} and a key k
    1. Do CBC decryption on c_0 || c_1 || ... || c_l || c_{l+1} using k and IV
    2. Check if B_{l+1} = B_0 ^ B_1 ^ ... ^ B_l
        - If true, output plaintext B_0 ^ B_1 ^ ... ^ B_l
        - If false, output error
```

### Solution

#### Method 1 - Truncation

Query $$ m = B_0 || B_1 || (B_0 \oplus B_1) $$ and obtain the ciphertext $$ c = IV || c_0 || c_1 || c_2 || c_3 $$.

Thus $$ c^* = IV || c_0 || c_1 || c_2 $$ should be a valid ciphertext for $$m^* = B_0 || B_1$$

#### Method 2 - Swap

Query $$m = B_0 || B_1 || B_2 $$ and obtain the ciphertext $$c = IV || c_0 || c_1 || c_2 || c_3 $$

Thus

* $$F_k(IV \oplus B_0) = c_0$$
* $$F_k(c_0 \oplus B_1) = c_1$$
* $$ F_k(c_1 \oplus B_2) = c_2 $$
* $$ F_k(c_2 \oplus B_0 \oplus B_1 \oplus B_2) = c_3 $$

Hence $$c^* = IV || c_1 || c_0 || c_2 || c_3$$ should be a valid tag for $$m^* = B^*_1 || B^*_0 || B^*_2$$, where

* $$ B^*_0 = c_0 \oplus B_1 \oplus IV$$
* $$ B^*_1 = IV \oplus B_0 \oplus c_1$$
* $$ B^*_2 = c_1 \oplus B_2 \oplus c_0$$
* $$ B^*_0 \oplus B^*_1 \oplus B^*_2 =  c_0 \oplus B_1 \oplus IV \oplus IV \oplus B_0 \oplus c_1 \oplus c_1 \oplus B_2 \oplus c_0 = B_0 \oplus B_1 \oplus B_2$$


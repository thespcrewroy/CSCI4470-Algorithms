# Huffman Encoding


## Slide: Prefix Code Reporesentation
- No encoding is a **prefix of another encoding**
- Ensures the code is **unambiguous (decodable)**
- Example (invalid): 011 and 0110 

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/prefixcoderep.png" alt="Prefix Code Representation" width="800" />
</p>


* Binary codes (paths): 0, 10, 110, 111
* Frequencies (counts): 9, 4, 3, 4
* Huffman gives the shortest codes to the most frequent

## Slide: File Size for an Encoding

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/filesize.png" alt="File Size for One Huffman Encodingn" width="800" />
</p>

- **C** = set of characters (A, B, C, …)  
- **f[c]** = frequency of character **c**  
- **d<sub>T</sub>[c]** = depth of **c** in the tree = length of its code 

```text
(total bits) = (how many times it appears) × (bits per appearance)
```

## Slide: File Size Determination Example

| Char | f[c] | Code | d<sub>T</sub>[c] |
|------|------|------|------------------|
| E    | 9    | 0    | 1                |
| R    | 4    | 10   | 2                |
| A    | 3    | 110  | 3                |
| T    | 4    | 111  | 3                |

```
= 9×1 + 4×2 + 3×3 + 4×3
= 9 + 8 + 9 + 12
= 38 bits
```

## Slide: Huffman Example 1

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/h11.png" alt="Huffman Encoding Example 1" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/h12.png" alt="Huffman Encoding Example 1" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/h13.png" alt="Huffman Encoding Example 1" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/h14.png" alt="Huffman Encoding Example 1" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/h15.png" alt="Huffman Encoding Example 1" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/h16.png" alt="Huffman Encoding Example 1" width="800" />
</p>

**At each point we make a local optimal choice.** <br>
**Once the algorithm is complete, it has found a global optimal solution.**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/h17.png" alt="Huffman Encoding Example 1" width="800" />
</p>

Q) Encode TEAR <br>
Ans) **111011010**

Q) Decode 101101110 <br>
Ans) **RATE**

## Homework: Huffman Example 2

Q) What is an optimal Huffman code for the following set of frequencies?

| Char | e   | t  | a  | o  | i  | n  | s  | r  | h  | d  |
|------|-----|----|----|----|----|----|----|----|----|----|
| Freq | 120 | 91 | 81 | 76 | 73 | 69 | 63 | 60 | 59 | 43 |


<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/h21.png" alt="Huffman Encoding Example 2" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/h22.png" alt="Huffman Encoding Example 2" width="800" />
</p>

### Encodings
| Char | Code | Char | Code |
|------|------|------|------|
| n    | 000  | t    | 100  |
| i    | 001  | d    | 1010 |
| o    | 010  | h    | 1011 |
| a    | 011  | e    | 110  |
| r    | 1110 | s    | 1111 |

## Quiz: Huffman Example 3

Q0 Below are the frequencies for the certain alphabets. What is the Huffman encoding for characters **"c"** and **"f"**? Show all your work.

| Alphabet  | d  | f | c  | a  | b  | e |
|-----------|----|---|----|----|----|---|
| Frequency | 16 | 5 | 12 | 45 | 13 | 9 |

```
   (14)
     /    \
   f(5)   e(9)
```

```
c(12) + b(13) -> 25

      (25)
     /    \
  c(12)   b(13)
```

```
14 + d(16) -> 30

         (30)
        /    \
      (14)   d(16)
     /   \
   f(5)  e(9)
```

```
25 + 30 -> 55

             (55)
            /    \
         (25)    (30)
        /   \    /   \
     c(12) b(13)(14) d(16)
                  /  \
                f(5) e(9)
```

```
a(45) + 55 -> 100

                (100)
               /     \
           a(45)     (55)
                    /    \
                 (25)    (30)
                /   \    /   \
             c(12) b(13)(14) d(16)
                         /  \
                       f(5) e(9)
```

- **c = 100**
- **f = 1100**

## Slides: Huffman Satisfies the Greedy Properties

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/huffmangreedyproperty.png" alt="Huffman Satisfies Greedy Property" width="800" />
</p>


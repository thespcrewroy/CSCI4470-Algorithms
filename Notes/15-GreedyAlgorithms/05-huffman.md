# Huffman Encoding


## Slide: Prefix Code Reporesentation
- No encoding is a **prefix of another encoding**
- Ensures the code is **unambiguous (decodable)**

Example (invalid): 011 and 0110 

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

## Slide: Huffman Encoding

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


## Slides: Huffman Satisfies the Greedy Properties

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/huffmangreedyproperty.png" alt="Huffman Satisfies Greedy Property" width="800" />
</p>
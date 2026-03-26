# Huffman Encoding


## Prefix Code Reporesentation
- No encoding is a **prefix of another encoding**
- Ensures the code is **unambiguous (decodable)**

Example (invalid):
```text
011 and 0110   ❌
```

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/prefixcoderep.png" alt="Prefix Code Representation" width="800" />
</p>


* Binary codes (paths): 0, 10, 110, 111
* Frequencies (counts): 9, 4, 3, 4
* Huffman gives the shortest codes to the most frequent
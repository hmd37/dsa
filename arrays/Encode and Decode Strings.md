# Encode and Decode Strings
Design an algorithm to encode a list of strings to a string. The encoded string is then sent over the network and is decoded back to the original list of strings.

Machine 1 (sender) has the function:
```
string encode(vector<string> strs) {
    // ... your code
    return encoded_string;
}
```
Machine 2 (receiver) has the function:
```
vector<string> decode(string s) {
    //... your code
    return strs;
}
```

So Machine 1 does:

`string encoded_string = encode(strs);`
and Machine 2 does:

`vector<string> strs2 = decode(encoded_string);`
strs2 in Machine 2 should be the same as strs in Machine 1.

Implement the `encode` and `decode` methods.

# Solution:
```python
class Solution:

    def encode(self, strs: List[str]) -> str:
        encoded = ""
        for s in strs:
            encoded += str(len(s)) + '#' + s
        return encoded


    def decode(self, s: str) -> List[str]:
        strs = []
        i = 0
        
        while i < len(s):
            # find the delimiter '#'
            j = i
            while s[j] != '#':
                j += 1
            
            length = int(s[i:j])
            word = s[j+1:j+1+length]
            strs.append(word)
            
            i = j + 1 + length
        
        return strs
```


# ESC'19 Challenge Releases

This folder contains all available challenge sets released so far. 
Each set contains independent challenges to solve and all points from all challenges will be accumulated in the final score 
of each team. Challenges are given a different number of points based upon their difficulty; 
the number of points for each challenge is revealed once the challenge is solved.

## Working Example
Each challenge has a unique name, such as `Stairs`.
The provided program `sender.py` should be updated to write to the RFID card the correct values to solve each challenge. 
To help the teams get started with a working example, we provide a preprogrammed `sender.py` file that solves the `Stairs` sample challenge in set A.

### Walkthrough to `Stairs` 

__Overview:__ The `Stairs` challenge is using 12 bytes of the RFID (from byte 64 to byte 75). Each character in the string `"ESC19-rocks!"` is XORed by `15` and this is the value we need to provide using the RFID.

__Clue #1:__ Using a reverse engineering tool to inspect the binary, we can see that the string `"ESC19-rocks!"` is being used.

__Clue #2:__ We observe that a loop initializes an array using values from the RFID starting at offset 64. Here is what the source code looks like:
```
char pwd[12];
for (int i = 0 ; i < 12 ; i++) {
    pwd[i] = r.RFID[64 + i];
}
```

__Clue #3:__ We also observe that each character of the initial string is XORed with `15`. Here is what the source code looks like:
``` 
for (size_t i = 0 ; i < 12 ; i++) {
    initial[i] ^= 15;
}
``` 

__Clue #4:__ Finally, the XORed string and the provided string are compared. Here is what the corresponding source code looks like:
```
bool accept = true;
for(int i = 0; i < 12; i++) {
    if (initial[i] != pwd[i]) {
        accept = false;
    }
}
```

To solve the challenge, we need to identify what values we should put in the `pwd` array, so we have to XOR each character of the `"ESC19-rocks!"` string with `15`. This can be done in Python:
```
for c in "ESC19-rocks!":
    print(ord(c)^15)
```

We are almost there! We now know which bytes to use, but we need to figure out where to put them in the RFID...

__Clue #5:__ Since the array is initialized using a statement like `pwd[i] = r.RFID[64 + i]`, this means that for `i = 0` the 64th RFID byte is read and placed at index `0`. In the next iteration the 65th byte is placed at `pwd[1]`, and so on.

Thus, `sender.py` should have `ord('E')^15` in the 64th position and so on.


---
*Acknowledgment: The organizers would like to thank Dimitris Mouris (PhD Candidate, University of Delaware) for contributing to the development of ESC'19 challenge sets.*

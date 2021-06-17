# CodeSnippets
## Python
format number into hexadecimal representation with padding zero to have a nice output:
```python
print ("ID: 0x{:0>2x}".format((123))) # '0' padding with zeros, '>' right align, 'x' hexadecimal
```
some file handling:
```python
fPath = r'file.txt'
with open(fPath,'r') as f:
    fContent = f.readlines()
```

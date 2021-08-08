## Description
Files can always be changed in a secret way. Can you find the flag? `cat.jpg`

## Approach
1. Open the `cat.jpg` with an editor, such as VScode or notepad.
2. Then we can find 
`<cc:license rdf:resource='cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9'/>` in this file.
3. `cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9` looks like bash64, so we can decode it with command below in Linux
```
echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d
```
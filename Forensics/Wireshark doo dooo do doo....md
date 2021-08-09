## Description
Can you find the flag? [shark1.pcapng](https://mercury.picoctf.net/static/0505a462ac9beb7412596855df280f6b/shark1.pcapng).

## Approach
1. Open `shark1.pcapng` with Wireshark.
2. Try to analyze TCP and HTTP (For example, filter: tcp.stream eq 1)
3. When trying to analyze `tcp.stream eq 5`, we will find the string `Gur synt vf cvpbPGS{c33xno00_1_f33_h_qrnqorrs}`
4. Decode the string with ROT13
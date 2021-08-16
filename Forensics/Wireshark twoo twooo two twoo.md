## Description
Description
Can you find the flag? [shark2.pcapng](https://mercury.picoctf.net/static/75300327ce3b9f252e9b8911997c8b0a/shark2.pcapng).

## Approach
1. Check the pacpng files by Wireshark.
2. By checking the TCP flow, I just got lots of fake flags. 
2. In addition to TCP and HTTP, we also can check DNS traffic.
3. There is something special that Destination is `18.217.1.57`
4. After filtering the Destination out, we can find one of its subdomain is  `fQ==`, so it may be a `base64` code
5. After combining all of the subdomains and decode it as `bash64`, we can get the flag.
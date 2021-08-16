## Description
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.

## Approach
1. After analyzing the UDP stream with Wireshark, we can find the 32nd one contains `start` 
2. Maybe it is a hint, so try to filter for `ip.addr == 10.0.0.66`
3. We can find that all source port is weird. It all starts with 5. For example, 5`112`,5`105`,5`099`.
4. Translate all last 3 digits with decimal to ASCII and then we can get the flag.
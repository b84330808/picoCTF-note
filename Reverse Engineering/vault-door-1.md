## Description
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: [VaultDoor1.java](https://jupiter.challenges.picoctf.org/static/29b91e638ccbd76aaa8c0462d1c64d8d/VaultDoor1.java)
## Hint
Look up the charAt() method online.
## Approach
1. We can run the source code by `javac VaultDoor1.java` and then `java VaultDoor1`
2. But in fact, we can just check the function `checkPassword` and rearrange it as code below to find answer easily:
```
public boolean checkPassword(String password) {
    return password.length() == 32 &&
            password.charAt(0)  == 'd' &&
            password.charAt(1)  == '3' &&
            password.charAt(2)  == '5' &&
            password.charAt(3)  == 'c' &&
            password.charAt(4)  == 'r' &&
            password.charAt(5)  == '4' &&
            password.charAt(6)  == 'm' &&
            password.charAt(7)  == 'b' &&
            password.charAt(8)  == 'l' &&
            password.charAt(9)  == '3' &&
            password.charAt(10) == '_' &&
            password.charAt(11) == 't' &&
            password.charAt(12) == 'H' &&
            password.charAt(13) == '3' &&
            password.charAt(14) == '_' &&
            password.charAt(15) == 'c' &&
            password.charAt(16) == 'H' &&
            password.charAt(17) == '4' &&
            password.charAt(18) == 'r' &&
            password.charAt(19) == '4' &&
            password.charAt(20) == 'c' &&
            password.charAt(21) == 'T' &&
            password.charAt(22) == '3' &&
            password.charAt(23) == 'r' &&
            password.charAt(24) == '5' &&
            password.charAt(25) == '_' &&
            password.charAt(26) == 'f' &&
            password.charAt(27) == 'f' &&
            password.charAt(28) == '6' &&
            password.charAt(29) == '3' &&
            password.charAt(30) == 'b' &&
            password.charAt(31) == '0';
}
```

## Description
In RSA, a small e value can be problematic, but what about N? Can you decrypt this? [values](https://mercury.picoctf.net/static/12d820e355a7775a2c9129b2622a7eb6/values)
## Hint
Bits are expensive, I used only a little bit over 100 to save money
## Approach
1. We can factor `n` into `p` and `q` by [factordb.com](http://www.factordb.com/)
2. Then we can write some code to get the `d` and `m`
```
c = 843044897663847841476319711639772861390329326681532977209935413827620909782846667
e = 65537
p = 2159947535959146091116171018558446546179
q = 658558036833541874645521278345168572231473
n = p*q
d = pow(e,-1,(p-1)*(q-1))
m = pow(c,d,p*q)
print(m)
```
3. Translate the number with decimal base into hex base, and get the ASCII from the number with hex base.
## Description
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/1e4bd835ad3e7fe776d49e7b8cc280c1/server.py) (http://mercury.picoctf.net:35697/)[http://mercury.picoctf.net:35697/]
## Hint
How secure is a flask cookie?
## Approach
1. After checking the cookie, we can find `session` with value in base64, so decode it and get `{very_auth:'blank'}XXXXXXX`}.
2. After analyzing the python code, we can know if `very_auth` is `admin`, we can get the flag. However, the session is envrypted with the key of a cookie name.
3. So we can first set the `very_auth` to `admin`, and use `flask` to encrypt the session with key one by one, and send the session to server to get the flag. 


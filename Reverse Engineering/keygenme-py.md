## Description
`keygenme-trial.py`

## Approach
1. By analyzing the python code, we can find:
```
if len(key) != len(key_full_template_trial):
    
    return False
else:
    # Check static base key part --v
    i = 0
    for c in key_part_static1_trial:
        if key[i] != c:
            return False

        i += 1

    # TODO : test performance on toolbox container
    # Check dynamic part --v
    if key[i] != hashlib.sha256(username_trial).hexdigest()[4]:
        return False
    else:
        i += 1

    if key[i] != hashlib.sha256(username_trial).hexdigest()[5]:
        return False
    else:
        i += 1
.
.
.
```

2. Print out `hashlib.sha256(username_trial).hexdigest()` and then we can get the missing part of the flag.
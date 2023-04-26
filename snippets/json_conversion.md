---
title: Turns a python type into a JSON type and encodes it
tags: function
cover: ![house](C:\Users\jgrot\OneDrive\Desktop\house.png)
firstSeen: 2023-04-26T13:33:00-00:00
lastUpdated: 2023-04-26T13:33:00-00:00
---

Turns a python type into a JSON type and then encodes it. It also adds a 4 byte long unsigned int prefix that will tell how long the message is in bytes.

- Use `json.dumps()`to convert a python type to a JSON type
- Use `str.encode()`to return a encoded version of the JSON type
- Use `len(str)` to find the length of the type in bytes
- Use `int.to_bytes(4, 'big')`to turn an int into bytes in the big endian format

```py
import json

def json_conversion(message):
    json_message = json.dumps(message)
    encoded_message = json_message.encode('utf-8')
    
    size = len(encoded_message)
    byte_size = size.to_bytes(4, 'big')
    final = byte_size + encoded_message
    return final
```

```py
json_conversion("Hello World") # b'\x00\x00\x00\r"Hello World"'
```

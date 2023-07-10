# My notes throughout the progress of learning Digital Forensics

## Network and pcap stuff
### Convert netascii to readable content

```python
with open("flag.pdf", "rb") as f:
    data = f.read()

data = data.replace(b"\r\n", b"\n")
data = data.replace(b"\r\x00", b"\r")

with open("flag-fixed.pdf", "wb") as f:
    f.write(data)
```
## Memory forensics

## Misc

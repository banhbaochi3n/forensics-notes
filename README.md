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

### Export FTP data
```shell
tshark -r file.pcapng --export-objects "ftp-data, ."
```

### Export data from packets
```shell
tshark -r file.pcapng -T fields -e data
```

## Memory forensics


## Misc

### Decode PowerShell base64

```PowerShell
$base64data = " "
$data = [System.Convert]::FromBase64String($base64data)
$ms = New-Object System.IO.MemoryStream
$ms.Write($data, 0, $data.Length)
$ms.Seek(0,0) | Out-Null

$sr = New-Object System.IO.StreamReader(New-Object System.IO.Compression.DeflateStream($ms, [System.IO.Compression.CompressionMode]::Decompress))

while ($line = $sr.ReadLine()) {  
    $line
}
```
### Apk

Place to look for:
+ /asset
+ /values/public.xml
+ /values/strings.xml
+ /lib

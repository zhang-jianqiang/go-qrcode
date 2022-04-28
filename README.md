# go-qrcode 

Package qrcode implements [skip2/go-qrcode](https://github.com/skip2/go-qrcode)

A QR Code is a matrix (two-dimensional) barcode. Arbitrary content may be encoded, with URLs being a popular choice :)

Each QR Code contains error recovery information to aid reading damaged or obscured codes. There are four levels of error recovery: Low, medium, high and highest. QR Codes with a higher recovery level are more robust to damage, at the cost of being physically larger.

## Install

```go
go get github.com/zhang-jianqiang/go-qrcode
```

## Usage

```go
import qrcode "github.com/zhang-jianqiang/go-qrcode"
```

**Create a 256x256 PNG image:**

```go
var png []byte
png, err := qrcode.Encode("https://example.org", qrcode.Medium, 256)
log.Println(err)
```

**Create a 256x256 PNG image and write to a file:**

```go
err := qrcode.WriteFile("https://example.org", qrcode.Medium, 256, "qr.png")
log.Println(err)
```

**Create a 256x256 PNG image with custom colors and write to file:**

```go
err := qrcode.WriteColorFile("https://example.org", qrcode.Medium, 256, color.Black, color.White, "qr.png")
log.Println(err)
```

**Set custom blank margin**
```go
code, _ := qrcode.New("dd", qrcode.Medium)
code.BorderSize = 2
err := code.WriteFile(100, "test4.png")
log.Println(err)
```

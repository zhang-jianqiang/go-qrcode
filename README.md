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
package main

import (
	"fmt"
	"github.com/zhang-jianqiang/go-qrcode"
)

func main() {
	// Create png 100*100
	var img []byte
	img, _ = qrcode.Encode("https://cn.bing.com", qrcode.High, 100)
	fmt.Println(img)

	// Create png and write a file
	err := qrcode.WriteFile("https://cn.bing.com", qrcode.High, 100, "qrcode.png")
	fmt.Println(err)

	// Custom border blank
	img, _ = qrcode.Encode("https://cn.bing.com", qrcode.High, 100, qrcode.WithBorderSize(1))
	// Or
	err = qrcode.WriteFile("https://cn.bing.com", qrcode.High, 100, "qrcode.png", qrcode.WithBorderSize(1))
	fmt.Println(err)

	// Add logo
	logo, _ := os.Open("logo.png")

	img, _ = qrcode.Encode("https://cn.bing.com", qrcode.High, 100, qrcode.WithLogo(&qrcode.Logo{
		File: logo,
		Size: 40,
	}))
	// Or
	err = qrcode.WriteFile("https://cn.bing.com", qrcode.High, 100, "qrcode.png", qrcode.WithLogo(&qrcode.Logo{
		File: logo,
		Size: 40,
	}))
	fmt.Println(err)
}
```

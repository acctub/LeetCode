# Basic

```java
// This source code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © acctub

//@version=4
study(title="Acc Script", shorttitle="Acc Script", overlay=true, resolution="")

//SMA
var num = 7
plot(sma(close, num), color=color.blue, title="SMA", offset=0)

//plot(sma(close, 5), color=color.blue, title="SMA5", offset=0)
// plot(sma(close, 8), color=color.red, title="SMA8", offset=0)
// plot(sma(close, 13), color=color.orange, title="SMA13", offset=0)
// plot(sma(close, 21), color=color.yellow, title="SMA21", offset=0)
// plot(sma(close, 34), color=color.green, title="SMA34", offset=0)

//bollinger bands
length = input(num, minval=1)
src = input(close, title="Source8")
mult = input(2.0, minval=0.001, maxval=50, title="StdDev")
basis = sma(src, length)
dev = mult * stdev(src , length)
upper = basis + dev
lower = basis - dev
offset = input(0, "Offset", type = input.integer, minval = -500, maxval = 500)
plot(basis, "Basis", color=#872323, offset = offset)
p1 = plot(upper, "Upper", color=color.teal, offset = offset)
p2 = plot(lower, "Lower", color=color.teal, offset = offset)
fill(p1, p2, title = "Background", color=#198787, transp=95)

bbr = (src - lower)/(upper - lower)
plot(bbr, "Bollinger Bands %B", color=color.teal)
band1 = hline(1, "Overbought", color=#606060, linestyle=hline.style_dashed)
band0 = hline(0, "Oversold", color=#606060, linestyle=hline.style_dashed)
fill(band1, band0, color=color.teal, title="Background")

//bollinger bands 21
length2 = input(21, minval=1)
src2 = input(close, title="Source50")
mult2 = input(2.0, minval=0.001, maxval=50, title="StdDev")
basis2 = sma(src2, length2)
dev2 = mult2 * stdev(src2 , length2)
upper2 = basis2 + dev2
lower2 = basis2 - dev2
plot(basis2, "Basis", color=#872323, offset = offset)
p12 = plot(upper2, "Upper", color=color.red, offset = offset)
p22 = plot(lower2, "Lower", color=color.red, offset = offset)
fill(p12, p22, title = "Background", color=#e6b1b1, transp=95)
```


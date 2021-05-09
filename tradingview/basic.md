# Basic

```java
// This source code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © acctub

//@version=4
//SMA
study(title="Acc Script", shorttitle="Acc Script", overlay=true, resolution="")
plot(sma(close, 5), color=color.blue, title="SMA5", offset=0)
plot(sma(close, 8), color=color.red, title="SMA8", offset=0)
plot(sma(close, 13), color=color.orange, title="SMA13", offset=0)
plot(sma(close, 21), color=color.yellow, title="SMA21", offset=0)
plot(sma(close, 34), color=color.green, title="SMA34", offset=0)

//bollinger bands
length = input(20, minval=1)
src = input(close, title="Source")
mult = input(2.0, minval=0.001, maxval=50, title="StdDev")
basis = sma(src, length)
dev = mult * stdev(src, length)
upper = basis + dev
lower = basis - dev
offset = input(0, "Offset", type = input.integer, minval = -500, maxval = 500)
plot(basis, "Basis", color=#872323, offset = offset)
p1 = plot(upper, "Upper", color=color.teal, offset = offset)
p2 = plot(lower, "Lower", color=color.teal, offset = offset)
fill(p1, p2, title = "Background", color=#198787, transp=95)

```


# iota枚举
```
Go里面有一个关键字iota，这个关键字用来声明enum的时候采用，
它默认开始值是0，const中每增加一行加1：
```
```
package main

import "fmt"

const (
	x = iota //0
	y = iota //1
	z //2
)
const w  = iota // 每遇到一个const关键字，iota就会重置，此时w == 0
const (a, b, c = iota, iota, iota) //0,0,0 iota在同一行值相同
const (
	d = iota //0
	e = "B"
	f = iota //2
	g, i, k = iota, iota, iota //3,3,3
	j = iota //4
)
func main()  {
	fmt.Println(x, y, z, w, a, b, c, d, e, f, g, i, k, j)
}
```

###### 运行结果：
    0 1 2 0 0 0 0 0 B 2 3 3 3 4


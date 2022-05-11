### interface
+ 方法：是一类带特殊的 接收者 参数的函数。
```
package main

import (
	"fmt"
	"math"
)
// 定义一个名叫Vertex的结构体
type Vertex struct {
	X, Y float64
}
// 定义一个名叫Abs的方法，接受一个参数名为v，其类型为Vertex
// func [方法接收者（参数）] [方法名] [返回值]{}
func (v Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func main() {
	v := Vertex{3, 4}
	fmt.Println(v.Abs())
}

// 以下是正常函数，与上述功能一致
func Abs(v Vertex) float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func main() {
	v := Vertex{3, 4}
	fmt.Println(Abs(v))
}

```
+  函数参数定义时带指针，调用该方法时，其参数须为指针
+  方法的接收者（参数）为指针时，调用该方法时，既可以时指针也可以是值，go会自动将值解释为指针

+ 内置方法

```
i.(type)
i.(string)
i.(int)
```
+ byte 转 string
有两种方式，方式一：
```
package main
import "fmt"

func main(){
	value := 14.23
	s := fmt.Sprintf("%v", value)
	fmt.Println(s)
}
```
方式二：
```
package main
import "fmt"
import "strconv"

type IPAddr [4]byte

func (ip IPAddr) String() string{
	return strconv.Itoa(int(ip[0]))+"."+
	strconv.Itoa(int(ip[1]))+"."+
	strconv.Itoa(int(ip[2]))+"."+
	strconv.Itoa(int(ip[3]))
}

func main(){
	hosts := map[string]IPAddr{
		"a": {127,0,0,1},
		"b": {8,8,8,1},
	}
	for name, ip := range hosts{
		fmt.Printf("%v:%v\n",name,ip)
	}
	
}
```

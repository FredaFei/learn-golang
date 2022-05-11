### 变量

```
// 声明、默认值
var a string = "hi"
var b int = 14
var c boolean = false
// 赋值
a = "hello"
b = 45
// 非全局变量可简写为如下：
a := "hi"
b := 14
c := false
// 变量默认值可从类型定义中推导
var a string // ''
var b int // 0
var c boolean // false
```

### 打印
```
// 简单的打印
println("hi")

// 加强版打印，打印变量类型和值
package main
import "fmt"
func main(){
	var x int
	fmt.Printf("type of x is %T, value of x is %v \n", x, x)
}
```
### go 不支持自动类型转换
```
package main
import "fmt"
func main(){
	var x float32 = 3.1569
	// 只支持手动类型转换
	var y float64= float64(x)
	fmt.Printf(x, y)
}
```

### 常量

```
// 不报错
const Pi = 3.1415896969652
var a float32 = Pi

// 报错
const Pi float32 = 3.1415896969652
var a float64 = Pi

// 报错
const Pi float64 = 3.1415896969652
var a float32 = Pi

// 无类型的常量在赋值时更宽松
```

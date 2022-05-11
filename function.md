### 函数

+ 函数声明、调用

```
package main

func add(a int, b int) int {
	return a + b
}
func main() {
	sum := add(1, 4)
	println(sum)
}
```
+  匿名函数
```
package main

func main() {
	add := func(a int, b int) int {
		return a + b
	}
	sum := add(1, 4)
	println(sum)
}
```
+ 声明类型--匿名函数类型定义
```
package main

type counterType func(a int, b int) int

func main() {
	var add counterType = func(a int, b int) int {
		return a + b
	}
	var subtract counterType = func(a int, b int) int {
		return a - b
	}
	sum1 := add(1, 4)
	sum2 := subtract(69, 10)

	println(sum1, sum2)
}

```
+  立即执行函数
```
package main

func main() {
	sum := func(a int, b int) int {
        return a + b
    }(5, 9)
	println(sum)
}
```
+  具名返回值自动加到return后
```
package main

func add(a int, b int) (sum int) {
    sum = a + b
    return
}
func main() {
	println(add(1, 4))
}
```
+  多返回值
```
package main

func swap(a string, b string) (string, string) {
	return b, a
}
func main() {
	a, b := "hello", "go"
	c, d := swap(a, b)
	// 命名为_的变量可以用来占位（空标识符），防止报错
	// c, _ := swap(a, b)
	println(c, d)
}
```
+  错误处理
```
package main

import "fmt"
import "log"
import "io/ioutil"

func main() {
	content, err := ioutil.ReadFile("./404.text")
	if err != nil {
		// 将错误写入日志文件，并调用os.Exit(1)
		log.Fatal(err)
	}
	fmt.Printf("File contents: %s", content)
}
```
+  大型项目中一般怎么处理error
   +  重大错误直接退出程序`os.Exit(1)`
   +  不影响功能的小错误写入日志，并用代码补救
   +  每天自动归纳日志，分析错误分布，发送日报
   +  出现事故后，调取事故前的日志，分析出错误原因并修复


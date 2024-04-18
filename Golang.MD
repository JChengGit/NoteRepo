#### 切片

```go
// 使用 make 函数创建切片
slice1 := make([]int, 5) // 创建一个长度为 5 的切片，初始值为零值

// 使用字面量语法创建切片
slice2 := []int{1, 2, 3, 4, 5} // 创建一个包含指定元素的切片

// 声明一个空切片
var slice3 []int

// 切片的切片
subSlice := slice2[1:3] // 切片从第二个元素到第三个元素（不包括第三个元素）

// 切片追加元素
slice = append(slice, 6) // 追加一个新元素到切片末尾
slice = append(slice, 7, 8, 9) // 追加多个元素到切片末尾

len(slice2) // 切片长度
cap(slice2) // 切片容量

// 遍历切片
for index, value := range slice {
    fmt.Printf("Index %d, ")
}
```



#### 时间

```go
// 格式化
now := time.Now()
fmt.Println("Formatted time:", now.Format("2006-01-02 15:04:05"))

// 解析
str := "2022-03-01"
t, err := time.Parse("2006-01-02", str)

// 计算
now := time.Now()
later := now.Add(24 * time.Hour)

start := time.Now()
time.Sleep(3 * time.Second)
duration := time.Since(start)

```



#### 反射

```go
uType := reflect.TypeOf(obj)
fmt.Println(uType.Name())
fmt.Println(uType.NumField())
fmt.Println(uType.NumMethod())

reflect.ValueOf(x)
```



#### 强制类型转换

```go
var x int = 10
var y float64 = float64(x) // 将int类型转换为float64类型

message := "GET / HTTP/1.1\r\nHost: example.com\r\n\r\n"
resq := []byte(message) // 字符串转换为字节切片
```



#### IO

```go
```



#### 互斥锁

```go
import (
    "sync"
)

type SafeCounter struct {
    lock	sync.Mutex
    count	int
}

func (s *SafeCounter) Increment() {
    s.lock.Lock() // 加锁，防止其他 goroutine 同时访问
    defer s.lock.Unlock() // 使用 defer 保证即使函数出现 panic，锁也会被释放

    s.count++ // 访问共享资源
}
```































1. **基础问题**：
   - 介绍 Go 语言的特点和优势。
   - 解释 Goroutine、Channel 的概念。
   - 什么是 defer？它的作用是什么？
   - 区分指针类型和值类型。
   - 解释接口和类型断言的概念。
   - 介绍 Go 语言中的错误处理机制。
2. **并发编程**：
   - Goroutine 与线程的区别是什么？
   - 如何优雅地关闭一个 Goroutine？
   - 什么是 Channel？如何使用 Channel 实现并发同步？
   - 解释 select 语句的作用。
3. **内存管理**：
   - Go 语言的垃圾回收机制是如何工作的？
   - 如何避免内存泄漏？
4. **数据结构与算法**：
   - 介绍 Go 语言中的数组、切片、映射的特点和使用方法。
   - 如何在切片中删除元素？
   - 解释二叉树的概念，并实现一个二叉树的遍历算法。
   - 介绍一种排序算法，并说明其时间复杂度和空间复杂度。
5. **网络编程**：
   - 如何使用 Go 语言编写一个简单的 HTTP 服务器？
   - 如何使用 Go 语言发送 HTTP 请求？
   - 解释 TCP 和 UDP 的区别，并说明 Go 语言中如何使用它们。
6. **性能优化**：
   - 如何评估一个 Go 程序的性能？
   - 介绍 Go 语言中的一些性能优化技巧。
7. **实际项目经验**：
   - 介绍你在实际项目中遇到的一些问题，并说明如何解决。
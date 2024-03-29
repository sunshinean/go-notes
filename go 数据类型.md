# go 的数据类型：
```
  布尔型  --》
    bool 类型的值为 true 或 false  
    var b bool = true
 ```
 ```
  数字类型  -->
    整型 int 和浮点型 float32、float64，Go 语言支持整型和浮点型数字，并且支持复数，其中位的运算采用补码。
    var a int = 1
 ```
 ```
  字符串类型  -->
    字符串就是一串固定长度的字符连接起来的字符序列。Go 的字符串是由单个字节连接起来的。
    Go 语言的字符串的字节使用 UTF-8 编码标识 Unicode 文本。
    var c string = "hello"
  ```
  
  ### 派生类型
  ```
      (a) 指针类型（Pointer）
      
        指针就是一个指针变量指向了一个值的内存地址。
        Go 语言的取地址符是 &，放到一个变量前使用就会返回相应变量的内存地址。
        定义指针   var a *int //定义指针
        ```
        package main
        import "fmt"
        func main() {
            var ptr *int //定义指针
            fmt.Println("变量a的地址是：%x", &ptr)
            if ptr == nil {
              fmt.Println("指针ptr是空指针")
            }
          }
        /*当一个指针被定义后没有分配到任何变量时，它的值为 nil。
        nil 指针也称为空指针。
        nil在概念上和其它语言的null、None、nil、NULL一样，都指代零值或空值。
        一个指针变量通常缩写为 ptr。*/
        ```
        运行结果：
          变量a的地址是：%x 0xc000092018
          指针ptr是空指针
 ```
 ``` 
      (b) 数组类型
        声明数组： var data_arr [5] int
       ```
        package main
        import "fmt"
        func main() {
          var data_arr [5] int
          var i int
          //data_arr[0] = 1
          //data_arr[1] = 2
          //data_arr[2] = 3
          //data_arr[3] = 4
          //data_arr[4] = 5
          fmt.Println(data_arr)
          for i = 0; i < 5; i++ {
            data_arr[i] = i
            fmt.Printf("data_arr[%d] = %d\n",i,data_arr[i])
          }
        }
       ```
        运行结果：[0 0 0 0 0]
                data_arr[0] = 0
                data_arr[1] = 1
                data_arr[2] = 2
                data_arr[3] = 3
                data_arr[4] = 4
   ```
   ```
      (c) 结构化类型(struct)
      (d) Channel 类型
      (e) 函数类型
      (f) 切片类型
      (g) 接口类型（interface）
      (h) Map 类型
   ```
      
###### 参考：https://www.runoob.com/go/go-data-types.html

# Map：
```
  Map 是一种无序的键值对的集合。
  Map 最重要的一点是通过 key 来快速检索数据，key 类似于索引，指向数据的值。
  Map 是一种集合，所以我们可以像迭代数组和切片那样迭代它。
```
```
  package main

  import "fmt"

  func main() {
    //使用map关键字来定义 Map [定义的是key的类型]value的类型
    //声明变量，默认 map 是 nil
    var map1 map[string]int //nil map 不能用来存放键值对
    //使用make函数定义 Map
    map2 := make(map[string]int)
    fmt.Println(map1)
    fmt.Println(map2)
    map2["a"]  = 1
    map2["b"] = 2
    map2["c"] = 3
    fmt.Println("map2===", map2)
    //遍历map
    for key, value := range map2{
      fmt.Printf("%s的值是 %d\n",key, value)
    }
    value, isExist := map2["a"]
    fmt.Println(value)
    fmt.Println(isExist)
    if isExist{
      fmt.Printf("a的值是 %d\n", value)
    } else {
      fmt.Println("a的值不存在")
    }
    //delete() 函数用于删除集合的元素, 参数为 map 和其对应的 key
    delete(map2, "a")
    a, isExist := map2["a"]
    fmt.Println(a)
    fmt.Println(isExist)
    if isExist{
      fmt.Printf("a的值是 %d\n", value)
    } else {
      fmt.Println("a的值不存在")
    }
  }
```
  
  ###### 运行结果是： 
  ```
    map[]
    map[]
    map2=== map[a:1 b:2 c:3]
    b的值是 2
    c的值是 3
    a的值是 1
    1
    true
    a的值是 1
    0
    false
    a的值不存在
 ```

#Go 并发  
```
  Go 语言支持并发，我们只需要通过 go 关键字来开启 goroutine 即可。
  goroutine是Go并行设计的核心。goroutine说到底其实就是协程，但是它比线程更小，
  十几个goroutine可能体现在底层就是五六个线程，Go语言内部帮你实现了这些goroutine之间的内存共享。
  执行goroutine只需极少的栈内存(大概是4~5KB)，当然会根据相应的数据伸缩。
  也正因为如此，可同时运行成千上万个并发任务。goroutine 是轻量级线程，goroutine 的调度是由 Golang 运行时进行管理的。
```
```
  package main

  import (
    "fmt"
    "time"
  )

  func say(s string) {
    for i := 0; i < 5; i++ {
      time.Sleep(100 * time.Millisecond)
      fmt.Println(s)
    }
  }

  func main() {
    go say("haha")
    say("lalalal")
  }
```
  
  运行结果：
    haha
    lalalal
    lalalal
    haha
    haha
    lalalal
    haha
    lalalal
    haha
    lalalal

# 通道（channel）  
```
  通道（channel）是用来传递数据的一个数据结构。
  通道可用于两个 goroutine 之间通过传递一个指定类型的值来同步运行和通讯。
  操作符 <- 用于指定通道的方向，发送或接收。如果未指定方向，则为双向通道。
```
### channel类型：无缓冲和缓冲类型  
```
  channel有两种形式的，一种是无缓冲的，一个线程向这个channel发送了消息后，
  会阻塞当前的这个线程，知道其他线程去接收这个channel的消息。
  
  带缓冲的channel，是可以指定缓冲的消息数量，当消息数量小于指定值时，
  不会出现阻塞，超过之后才会阻塞，需要等待其他线程去接收channel处理
```
```
  package main

  import "fmt"

  func main()  {
    //声明通道 关键字 chan 数字1 为缓冲区大小
    ch := make(chan int, 1)
    fmt.Println(ch)
    ch <- 3
    //定义了缓冲区才能读取通道里面的值 否则会报一个错 fatal error: all goroutines are asleep - deadlock!（所有的进程都在sleep）
    /*
     出错信息的意思是： 
    在main goroutine线，期望从管道中获得一个数据，而这个数据必须是其他goroutine线放入管道的 
    但是其他goroutine线都已经执行完了(all goroutines are asleep)，那么就永远不会有数据放入管道。 
    所以，main goroutine线在等一个永远不会来的数据，那整个程序就永远等下去了。 
    这显然是没有结果的，所以这个程序就说“算了吧，不坚持了，我自己自杀掉，报一个错给代码作者，我被deadlock了”
    */
    val := <- ch
    fmt.Println(val)
  }
```
  
  运行结果：
    0xc000096000
    3

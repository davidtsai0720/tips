# **Go Channel**

- [Dead Lock](#dead-lock)

## ***Dead Lock***

```go
func OnlyProducer() {
    ch := make(chan int)
    ch <-1
}

func OnlyConsumer() {
    ch := make(chan int)
    <-ch
}

func InSameGorountineI() {
    ch := make(chan int)
    ch <- 1
    <- ch
}

func InSameGorountineII() {
    ch := make(chan int)
    <- ch
    ch <- 1
}
```

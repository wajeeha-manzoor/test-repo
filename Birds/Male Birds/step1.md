---
title: Introduction

---
<!--Introduction-->

Go provides communication mechanisms called channels that allow goroutines to share data.

We create channels using the `make()` function. It takes in the chan keyword and the channel’s element type. See the syntax below:

```go
myChanel := make(chan int)
```

Channels make it possible to craft incredibly high-performance, highly concurrent applications in Go.

In this scenario, we will cover two important concepts: unbuffered and buffered channels.
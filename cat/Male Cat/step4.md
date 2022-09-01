---
title: Unbuffered channels

---
<!--Unbuffered channels-->

In this step, we’ll talk about channel operations. Remember, channels can be thought of as pipelines that carry messages between goroutines. Take this channel as an example:

```go
myChannel := make(chan int)
```

Whenever a goroutine puts a value/message into the channel, it closes that channel to other routines until the value is received by a receiver goroutine.

Let’s see using the code below:

{{copy filename='code.go'}}
```go
package main

import (
	"fmt"
	"math/rand"
	"time"
)

func showValue(c chan int) {
	randomValue := rand.Intn(10)
	fmt.Println("Generated random value: {}", randomValue)
	time.Sleep(1000 * time.Millisecond)
	c <- randomValue
	fmt.Println("The value sent to the channel is:", randomValue)
}

func main() {

	myChannel := make(chan int)
	defer close(myChannel)

	go showValue(myChannel)
	go showValue(myChannel)

	channelContent := <-myChannel
	fmt.Println("Value received from the channel:", channelContent)
}
```
{{ /copy }}

In the code above, we have created a channel `myChannel()` and used it to pass messages from two go `showValue()` goroutines. We also added `defer close(myChannel)` to defer closing the channel until the `main()` function execution is complete.

The goroutine `showValue(myChannel)` passes the channel myChannel. `rand.Intn(10)` generates a random number between 1 and 10 that is sent to myChannel using `c <- randomValue`.

After completion, the program goes back to the main function where the channel value is received by `channelContent := <-myChannel` before being printed out.

Let’s now run the application to see if both goroutines successfully send values using the channel. Run the command below:

{{ execute }}
```
go run code.go
```
{{ /execute }}

After the execution, you may find out something unusual: Only one goroutine was able to complete the process of sending and receiving. 

We only saw `The value sent to the channel is: 1`, while we should also see `The value sent to the channel is: 7`.

This is due to the fact that we're using unbuffered channels.

Next, we’ll look at how we can solve that problem using buffered channels.
---
title: Buffered channels

---
<!--Buffered channels-->

In the previous step, we faced the challenge of executing communication for multiple Goroutines using a single channel. The way to overcome this challenge is to use buffered channels.

Here is an example of a buffered channel:

```go
myChannel := make(chan int, 3)
```

The difference between the unbuffered channels we’ve used in the previous steps and this buffered channel is the capacity argument, in this case, 3. The goroutine will now only block the channel from taking more messages/values after the capacity exceeds 3.

Now, let’s see how this solves the challenge we faced in the previous step. Add the code below:

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
	myChannel := make(chan int, 4)
	defer close(myChannel)

	go showValue(myChannel)
	go showValue(myChannel)

	channelContent := <-myChannel
	fmt.Println("Value received from the channel:", channelContent)
	time.Sleep(1000 * time.Millisecond)
}
```
{{ /copy }}

From the code above, we should now expect the second goroutine to continue using the channel whether the first goroutine value has been received or not. We’ve now successfully implemented a non-blocking channel.

Run the application using the command below:

{{ execute }}
```
go run code.go
```
{{ /execute }}

Let’s look at the key takeaways.















An unbuffered channel is used to perform synchronous communication between goroutines while a buffered channel is used for perform asynchronous communication. An unbuffered channel provides a guarantee that an exchange between two goroutines is performed at the instant the send and receive take place.
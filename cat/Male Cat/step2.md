---
title: Write data to a channels

---
<!--Write data to a channels-->

Channels are the only medium of communication through which goroutines communicate. Think of it as a pipeline where goroutines can post the data they want to send as well as receive values sent to them.

In this step, we will learn how to write data to a channel. We do that by using `c<-`.

Below is an implementation of channel data reading:

{{copy filename='code.go'}}
```go
package main

import (
	"fmt"
)

func viewChannelContent(c chan int) {
	// put value into the channel
	c <- 10
}

func main() {

	fmt.Println("Thread started")
	//create channel of int
	myChannel := make(chan int)
	// call to goroutine
	go viewChannelContent(myChannel)

	fmt.Println("Thread ends")
}
```
{{ /copy }}

From the code above, we’ve created a channel `myChannel()` that passes int variables. The goroutine `viewChannelContent()` uses the information in the channel as its argument. 

Lastly, we wrote an int variable 10 on our channel using `c <- 10`. We could write any value we want, 10 is just an example of what `viewChannelContent` should have as a value. 

Next, we’ll read the data in the channel.
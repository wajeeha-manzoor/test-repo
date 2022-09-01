---
title: Read data from a channel

---
<!--Read data from a channel-->

After writing data to the channel, we need a way to read it for the communication process to be complete. Retrieving data from a channel is done using the syntax `<-channelName`.

The program below reads the data written in the previous step:

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
{{ highlight }}
	//Read value in the channel
	channelContent := <-myChannel
	fmt.Println("The channel contains the value: ", channelContent)
{{ /highlight }}
	fmt.Println("Thread ends")
}
```
{{ /copy }}

From the code above, the channel contains an int variable which is taken as a parameter by the function `viewChannelsContent()`. We read the int value in the channel by using `<-myChannel` syntax.

Run the code using the command to read the channel’s content:

{{ execute }}
```
go run code.go
```
{{ /execute }}
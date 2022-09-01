---
title: Key takeaways

---
<!--Key takeaways-->

- Channels are the medium of communication used by goroutines
- There are two types of channels: buffered and unbuffered channels.
- `myChannel<-` writes data to a channel
- `<- myChannel` reads data from a channel
- Unbuffered channels: Can only handle one message from a goroutine at once.
- Buffered channel: Can handle multiple messages from multiple goroutines at once.
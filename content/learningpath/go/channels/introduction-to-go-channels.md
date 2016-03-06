+++
topic = "go"
categories = ["go", "concurrency"]
learning = "Channel"
type = "post"
externalTitle="Introduction To Golang: Channels"
link = "http://openmymind.net/Introduction-To-Go-Channels/"
date = "2016-02-26T23:47:56-03:00"
title = "Introduction to go channels"
keepLearning = [
  "Buffer channel",
]
+++

In this post [@karlseguin](https://twitter.com/karlseguin) explains how channels work in golang.

So basically channels is the way golang uses to make communication between goroutines. Can be for both, pass signals or data around, different than thread-based programming it is not necessary to lock data around, to avoid deadlocks, as with goroutines only one goroutine has access to a piece of data at a given time. So it does not do a lock of data.

**He gives one analogy about, thread vs  golang channels:**

<blockquote>
Consider a phone conversation. It can be difficult to coordinate who should talk, especially as more people get added to the conversation. It isn't uncommon for two people to speak at once. Conversely, it also isn't uncommon for one person to do all the talking and not let the others participate. This, to me, is what thread-based programming is like.<br /><br />
Channels on the other hand, are more like passing notes in class. Coordination is strictly controlled by the act of passing the note to someone. There's simply no way for you and your friend to write on the same note at the same time.
</blockquote>

### How create a go channel?

{{< highlight go >}}
c := make(chan int, 1)
{{< /highlight >}}

<br />
Basically it creates one channel that enables pass integers between goroutines. It is called **buffer channel**.

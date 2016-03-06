+++
topic = 'go'
categories = ['go']
date = "2016-03-06T18:19:12-03:00"
keepLearning = [
  "Distributed Scheduling system",
  "Policy Engine",
  "Isolation - Secure Perimeter Networking",
  "Semantically aware communications"
]
learning = "Why use go?"
video = "https://www.youtube.com/watch?v=qC9WhjmewIk"
title = "Talk Why We use go at Apcera"
type = "talk"

+++

This talk from of [@derekcollison](https://twitter.com/derekcollison), shows why they are using golang at [apcera](https://www.apcera.com/).

It caught my attention when he refers companies that are using golang, he mention one source:

https://github.com/golang/go/wiki/gousers

Opening the github and doing a quickly count ```document.querySelectorAll('.markdown-body li');``` it says about 348 companies using golang are listed in this wiki.

**Some highlight for:**

- Digitalocean
- Disqus
- Facebook
- Github
- Google
- IBM
- Netflix
- Pivotal
- Rackspace
- Shopify
- ...

Some of these companies I didn't know that were using golang, it's nice to see so different companies, using go for achieve their expected results.

*... backing to the talk*

**Some of the reasons that he gave about why go are:**

- Simple language, easy to remember
- Good standard library
- Easy concurrency
- Synchronous Programming Model (he compares that with node.js callbacks)
- Good garbage collection
- Really stacks

One point he emphasize and that I most like is that **go is for get things done**.

### Why Go at Apcera?

**In his opinion:**

- **Best choice for distributed systems**<br />
  He says he is able to test all system by using Go routines, it's not a kind of unit test, but more a functional test
- **It's a good core language**<br />
  He says that is easy to hire talent people, even without a background experience, as it is an accessible language in few weeks people can be productive and know the language well.
- **Good standard library support**
- **Tooling is amazing**<br />
  go vet, go fmt, go test -race, etc...


**He mention what they do there and why go fit:**

- Message systems
- Distributed Scheduling system
- Orchestator
- Policy Engine
- Isolation - Secure Perimeter Networking
- Semantically aware communications

He endup the talk asking: **Why Go?**

- It is simple language
- Pretty good ecosystem
- It is getting better faster

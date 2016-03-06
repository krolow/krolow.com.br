+++
topic = "go"
categories = ["go", "geolocation", "algorithm"]
learning = "Why use go?"
type = "post"
externalTitle="How We Built Uber Engineering’s Highest Query per Second Service Using Go"
link = "https://eng.uber.com/go-geofence/"
date = "2016-02-27T23:47:56-03:00"
title = "How uber use Go for geolocation"
keepLearning = [
  "[R-tree](https://en.wikipedia.org/wiki/R-tree)",
  "[S2](http://blog.christianperone.com/2015/08/googles-s2-geometry-on-the-sphere-cells-and-hilbert-curve/)",
  "[Ray casting algorithm](https://en.wikipedia.org/wiki/Point_in_polygon#Ray_casting_algorithm)",
  "[Go memory model](https://golang.org/ref/mem)",
  "[Sync/atomic](https://golang.org/pkg/sync/atomic/)",
  "[Go Sync of memory](https://golang.org/pkg/sync/#RWMutex)"
]
+++

Good article explaining why they chose Go instead of node.js, to build their geo location query system.

**Some aspects they have highlighted about golang:**

- High-throughput and low-latency
- CPU intensive workload
- Non-disruptive background loading, refreshing in-memory, in go they would be able to use goroutines

It also explains how they come up with the solution to make the index of data, instead of use algorithms like [R-tree](https://en.wikipedia.org/wiki/R-tree), or [S2](http://blog.christianperone.com/2015/08/googles-s2-geometry-on-the-sphere-cells-and-hilbert-curve/)
They saw that they are city-centric, all the business logic is related to city, so it allows they create two boundaries, one for the city, so first of all they found the city, and second inside the city they found the geolocations.

As they said: "While the runtime complexity of the solution remains O(N), this simple technique reduced N from the order of 10,000s to the order of 100s."

**They end up summarizing their experience with golang:**

* High developer productivity (few days to learn language, easy to maintain because static typing)
* High performance in throughput and latency
* Super reliable

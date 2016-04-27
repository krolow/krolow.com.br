+++
topic = 'microservices'
categories = ['microservices']
date = "2016-04-27T11:33:01-03:00"
externalTitle = ""
keepLearning = []
learning = "Use Case / In Action"
video = "https://www.youtube.com/watch?v=Y3vgtWMXJjc"
title = "DigitalOcean: Microservices as the Cloud"
type = "talk"

+++

In this talk, [Phil Calçado](https://twitter.com/pcalcado)
shows his previous experiences in other companies as well his
current experience in migrate the architecture of Digital
Ocean to make usage of microservices architecture.

He starts the talk showing how the architecture of digital
ocean works, it uses some iterations showing from where it
come and where it is nowadays.

Once explained the architecture he starts to talk about the
move to microservices, and how accomplish the [micro services
prerequisites](http://martinfowler.com/bliki/MicroservicePrerequisites.html) that are described by Martin Fowler.

**Prerequisites are:**

- Rapid provisioning
- Basic Monitoring
- Rapid application deployment

**How digitalocean solve:**

- **Rapid provisioning:** They use their self to provision new machines
- **Basic Monitoring:** They use [Prometheus](https://prometheus.io/), he points out some problems of [graphite](http://graphite.wikidot.com/) like usage of disks.
- **Rapid application deployment:** They are using [kubernets](http://kubernetes.io/) for that,
he mentions about get involved in a lot of discussing between the usage of [mesos](http://mesos.apache.org/) and kubernets, he
says that you might choose the best for your use case, BUT, that google has been investing a lot of money in
kubernets, so it probably good to keep with it, so probably features that it does not have now it would
probably have in a near future. In the other hand if you are in a big company that can afford support, it would be
good choose mesos as it has a paid support team.

**In Q&A section there were some good questions/answers that come up like:**

- DNS vs Service Discovery, he suggests the usage of service discovery as DNS takes to long to propagate, his suggestion is to use
    [Consul](https://github.com/hashicorp/consul)
- API Gateways and if falcor/graphql might be a solution to avoid gateways, he says that would avoid usage of falcor/graphql as it would relay
    the logic on client, and it's something that he attempts to avoid as the process to deploy new versions of app take to long (like process
    of IOS to publish new app versions)

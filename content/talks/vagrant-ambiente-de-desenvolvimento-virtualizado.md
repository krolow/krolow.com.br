+++
year="2014"
date = "2014-09-28"
slideshare = "//www.slideshare.net/slideshow/embed_code/key/m5HVKNJEWxP3NE"
title = "vagrant ambiente de desenvolvimento virtualizado"

+++
Talk given in Pelotas, at conference [Tchê Linux Pelotas](http://tchelinux.org/wiki/evento_2012_pelotas), it presents vagrant as a solution for development environments, pointing some problems and some solutions that vagrant might help, some of the points are:

**Problems**

* Projects environment are complex (multiple databases, multiple web-services, multiple languages)
* Handle software version is complex (different requirement, different version...)
* Development OS might be different than production OS
* How share the env between developers
* We do not isolate our development, it might be sharing same resources of browser and other processes running in development machine
* It takes time to configure all the project
* You can not replicate this process in another machine


So a long of the presentation it shows some facts and problems and how vagrant and some provision tool might help to solve such problems, by creating a sharable, isolate and replicable environment.

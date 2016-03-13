+++
categories = ['command', 'linux']
date = "2016-03-13T12:07:57-03:00"
learning = ""
title = "Find SATA speed"

+++
{{< highlight bash >}}
dmesg | grep -i sata | grep 'link up'
{{</highlight>}}

- SATA revision 1.0 => 1.5 Gbit/s, 150 MB/s
- SATA revision 2.0 => 3 Gbit/s, 300 MB/s
- SATA revision 3.0 => 6 Gbit/s, 600 MB/s
- SATA revision 3.2 => 16 Gbit/s, 1969 MB/s

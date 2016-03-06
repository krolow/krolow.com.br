+++
categories = ["linux", "command"]
date = "2016-03-06T14:21:18-03:00"
title = "list processes with most opened files"

+++

{{< highlight bash >}}
lsof -n 2>/dev/null | awk '{print $1,$2}' | sort | uniq -c | sort -nr | head -25 | while read nr name pid ; do printf "%10d / %-10d %-15s (PID %5s)\n" $nr $(cat /proc/$pid/limits | grep 'open files' | awk '{print $5}') $name $pid; done
{{</highlight>}}

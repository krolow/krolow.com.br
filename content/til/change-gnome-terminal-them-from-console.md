+++
categories = ['gnome-terminal', 'command', 'linux']
date = "2016-03-11T12:22:28-03:00"
title = "Change gnome terminal theme from console"

+++
{{< highlight bash >}}
# define the default profile
gconftool-2 --set --type string /apps/gnome-terminal/global/default_profile %profile-name%
{{< /highlight >}}

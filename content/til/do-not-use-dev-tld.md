+++
categories = ["development", "docker", "tld"]
date = "2017-01-12T22:08:37Z"
learning = ""
title = "Do not use dev TLD"
+++


Today I learned to not use `.dev` as a TLD to local development.

It ends up that there is already one [open process](https://gtldresult.icann.org/application-result/applicationstatus/applicationdetails/964)
to become a global TLD, like we have `.com`, `.net` and nowadays `.whatever`...

But until today I didn't know why when I used sometimes `.dev` it was pointing to IP address `127.0.53.53`, but by researching today the
reason I end up finding it!

It's to avoid [name collision](https://www.icann.org/resources/pages/name-collision-2013-12-06-en)

#### ...in their words:

> **127.0.53.53**
> is a special IPv4 address that will appear in system logs alerting system administrators that there is potential name collision
> issue, enabling a quick diagnosis and remediation. The "53" is used as a mnemonic to indicate a DNS-related problem owing to the use of
> network port 53 for the DNS service.


So from now on I will start to use `.local` as my local dev environment TLD.

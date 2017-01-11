+++
categories = ["docker", "go"]
date = "2017-01-11T11:51:54Z"
learning = ""
title = "Go compile binary not running in alpine and busybox"

+++
I was working in a [proxy pac project to serve TLD for local development](https://github.com/krolow/tld-proxy-pac). I have decided to use
golang, because the code would be quite simple and get a binary as output would help in use a small docker image and just copy the binary.

Once the code was finish, I have started the creation of the docker file that was quite simple, just a copy of binary file to inside the
docker image.

Unfortunately it was not that simple, in the first tries I got this error:

{{< highlight bash >}}
panic: standard_init_linux.go:175: exec user process caused "no such file or directory" [recovered]
        panic: standard_init_linux.go:175: exec user process caused "no such file or directory"

goroutine 1 [running, locked to thread]:
panic(0x7ea980, 0xc820143420)
        /usr/local/go/src/runtime/panic.go:481 +0x3e6
github.com/urfave/cli.HandleAction.func1(0xc82011b2e8)
        /go/src/github.com/opencontainers/runc/Godeps/_workspace/src/github.com/urfave/cli/app.go:478 +0x38e
panic(0x7ea980, 0xc820143420)
        /usr/local/go/src/runtime/panic.go:443 +0x4e9
github.com/opencontainers/runc/libcontainer.(*LinuxFactory).StartInitialization.func1(0xc82011abf8, 0xc82001e090, 0xc82011ad08)
        /go/src/github.com/opencontainers/runc/Godeps/_workspace/src/github.com/opencontainers/runc/libcontainer/factory_linux.go:259 +0x136
github.com/opencontainers/runc/libcontainer.(*LinuxFactory).StartInitialization(0xc82005c820, 0x7f53b3b86470, 0xc820143420)
        /go/src/github.com/opencontainers/runc/Godeps/_workspace/src/github.com/opencontainers/runc/libcontainer/factory_linux.go:277 +0x5b1
main.glob.func8(0xc82007a780, 0x0, 0x0)
        /go/src/github.com/opencontainers/runc/main_unix.go:26 +0x68
reflect.Value.call(0x74f180, 0x900b08, 0x13, 0x846ea8, 0x4, 0xc82011b268, 0x1, 0x1, 0x0, 0x0, ...)
        /usr/local/go/src/reflect/value.go:435 +0x120d
reflect.Value.Call(0x74f180, 0x900b08, 0x13, 0xc82011b268, 0x1, 0x1, 0x0, 0x0, 0x0)
        /usr/local/go/src/reflect/value.go:303 +0xb1
github.com/urfave/cli.HandleAction(0x74f180, 0x900b08, 0xc82007a780, 0x0, 0x0)
        /go/src/github.com/opencontainers/runc/Godeps/_workspace/src/github.com/urfave/cli/app.go:487 +0x2ee
github.com/urfave/cli.Command.Run(0x849d58, 0x4, 0x0, 0x0, 0x0, 0x0, 0x0, 0x8dfe00, 0x51, 0x0, ...)
        /go/src/github.com/opencontainers/runc/Godeps/_workspace/src/github.com/urfave/cli/command.go:191 +0xfec
github.com/urfave/cli.(*App).Run(0xc820001980, 0xc82000a100, 0x2, 0x2, 0x0, 0x0)
        /go/src/github.com/opencontainers/runc/Godeps/_workspace/src/github.com/urfave/cli/app.go:240 +0xaa4
main.main()
        /go/src/github.com/opencontainers/runc/main.go:137 +0xe24
➜
{{</highlight>}}


After some google about the error, I was thinking it might be related with the docker version, I have tried to upgrade and downgrade and keep
with no lucky.

So I found [this
stackoverflow](http://stackoverflow.com/questions/36279253/go-compiled-binary-wont-run-in-an-alpine-docker-container-on-ubuntu-host) by the
description it seems that error was quite similar to mine.

I have decided to give it a try, and it works!  Basically the issue is that golang `net` library when normally build a package it creates
dynamic links to some `.so` libs, in my case these were the links:


{{< highlight bash >}}
 -> ldd builds/1.0.0/linux_amd64/tld-proxy-pac
        linux-vdso.so.1 =>
        (0x00007ffd9a087000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f6470502000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f6470139000)
        /lib64/ld-linux-x86-64.so.2 (0x00005589babab000)ldd builds/1.0.0/linux_amd64/tld-proxy-pac
        linux-vdso.so.1 =>  (0x00007ffd9a087000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f6470502000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f6470139000)
        /lib64/ld-linux-x86-64.so.2 (0x00005589babab000)
{{</highlight>}}


So what I have to do is build `netgo` by forcing static links `CGO_ENABLED=0 go build -tags netgo -a -v` and build my code using
`CGO_ENABLED=0` as well `CGO_ENABLED=0 goxc`.

By checking the links in the new binary output, I could ensure the non existence of dynamic links:


{{< highlight bash >}}
-> ldd builds/1.0.0/linux_amd64/tld-proxy-pac
        not a dynamic executable
{{</highlight>}}

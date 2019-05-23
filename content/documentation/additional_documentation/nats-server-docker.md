# nats-server-docker

+++ title = "Run the NATS Docker Image" description = "" category = "tutorials" \[menu.main\] name = "Docker" weight = 8 identifier = "doc-nats-server-docker" parent = "Additional Documentation" +++

In this tutorial you run the [NATS server Docker image](https://hub.docker.com/_/nats/). The Docker image provides an instance of the [NATS Server](https://github.com/nats-io/nats-site/tree/c42c46a7c6b8669e66e28419887d2f8dd29aa502/documentation/server/gnatsd-intro/README.md). Synadia actively maintains and supports the gnatsd Docker image. The NATS image is only 6 MB in size.

**1. Set up Docker.**

See [Get Started with Docker](http://docs.docker.com/mac/started/) for guidance.

The easiest way to run Docker is to use the [Docker Toolbox](http://docs.docker.com/mac/step_one/).

**2. Run the gnatsd Docker image.**

```bash
> docker run -p 4222:4222 -p 8222:8222 -p 6222:6222 --name gnatsd -ti nats:latest
```

**3. Verify that the NATS server is running.**

You should see the following:

```bash
Unable to find image 'nats:latest' locally
latest: Pulling from library/nats
2d3d00b0941f: Pull complete 
24bc6bd33ea7: Pull complete 
Digest: sha256:47b825feb34e545317c4ad122bd1a752a3172bbbc72104fc7fb5e57cf90f79e4
Status: Downloaded newer image for nats:latest
```

Followed by this, indicating that the NATS server is running:

```bash
[1] 2017/06/28 18:34:19.605144 [INF] Starting nats-server version 0.9.6
[1] 2017/06/28 18:34:19.605191 [INF] Starting http monitor on 0.0.0.0:8222
[1] 2017/06/28 18:34:19.605286 [INF] Listening for client connections on 0.0.0.0:4222
[1] 2017/06/28 18:34:19.605312 [INF] Server is ready
[1] 2017/06/28 18:34:19.608756 [INF] Listening for route connections on 0.0.0.0:6222
```

Notice how quickly the NATS server Docker image downloads. It is a mere 6 MB in size.

**4. Test the NATS server to verify it is running.**

An easy way to test the client connection port is through using telnet.

```bash
> telnet localhost 4222
```

Expected result:

```bash
Trying ::1...
Connected to localhost.
Escape character is '^]'.
INFO {"server_id":"YMeTi2z178lM5SG302YgH2","version":"0.9.6","go":"go1.7.4","host":"0.0.0.0","port":4222,"auth_required":false,"ssl_required":false,"tls_required":false,"tls_verify":false,"max_payload":1048576}
```

You can also test the monitoring endpoint, viewing `http://localhost:8222` with a browser.

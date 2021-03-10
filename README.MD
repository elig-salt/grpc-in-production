# gRPC in production

When using gRPC in production, at some point the following problems become more appearant:

## Schema breaking changes
It's hard to break protobuf schemas, but possible.
Check out how to absolutely prevent it: [Schema Breaking changes](./buf/README.MD)

## Load balancing
gRPC connections are HTTP2 based - meaning multiple requests are multiplexed on each connection.

A client will have all of his requests sent on the first connection it opened.
Check out an awesome way to solve this, and also benefit from a variety of additional tools and capabilities:
[LinkedD](./linkerd-demo/README.md)

# xtp-ctl -- XTP Control Protocol Spec

## Motivation

[XTP](../README.md) requires a duplex pipe between the External Protocol process and the client application. This duplex pipe follows the `xtp-ctl` protocol, defined in this document.

## Spec

### Composition of Protocols

`xtp-ctl` uses the following other standards:

- [multiaddr](https://github.com/jbenet/multiaddr) for describing both "external transport" and "xtp-ctl pipe" endpoint addresses.
- [multistream](https://github.com/jbenet/multistream) for a self-describing wire protocol
- [libp2p transports](https://github.caom/libp2p/libp2p) for the transport protocol interface and modules to use
- [libp2p stream multiplexing](https://github.caom/libp2p/libp2p) to interleave many transport protocol flows in the same xtp-ctl pipe.

### `xtp-ctl` Pipe

The `xtp-ctl` wire protocol requires a reliable duplex pipe.

WIP

### `xtp-ctl` Protocol

The `xtp-ctl` wire protocol requires a reliable duplex pipe.

WIP

#### High Level Description

WIP

#### Wire Framing

Discuss stream multiplexing.

(Outside or inside the protocol??)

WIP

#### RPC Messages

WIP

(use protobuf??)

## Implementation Notes

### Multistream

The `xtp-ctl` wire protocol is meant to be mounted on top of [multistream](https://github.com/jbenet/multistream), but it is also possible to use `xtp-ctl` without multistream. Therefore, this spec defines the `xtp-ctl` protocol directly, leaving the multistream mounting to the parent.

The `xtp-ctl` pipe we propose here includes multistream, and suggests a transport, but leaves it up to the user to decide ultimately, as the user may have transport constraints.

### Head of Line Blocking

If the `xtp-ctl` pipe is being transferred over a lossy protocol (eg. UDP across the internet), we strongly recommend using a transport such as QUIC to prevent head-of-line blocking issues.

### Standard Protocol Libraries

It is recommended that `xtp-ctl` implementations use libraries from the [multiformats](https://github.com/multiformats) and [libp2p](https://github.com/libp2p/libp2p) projects.

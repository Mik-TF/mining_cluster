<h1>Mining Cluster</h1>

<h2>Table of Contents</h2>

- [Introduction](#introduction)
- [Tools as Building Blocks](#tools-as-building-blocks)
  - [Base Layer - Hardware](#base-layer---hardware)
  - [Cluster - Network](#cluster---network)
  - [Mining - Apps](#mining---apps)
- [Project Execution Flow](#project-execution-flow)
- [Maintenance](#maintenance)
- [License](#license)

---

## Introduction

We propose a proof-of-concept dual-coin mining cluster. This mining cluster uses GPU and CPU on any desktop computer to mine Monero, and to mine and stake Zano.

## Tools as Building Blocks

To achieve our proof-of-concept, we created a series of FOSS tools that can be combined to build projects.

- Tools
  - [ISO Boot Maker](https://github.com/Mik-TF/isobootmaker)
  - [TF Boot Maker](https://github.com/Mik-TF/tfbootmaker)
  - [Tailscale Cluster](https://github.com/Mik-TF/tscluster)
  - [Zano Miner](https://github.com/Mik-TF/zanominer)
  - [Monero Miner](https://github.com/Mik-TF/monerominer)

In the spirit of modular design, we created basic repositories with pieces of the whole. We can now build on those blocks and create complex forms.

As an example, we thus present the architecture and steps to deploy a Zano and Monero mining cluster. Any kind of blockchain workload could be deploy with such a system of modular tools.

### Base Layer - Hardware

For the base layer, you can set a private cluster via a VPN, or you can also deploy on the ThreeFold Grid.

- TF Boot Maker Tool:
  - Boot any computer into a 3node.
- ISO Boot Maker Tool:
  - Boot any computer into any ISO, e.g. Ubuntu 24.04.

### Cluster - Network

For the cluster, you can use Tailscale for private cluster via VPN, while the ThreeFold Grid comes equipped with the Mycelium network.

- Tailscale Cluster Tool
  - Manage a cluster with a control node and managed nodes via VPN.
- [Mycelium](https://github.com/threefoldtech/mycelium):
  - Manage a cluster of nodes on the ThreeFold Grid.

### Mining - Apps

- CPU Mining
  - Use the computer CPU to mine Monero via proof of work.
- GPU Mining
  - Use the computer GPU to mine Zano via proof of work and proof of stake.

## Project Execution Flow

A concrete real-world scenario could look like this:

- Get desktop computers with proper specs, e.g. good CPU and GPU for managed nodes.
- Get a laptop as the control node.
- Use the ISO Boot Maker Tool to:
  - Create a Ubuntu 24.04 ISO image and install it on each node.
- Use the Zano Miner and Monero Miner Tools to:
  - Run the two miner scripts on each managed node.
- Run the Tailscale managed script on each managed node.
- Run the Tailscale control script on the control node.

## Maintenance

The flow explained above will provide a cluster of one control node and many managed nodes.

The managed nodes can be accessed remotely using Tailscale. It is also possible to see the desktop screen using NoMonitor as explained in the respective repo.

Prometheus and Grafana are used for monitoring and update scripts are set on the managed nodes to keep them updated.

## License

This work is done under the [Apache 2.0 license](./LICENSE).

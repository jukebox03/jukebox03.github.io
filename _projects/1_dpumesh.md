---
layout: page
title: DPUmesh
description: Offloading service mesh sidecars onto a BlueField-3 DPU
importance: 1
category: research
---

**TNET Lab, Seoul National University · December 2025 – present**

A service mesh gives microservices uniform observability, retries, and mTLS by putting a sidecar proxy in front of every service. The abstraction is clean; the bill is not. Every request crosses the proxy twice, and on a busy node the sidecars end up competing with the application for the same host CPU.

DPUmesh moves that work off the host entirely, onto a **NVIDIA BlueField-3 DPU**. The data path runs on the DPU's own cores over DMA, so the mesh stops consuming cycles that the application needs.

#### Transparent framework integration

The part I find most interesting is that none of this should be the application's problem. I integrated the DPUmesh architecture directly into the **Apache Thrift** RPC framework, so a service already written against Thrift picks up the offloaded data path with **zero modifications to user code** — no sidecar to inject, no client library to swap.

#### Benchmarking and debugging

I benchmarked sidecar proxy overhead using **DeathStarBench**, a microservice benchmark suite that exercises realistic multi-hop call graphs rather than a synthetic echo server. Along the way I tracked down severe **Consul service-registry leaks** that were stalling CPU and exhausting connections under sustained load — the kind of bug that does not show up until you leave a benchmark running long enough.

#### Related repositories

- [`DPUmesh`](https://github.com/jukebox03/DPUmesh) — library and benchmark harness
- [`test_dma`](https://github.com/jukebox03/test_dma) — a small tool for measuring the DMA hardware limit, written to establish what the ceiling actually is before optimizing against it
- [`mini_ms`](https://github.com/jukebox03/mini_ms) — an event-driven microservice in C, used as a controllable workload

*This is ongoing lab work; results are not yet published.*

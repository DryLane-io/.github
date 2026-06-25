<div align="center">

# The Dry Stack

**One stack that is a database, a message queue, and a serializer — on a single box.**

[**drylane.io**](https://drylane.io) · [info@drylane.io](mailto:info@drylane.io) · [LinkedIn](https://www.linkedin.com/company/drylane-io) · [X](https://x.com/drylaneio)

</div>

---

Most systems are glued together from three separate pieces: a **database** to store data, a
**message queue** to move it, and a **serializer** to pack it on the wire. Every seam between them
is a copy, a serialization pass, and a network hop.

**Drylane fuses all three into one stack that runs on a single box** — ingesting **66 million
records a second** and answering queries in **microseconds**. No cluster required to be fast.

## The three pieces

| | What it is | Replaces |
|---|---|---|
| **Facts** | An embedded time-series store — SIMD query surfaces over billions of records, answers in microseconds. | the database (InfluxDB, Timescale) |
| **Nio** | The zero-copy network layer — ~100M messages/second, ~6µs round-trips over loopback. | the message queue (Kafka) |
| **Zao** | Serialization at memcpy speed — tiered codegen reaching ~67 GB/s on the fast path. | the serializer (Protobuf) |

## See it live

Everything below is a **real engine serving real queries**, not a screenshot. Click and break things.

- [**drylane.io**](https://drylane.io) — start here
- [**live.drylane.io**](https://live.drylane.io) — market-data wall: live ingest + continuous queries, watch the cap evict
- [**f1.drylane.io**](https://f1.drylane.io) — a real Formula 1 race, ingested once and replayed/queried in microseconds
- [**chaos.drylane.io**](https://chaos.drylane.io) — a two-node cluster you can break: cut the link, force a failover, watch it heal — no split-brain
- [**log.drylane.io**](https://log.drylane.io) — a virtualized browser over a huge live log, including the unsealed tail
- [**api.drylane.io**](https://api.drylane.io) — the query benchmark suite, run live on the box
- [**pi.drylane.io**](https://pi.drylane.io) — the same engine on a $35 Raspberry Pi 4

## What it's built with

The core is **C++** (the storage engine and the io_uring / RIO transport), with idiomatic **C#**
wrappers on top — write your app in C# and get native, zero-copy speed underneath. Runs on **Linux**
(io_uring) and **Windows** (RIO), tuned down to the SIMD for **Intel**, **AMD**, and **ARM** — the
same engine from a server rack to a Raspberry Pi.

## Is it open source?

Not yet — the engine isn't public. If you run time-series or streaming at scale and want to try it,
talk use cases, or just kick the tires: **[info@drylane.io](mailto:info@drylane.io)**.

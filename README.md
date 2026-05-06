# buildownwheels

A collection of infrastructure components I've reimplemented from scratch in Rust — databases, caches, runtimes — to understand how they actually work under the hood.

## The wheels

### [BoolCache](https://github.com/importsource/BoolCache)
A Redis-compatible in-memory cache. Speaks the RESP2 protocol so any `redis-cli` or Redis SDK works against it. Supports all core data types (String / List / Hash / Set / Sorted Set), dual persistence (AOF + RDB), key expiry, and primary-replica replication.

### [BoolDB](https://github.com/importsource/BoolDB)
A relational database with a real SQL engine. Page-based storage with a buffer pool, B-Tree indexes, ACID transactions backed by MVCC and Write-Ahead Logging, plus a TCP server and interactive CLI client.

### [BoolGraphDB](https://github.com/importsource/BoolGraphDB)
A lightweight embeddable graph database. Labeled property graph model, fluent traversal API (`has_label`, `out`, `in`, `filter`...), BFS / shortest-path queries, WAL-based crash recovery with automatic snapshots, and a simple TCP text protocol.

### [BoolDock](https://github.com/importsource/BoolDock)
A minimal container runtime. Implements the Linux primitives that make containers work — namespaces, cgroups, `pivot_root`, UID remapping — in a few thousand lines of Rust. Falls back to a `fork` + `chroot` development mode on macOS.

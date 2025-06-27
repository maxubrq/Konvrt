# Konvrt

**Konvrt** is a blazing‑fast, Rust‑powered engine that converts *any* file format to *any* other — safely, streaming‑ready, and embeddable from CLI to cloud.

---

## 🚀 TL;DR

```bash
# Install the CLI
cargo install konvrt

# Convert JPEG to modern WebP
konvrt photo.jpg --to webp

# Chain conversions with zero temp files
konvrt archive.tar.gz --to zip | konvrt --to 7z
```

---

## 🔮 Magic Kano Feature Map

A quick look at how Konvrt’s features align with the extended Kano model (including your **Magic** tier):

| Tier            | Feature Highlights                                                                                                                                                                                                                                                                                                                                                           |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Must‑Have**   | • Universal `--from/--to` CLI & crate API<br>• Lossless integrity check (SHA‑3)<br>• Stream‑safe: chunked I/O, back‑pressure<br>• Secure by default: memory‑safe Rust, sandboxed adapters                                                                                                                                                                                    |
| **Performance** | • Zero‑copy mmap & SIMD paths<br>• Async task scheduler (Tokio)<br>• GPU‑backed transcoding for images/video<br>• Adaptive parallelism (scales with CPU cores)                                                                                                                                                                                                               |
| **Delight**     | • Smart progress bars with ETA & throughput<br>• `--guess` picks best target format automatically<br>• Auto‑compress on the fly (< 50 MB RAM/stream)<br>• One‑liner pipes (`stdin` ⇄ `stdout`) work everywhere                                                                                                                                                               |
| **Magic**       | • **One‑Shot Publish**: drop any file, Konvrt emits optimal web‑ready bundle (e.g., responsive images, AVIF, Brotli, pre‑zipped)<br>• ML‑driven **Quality/Size Oracle** selects sweet‑spot params<br>• **Wasm Adapter Hot‑Swap**: load new formats at runtime, no restart<br>• **Context‑Aware Pipelines**: infer intent (archive, transcode, optimize) from content & flags |

---

## ✨ Key Features

* **Plug‑in adapters**: each format lives in its own crate or Wasm module; community can publish on crates.io without rebuilding core.
* **Everywhere**: same engine powers desktop apps, serverless lambdas, or embedded devices (no‑std optional).
* **Observability built‑in**: trace spans, Prom metrics, and flamegraph dump on `SIGUSR1`.
* **License‑friendly**: dual‑licensed MIT/Apache‑2.0, plus adapter‑level permissive exceptions.

---

## 🏗️ Architecture at a Glance

```
┌────────────── CLI / gRPC / FFI binding ──────────────┐
│                                                     │
│        front‑end shells (thin)                      │
└────────────── ▼──────────────────────────── ▼────────┘
        ╭──────────────────────────────╮
        │  Konvrt Engine Core          │  ← async tasks, ring‑buffers
        │  • Scheduler                 │
        │  • Sandbox & policy          │
        │  • Adapter host (Wasm/trait) │
        ╰──────────────────────────────╯
```

Crates layout: `konvrt-core`, `konvrt-cli`, `konvrt-adapter-sdk`, `konvrt-wasm-host`, `konvrt-cloud`.

---

## 📦 Supported Formats (v0.1)

| Category | Formats               |
| -------- | --------------------- |
| Images   | PNG, JPEG, WebP, AVIF |
| Archives | TAR, ZIP, 7z, GZIP    |
| Audio    | MP3, FLAC             |
| Video    | MP4 (H.264), WebM     |

> *Full list is generated at runtime from the adapter registry.*

---

## 🔜 Roadmap

| Version | Highlights                                      |
| ------- | ----------------------------------------------- |
| **0.1** | Core pipeline, 10 adapters, baseline benchmarks |
| **0.3** | Wasm adapter SDK + hot‑swap, GPU paths          |
| **0.6** | One‑Shot Publish, ML oracle beta                |
| **1.0** | Stable APIs, cloud autoscale, GUI desktop app   |

---

## 📊 Benchmarks

Automated GitHub Actions run native perf tests on each commit; flamegraphs are published to `gh‑pages` for deep dives.

---

## 🤝 Contributing

1. Fork & `cargo test --all`.
2. Create a new adapter with `cargo generate konvrt‑adapter‑template`.
3. Follow the CI style/lint rules (`rustfmt`, `clippy`, `just check`).

We follow the [Contributor Covenant](CODE_OF_CONDUCT.md).

---

## 🛡️ License

Konvrt is dual‑licensed under **MIT** and **Apache‑2.0**. You may choose either license.

---

## 💬 Community & Support

* **Discussions**: GitHub *Discussions* tab
* **Chat**: `#konvrt` on Matrix / Discord bridge
* **Security issues**: [security@konvrt.dev](mailto:security@konvrt.dev)

---

> © 2025 Konvrt contributors. Built with ❤️ in Rust.

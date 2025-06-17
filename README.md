# Konvrt

**Konvrt** is a blazing-fast archive format conversion engine written in Rust. It’s built to convert between compression formats like `.zip`, `.7z`, `.tar.gz`, and `.rar` with safety, speed, and precision. Part of the **Xtrakt** and **Komprss** toolchain.

## 🔁 What It Does

Konvrt lets you:

- Convert `.zip` → `.7z`, `.7z` → `.tar.gz`, and more
- Automatically extract + recompress archives in one step
- Handle password-protected archives (read-only)
- Batch convert multiple archives
- Use CLI or embed in Rust applications

---

## 🚀 Features

- 🔄 One-liner archive format conversion
- 📂 Batch processing support
- 🔐 Reads password-protected archives
- ⚙️ Clean error handling and file validation
- 🧰 CLI & Library API
- 🧼 Safe file handling (no zip-slip, no overwrites by default)

---

## 📦 Installation

```bash
git clone https://github.com/your-org/konvrt.git
cd konvrt
cargo build --release
````

---

## 🛠️ CLI Usage

### Basic Conversion

```bash
konvrt convert file.zip --to 7z
```

### Convert with Output Path

```bash
konvrt convert archive.7z --to tar.gz --output ./converted/archive.tar.gz
```

### Batch Convert a Folder

```bash
konvrt convert ./archives/ --to zip --recursive
```

---

## 📚 Library Usage (Rust)

```rust
use konvrt::Konverter;

fn main() {
    let konverter = Konverter::new();

    konverter
        .convert("archive.rar", "archive.zip")
        .expect("Conversion failed");
}
```

---

## 🗃️ Supported Formats

| Format    | Read | Write       |
| --------- | ---- | ----------- |
| `.zip`    | ✅    | ✅           |
| `.7z`     | ✅    | ✅           |
| `.rar`    | ✅    | ❌ (planned) |
| `.tar.gz` | ✅    | ✅           |
| `.tar`    | ✅    | ✅           |

> Write support for `.rar` may require proprietary tools or licensing.

---

## 📁 Project Structure

```
konvrt/
├── src/
│   ├── konverter.rs     # Core conversion logic
│   ├── formats/         # Handlers per archive type
│   ├── cli.rs           # CLI implementation
│   └── lib.rs
├── tests/
└── Cargo.toml
```

---

## 🧪 Tests

```bash
cargo test
```

---

## 🔐 Security

* Validates input before processing
* Protects against directory traversal attacks (zip-slip)
* No overwrite by default (unless `--force` is passed)

---

## 🤝 Part of the Suite

* 🗃 [Xtrakt](https://github.com/your-org/xtrakt) – Extract archives
* 📦 [Komprss](https://github.com/your-org/komprss) – Compress into archives
* 🔄 **Konvrt** – Convert archives between formats

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for full text.

---

Crafted with ❤️ in Rust by \[Your Name / Team / Org]

# 🚀 Federate CLI

**Federate** lets you query multiple data sources — APIs, databases, files — as if they were a single SQL database.  
Run it **locally for free**, or sign up for early access to the upcoming **remote mode** for multi-user collaboration and orchestration.

---

## ✨ Features

- 🔄 **Query anything with SQL** — APIs, CSV, JSON, SQLite, Postgres, and more
- 🧱 **Plan-based architecture** — Define everything in one YAML or JSON file
- 💻 **Local mode (Free)** — All processing happens locally, no cloud required
- 🌐 **Remote mode (Coming Soon)** — Share, schedule, and orchestrate data jobs
- ⚙️ **Simple CLI** — One binary, zero dependencies

---

## 📦 Installation (Local Mode)

### 1. Download the latest release

Visit the [Releases page](https://github.com/squeakycheese75/federate-hub/releases/latest) and download the binary for your OS.

**Apple Silicon (M1/M2/M3) Macs**:
```bash
curl -L https://github.com/squeakycheese75/federate-hub/releases/latest/download/federate-darwin-arm64 -o federate
chmod +x federate
```

**Intel Macs**:
```bash
curl -L https://github.com/squeakycheese75/federate-hub/releases/latest/download/federate-darwin-amd64 -o federate
chmod +x federate
```

**Linux (x86_64)**:
```bash
curl -L https://github.com/squeakycheese75/federate-hub/releases/latest/download/federate-linux-amd64 -o federate
chmod +x federate
```

**Windows (PowerShell)**:
```powershell
Invoke-WebRequest https://github.com/squeakycheese75/federate-hub/releases/latest/download/federate-windows-amd64.exe -OutFile federate.exe
```

---

### 2. First Run on macOS

macOS may block the binary since it’s unsigned:

```bash
# Remove quarantine
xattr -d com.apple.quarantine federate
./federate --help
```

Or:
1. Run the binary (you’ll get a warning)
2. Go to **System Settings → Privacy & Security**
3. Click **Allow Anyway**
4. Re-run `./federate`

---

### 3. Add to PATH (optional)

```bash
sudo mv federate /usr/local/bin/
```

Then try:

```bash
federate --help
```

---

### 🔧 Setup Workspace

```bash
# Initialize the local workspace at ~/.federate
federate init
```

---

## 🧪 Run an Example Plan

The easiest way to get started is by running a built-in example:

```bash
federate run --plan examples/quickstart/plan.json
```

This will load a CSV file and create a SQLite-backed dataset.

---

## 📁 Explore More Examples

Browse the [examples](./examples) directory for ready-to-run plans:

- Basic CSV / JSON ingestion
- SQLite and Postgres queries
- Deduplication and joins across sources
- Enterprise-grade federation scenarios

---

## 🧩 How It Works

Federate uses a single `plan.yaml` or `plan.json` file to:

- Define **data sources** (CSV, SQLite, Postgres, etc.)
- Configure **datasets** with SQL queries and plugins
- Enable **joins**, **deduplication**, and **storage options**

---

## 🧠 Learn More

- [📄 Plan file format](docs/plan-spec.md) (coming soon)
- [❓ FAQ](docs/faq.md)
- [🧪 Examples](./examples)

---

## 💡 Licensing

Federate CLI is:
- ✅ **Free** for personal and commercial use in **local mode**
- 🔐 **Paid** for advanced **remote mode** features

### Local Mode (Free)
Everything runs on your machine:
- No internet connection required
- Unlimited connectors, datasets, and joins
- Ideal for analysts, engineers, and builders

### Remote Mode (Paid, Coming Soon)
Advanced collaboration and automation:
- Team-wide access to shared plans and storage
- Scheduled runs and background jobs
- Web UI, access control, audit logs

📝 [Join the waitlist](https://datadictionary-core.vercel.app/#signup) for early access.
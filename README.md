<div align="center">

# 🦀 Ferris

### *"The Rustacean"* — Professional Rust Developer & Systems Engineer

*In safe code we trust. In unsafe blocks, we audit.*

[![Rust](https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white)](https://www.rust-lang.org/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:golden.peach.ts@gmail.com)
[![Crates.io](https://img.shields.io/badge/crates.io-FC8D62?style=for-the-badge&logo=rust&logoColor=white)](https://crates.io/users/your-handle)

</div>

---

## 👋 About Me — Call Me Ferris

I'm **Ferris** — a Rustacean through and through. I write Rust for a living, dream in lifetimes, and genuinely think `Result<T, E>` is one of the most beautiful ideas in modern programming. With **[X]+ years** of professional Rust experience, I build systems that are fast, correct, and impossible to break — the way they were always meant to be.

- 🔭 Currently building **[FluxGate](#-fluxgate--my-current-focus)** — a high-performance **AI gateway** in Rust, routing and orchestrating LLM traffic across providers
- 🌱 Diving into **async runtime internals, embedded `no_std`, and formal verification with Kani**
- 💬 Ask me about **ownership, lifetimes, async runtimes, zero-cost abstractions, or why the borrow checker is your friend**
- 🦀 I unironically love the compiler errors
- 📫 Reach me at **wb.ts416@gmail.com**

---

## 🔥 FluxGate — My Current Focus

> A **high-performance AI gateway** written in Rust. One endpoint, every model — with the safety, throughput, and observability that production LLM traffic actually demands.

**The problem:** Modern apps talk to a dozen model providers (OpenAI, Anthropic, Mistral, Bedrock, local Llama deployments, you name it). Each has different APIs, auth schemes, rate limits, failure modes, and pricing. Wiring this up in every service is a tax on every team.

**What FluxGate does:**

- 🔀 **Unified routing** — single OpenAI-compatible API, multi-provider backends, automatic fallback on failure
- ⚡ **Async-native** — built on **Tokio** + **Axum** + **Hyper** for streaming throughput at thousands of concurrent connections
- 🛡 **Guardrails** — per-key rate limiting, token budgets, prompt-level policies, PII redaction hooks
- 💾 **Smart caching** — semantic + exact-match response caching backed by **Redis**, with TTL and invalidation strategies
- 📊 **Full observability** — OpenTelemetry traces, Prometheus metrics, per-request cost attribution
- 🔌 **Pluggable** — middleware traits let you drop in custom auth, logging, routing logic without forking
- 🦀 **Zero-cost where it counts** — the hot path is allocation-conscious, lock-free where possible, and benchmarks against the leading Go and Node alternatives

**Stack:** Rust · Tokio · Axum · Tower · Hyper · SQLx · Redis · OpenTelemetry · Docker

> Status: actively building. Stars and feedback welcome once the repo goes public.

---

## 🛠 My Rust Toolbox

### Core
![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)
![Cargo](https://img.shields.io/badge/Cargo-000000?style=flat-square&logo=rust&logoColor=white)

### Async Runtimes
![Tokio](https://img.shields.io/badge/Tokio-000000?style=flat-square)
![async-std](https://img.shields.io/badge/async--std-1E90FF?style=flat-square)
![Rayon](https://img.shields.io/badge/Rayon-DEA584?style=flat-square)
![Smol](https://img.shields.io/badge/Smol-5A8DEE?style=flat-square)

### Web & Networking
![Axum](https://img.shields.io/badge/Axum-000000?style=flat-square)
![Actix](https://img.shields.io/badge/Actix-000000?style=flat-square&logo=actix&logoColor=white)
![Tonic](https://img.shields.io/badge/Tonic_gRPC-244c5a?style=flat-square)
![Hyper](https://img.shields.io/badge/Hyper-000000?style=flat-square)

### Data
![SQLx](https://img.shields.io/badge/SQLx-336791?style=flat-square)
![Diesel](https://img.shields.io/badge/Diesel-A0204C?style=flat-square)
![SeaORM](https://img.shields.io/badge/SeaORM-3D8BFD?style=flat-square)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

### AI & Observability
![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-425CC7?style=flat-square&logo=opentelemetry&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![LLM_APIs](https://img.shields.io/badge/LLM_APIs-10A37F?style=flat-square)

### Systems
![WebAssembly](https://img.shields.io/badge/WebAssembly-654FF0?style=flat-square&logo=webassembly&logoColor=white)
![Embedded](https://img.shields.io/badge/embedded--hal-FF6B35?style=flat-square)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## 🚀 Projects I Build With & Contribute To

These are real, production-grade Rust projects in the ecosystem I work with daily — and where I've opened issues, sent PRs, or built systems on top.

### 🔧 [Tokio](https://github.com/tokio-rs/tokio)
> The asynchronous runtime that powers most of the modern Rust async ecosystem.

**What it is:** A multi-threaded, work-stealing async runtime built on top of `mio` for non-blocking I/O. It provides the executor, task scheduler, timers, sync primitives, and I/O traits (`AsyncRead`, `AsyncWrite`) that nearly every async Rust crate depends on.

**Why it matters:** The cooperative scheduler with work-stealing rebalances tasks across cores automatically — you write straight-line async code and get throughput that rivals hand-tuned event loops in C. The `tokio::select!` macro for racing futures, `JoinSet` for structured concurrency, and the channel primitives (`mpsc`, `oneshot`, `broadcast`, `watch`) are tools I reach for daily.

**In FluxGate:** Tokio is the engine. Every inbound request, every upstream provider call, every cache lookup and metric emission is a Tokio task. I've spent real time understanding how the runtime handles backpressure, how to avoid blocking the executor, and when to drop down to `spawn_blocking` for CPU-bound work like tokenization.

**Stars:** ⭐ 27k+ · **Lang:** Rust

---

### ⚡ [Axum](https://github.com/tokio-rs/axum)
> An ergonomic and modular web framework built on top of Tokio, Tower, and Hyper.

**What it is:** A web framework that leans hard into Rust's type system for safety and ergonomics. Routes are just functions, handlers extract typed data via the `FromRequest` / `FromRequestParts` traits, and middleware is just Tower `Service`s composed at the router level.

**What makes it special:** Axum has no macros for routing — `Router::new().route("/users/:id", get(get_user))` is plain Rust you can grep and refactor. A handler signature like `async fn handler(State(db): State<Db>, Json(payload): Json<Body>) -> Response` is fully type-checked at compile time, including which middleware ran. Composability with the Tower ecosystem means rate limiting, retries, timeouts, and tracing snap in without bespoke integrations.

**In FluxGate:** Axum is the HTTP surface. The provider-agnostic `/v1/chat/completions` endpoint is an Axum handler that streams responses straight from upstream via Hyper, with Tower middleware handling auth, rate limits, and observability before the request even reaches my business logic.

**Stars:** ⭐ 19k+ · **Lang:** Rust

---

### 🔍 [Ripgrep](https://github.com/BurntSushi/ripgrep)
> A line-oriented search tool that recursively searches directories for a regex pattern. Faster than `grep`, `ag`, and `ack`.

**What it is:** Andrew Gallant's (`BurntSushi`) line search tool. Default-respects `.gitignore`, supports PCRE2, handles UTF-8 correctly, and parallelizes directory traversal across cores.

**What makes it special:** A masterclass in performant systems code. The underlying [`regex`](https://github.com/rust-lang/regex) crate uses a hybrid NFA/DFA approach with SIMD acceleration for literal prefixes; memory-mapped I/O on large files avoids copy overhead; parallel walking via the `ignore` crate handles huge trees without saturating syscalls. Reading the source taught me more about real-world Rust performance than any blog post.

**Why I keep it close:** Permanently in my `$PATH`. The `rg --json` output is what I pipe into custom analysis scripts when I need structured grep output — and it's a reference implementation I revisit whenever I'm trying to make my own Rust code faster.

**Stars:** ⭐ 49k+ · **Lang:** Rust

---

### 📊 [Polars](https://github.com/pola-rs/polars)
> Lightning-fast DataFrame library for Rust and Python. Faster than Pandas, often by 10–100×.

**What it is:** A DataFrame library built on Apache Arrow's columnar memory format, with a lazy query engine that does whole-query optimization — predicate pushdown, projection pushdown, common subexpression elimination — before executing anything.

**What makes it special:** Polars treats data work like a query planner treats SQL: you describe what you want with `LazyFrame`, and the engine figures out the cheapest way to compute it across multiple cores. The expression API (`col("price").mean().over("category")`) composes in ways pandas' string-based groupby never managed. Because the core is Rust, you get the same engine whether you call it from Rust, Python, or Node.

**Where I use it:** ETL pipelines where pandas runs out of memory or runtime. I've replaced multi-hour pandas jobs with Polars lazy pipelines that finish in minutes — same logic, an order of magnitude less RAM. Also useful inside FluxGate for analyzing request/cost telemetry at scale.

**Stars:** ⭐ 31k+ · **Lang:** Rust

---

### 📝 [Helix](https://github.com/helix-editor/helix)
> A post-modern modal text editor written in Rust. Tree-sitter native, LSP-first.

**What it is:** A modal editor inspired by Kakoune's selection-first model rather than Vim's verb-object model. Tree-sitter is built in for syntax-aware highlighting and structural selection; LSP support is core, not a plugin.

**What makes it special:** Selection-first editing reverses the order — `wd` ("select word, delete") instead of vim's `dw` ("delete word"). You see exactly what you're about to operate on before you operate on it. Tree-sitter integration means selections can target AST nodes (`Alt-o` to expand to the parent node, for instance) — refactoring at the structural level instead of the line level. No `.vimrc` archaeology, no plugin manager: it just works on every machine I touch.

**Why it matters to me:** Daily driver. Reading its source is one of the cleanest examples I know of how to architect a large Rust application — clean module boundaries, sensible use of channels for editor/LSP communication, and careful management of borrowing across a complex state graph.

**Stars:** ⭐ 36k+ · **Lang:** Rust

---

<div align="center">

```rust
fn main() {
    println!("Thanks for stopping by. Now go write some Rust. 🦀");
}
```

![Profile Views](https://komarev.com/ghpvc/?username=sn-chr&style=flat-square&color=orange)

</div>

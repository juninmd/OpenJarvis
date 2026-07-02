# OpenJarvis (juninmd fork)

Fork of Stanford's OpenJarvis — local-first personal AI agent framework.

## Tech Stack

- **Language:** Python 3.10+ (core), Rust (native modules via PyO3), Node.js (Claude Agent SDK runner)
- **Runtime:** uv (Python), Cargo (Rust)
- **Framework:** Custom registry-based plugin system
- **Testing:** pytest, ruff (lint), cargo clippy (Rust)
- **Documentation:** MkDocs

## Upstream

This is a fork of [github.com/open-jarvis/OpenJarvis](https://github.com/open-jarvis/OpenJarvis). See `CLAUDE.md` for detailed architecture and development guide.

## Commands

```bash
uv sync --extra dev                              # Install dev deps
uv run maturin develop -m rust/crates/openjarvis-python/Cargo.toml  # Build Rust bridge
uv run pytest tests/ -v                          # Run tests
uv run ruff check src/ tests/                    # Lint
cd rust && cargo clippy --workspace --all-targets -- -D warnings  # Rust lint
cd rust && cargo test --workspace                # Rust tests
```

## Conventions

- Registry pattern for extensible primitives
- `_stubs.py` for ABCs, `_discovery.py` for auto-detection
- `@dataclass(slots=True)` for performance
- `from __future__ import annotations` everywhere
- Optional extras fail soft with `try/except ImportError`
- Apache 2.0 license (upstream)

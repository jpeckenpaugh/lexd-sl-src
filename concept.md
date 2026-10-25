# CONCEPT: The Observable Source Engine (`lexd-sl-src`)

> *"The map is not the territory; the lens is not the light."*

`lexd-sl-src` is the reproducible computational instrument that connects upstream sign language media to downstream scientific models. It exists to observe and capture without unexamined distortion.

---

## 1. The Intent
Upstream research datasets (such as ASL-LEX 2.0 hosted via OSF/Vimeo) are living academic artifacts. They were recorded under real-world experimental protocols with stationary cameras, natural lighting variations, and human signers.

Rather than treating data preparation as a black-box preprocessing script that silently mutates pixels, `lexd-sl-src` treats ingestion as an **auditable, reproducible experiment**.

---

## 2. Guiding Invariants (The Working Temperature)
We do not freeze the pipeline into immutable stone, but we hold fast to four conservation principles:

1. **Provenance Over Assumptions**:
   - Every raw stream fetched from upstream has its exact bytes, headers, and SHA-256 hash recorded.
   - If upstream changes, the hash detects the divergence immediately.
2. **Stationary Geometry (Frame 0 Lock)**:
   - When a camera is stationary, signer motion is semantic signal, not camera drift.
   - We lock the coronal symmetry line once at resting neutral stance ($S_0$) rather than dynamically cropping per-frame, preserving natural torso lean and reach.
3. **Lossless Master Slices**:
   - $480 \times 480$ is a direct integer pixel slice from the source ($640 \times 480$ or $720 \times 480$). No pixels are resampled or synthesized at this stage.
4. **Dyadic Integer Decimation**:
   - Downsampling to model shape ($240 \times 240$) is strictly $2 \times 2$ area averaging ($0.5\times$). No fractional interpolation smearing.

---

## 3. Operational Surface
- **The Vehicle**: A single, clean, self-contained Python notebook designed to run anywhere with standard tools (`python3`, `ffmpeg`, standard libs).
- **The Destination**: Outputs are pushed downstream to `lexd.livive.net` as verified training tensors and a relational SQLite witness.

---

## 4. Open Horizons (Fluidity)
- This notebook currently speaks the ASL-LEX dialect.
- When new corpora (SignBank, WLASL, SpreadTheSign) are introduced, they become parallel input adaptors sharing the same geometrical and cryptographic invariants.

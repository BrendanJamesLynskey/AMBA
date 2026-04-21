# ⇄ Arm AMBA Presentation Series

Interactive slide decks covering Arm's **Advanced Microcontroller Bus Architecture (AMBA)** — from the 1996 release of AMBA 1 through the modern AMBA 5 CHI used in every multi-cluster Arm SoC, plus what comes next for chiplets, accelerators, and confidential compute.

Designed as interview preparation for SoC, silicon, and firmware engineers who build or verify Arm-based systems.

## ▶ [Open the Series Landing Page](https://brendanjameslynskey.github.io/AMBA/)

> **Setup:** Enable GitHub Pages (Settings → Pages → Deploy from `main` branch, `/ (root)` directory).
>
> Alternatively, open `index.html` locally in any browser — all presentations work offline after first load.

---

## Presentations

| # | Topic | Slides | Status |
|---|-------|--------|--------|
| 01 | History of AMBA — 1996 → 2024 | 22 | ✅ Complete |
| 02 | AHB &amp; APB — the Original Protocols | 20 | ✅ Complete |
| 03 | AXI Deep Dive — Channels, Bursts &amp; Ordering | 22 | ✅ Complete |
| 04 | ACE &amp; ACE-Lite — Coherency over AXI | 20 | ✅ Complete |
| 05 | CHI — Scalable Multi-Cluster Coherency | 20 | ✅ Complete |
| 06 | Future of AMBA — Chiplets, CXL, AI &amp; CCA | 20 | ✅ Complete |

---

## Presentation 01: History of AMBA

22 slides covering the full arc of Arm's on-chip interconnect:

**1996 — AMBA 1 (ASB &amp; APB)** — a 32-bit System Bus and a simple Peripheral Bus, released as an open specification to accelerate Arm-based SoC integration at a time when every ASIC vendor had its own proprietary bus.

**1999 — AMBA 2 (AHB)** — Advanced High-performance Bus replaces ASB. Single-clock-edge, pipelined, split/retry, burst transfers, multi-master arbitration. Becomes the de-facto 32-bit SoC bus for a decade.

**2003 — AMBA 3 (AXI, ATB, APB3)** — AXI introduces five independent channels (AR, R, AW, W, B), out-of-order transactions, and ID-based interleaving. ATB (AMBA Trace Bus) unifies CoreSight trace.

**2010 — AMBA 4 (AXI4, ACE, QoS, AXI4-Lite, AXI4-Stream)** — burst length up to 256, QoS fields, user-sideband, and **ACE** adds cache coherency to AXI. AXI4-Stream becomes the lingua franca of FPGA DSP pipelines.

**2013 — AMBA 5 (CHI)** — a clean-sheet packetised protocol for &gt;16-cluster systems. Used in the Arm CMN-600/650/700 mesh interconnects that back every Neoverse-N/V server CPU.

**2017 — AMBA 5 refresh (AXI5, AHB5, APB5, ACE5, CHI-B/C/D/E)** — atomics, user request attributes, MTE / TrustZone extensions, and cache stashing.

**2023+** — CHI-C2C for chiplet-to-chiplet over **UCIe**; MPAM for QoS and partitioning; convergence with CXL.mem; AMBA-over-PCIe bridges.

## Presentation 02: AHB &amp; APB

20 slides on the original high-performance and peripheral protocols — the **AHB phase model** (address/data phases, HREADY backpressure, HRESP), **AHB-Lite** simplification (single master, no retry/split), **AHB5** additions (secure/non-secure, exclusive access, user signals), the **APB bus** (PSEL/PENABLE two-phase handshake), APB3/APB4/APB5 additions (PSLVERR, PPROT, PWAKEUP, RME), multi-layer AHB vs crossbar, and when to still choose AHB today (low-power MCU subsystems).

## Presentation 03: AXI Deep Dive

22 slides on the workhorse of modern SoCs — the **five channels** (AR/R/AW/W/B), the **VALID/READY** handshake, burst types (FIXED/INCR/WRAP), burst lengths (AXI3: 1–16; AXI4: 1–256), **AXI IDs** for out-of-order transactions, the AXI3 write-interleaving feature and why AXI4 removed it, **exclusive access** (EXOKAY), **QoS**, **USER** sideband, **AXI4-Lite** (single-beat, no IDs) and **AXI4-Stream** (pure data pipe, no address), common pitfalls (WLAST/RLAST, AWREADY-before-AWVALID legality, deadlock rings), and how a crossbar routes and reorders.

## Presentation 04: ACE &amp; ACE-Lite

20 slides on Arm's first coherent on-chip protocol — the **three extra snoop channels** (AC, CR, CD), the **five cache states** (UniqueClean, UniqueDirty, SharedClean, SharedDirty, Invalid) that form a MOESI variant, **ReadShared / ReadUnique / CleanUnique / MakeUnique** transaction types, **DVM** (Distributed Virtual Memory) messages for TLB invalidates, memory barriers, **ACE-Lite** for one-way I/O coherency (DMA, GPU, NIC), and the CCI-400 / CCI-500 / CCI-550 Cache-Coherent Interconnects that used it.

## Presentation 05: CHI — Scalable Coherency

20 slides on the clean-sheet packetised interconnect behind Neoverse — **node types** (RN-F, RN-I, HN-F, HN-I, SN-F, MN), the **four message channels** (REQ / RSP / SNP / DAT), **cache states** (UC, UD, SC, SD, I), **Home-based snoops** and the directory at the HN-F, **snoop filter** operation, **DMT / DCT** (Direct-Memory / Direct-Cache Transfer), **QoS classes**, **Retry** and DVM, the **CMN-600 / CMN-650 / CMN-700 mesh interconnects**, and how CHI scales to 128+ coherent nodes across Neoverse V2 clusters.

## Presentation 06: Future of AMBA

20 slides on where AMBA is going — **CHI-C2C** for coherent chiplet-to-chiplet transport over **UCIe** (Universal Chiplet Interconnect Express), **MPAM** (Memory-system Partitioning and Monitoring) for QoS/QoE in servers, **RME** (Realm Management Extension) and the AMBA hooks that implement **Arm Confidential Compute Architecture (CCA)**, AMBA's role in **AI accelerators** (NPUs, HBM3/4 paths, scatter-gather DMA), **CXL.mem coexistence** (near-memory expanders over CHI, pooled memory over CXL), convergence trends, and how verification is shifting from UVM to formal + protocol-checking IP.

---

## Technical details

- **Framework:** [Reveal.js 4.6.1](https://revealjs.com) from CDN
- **Fonts:** Playfair Display (headings), DM Sans (body), JetBrains Mono (code)
- **Offline:** works after first load (fonts &amp; Reveal.js cached by the browser)
- **Navigation:** `→` / `←` for slides, `Esc` for overview, `F` for fullscreen, `S` for speaker notes

## Related repositories

- [Hardware](https://github.com/BrendanJamesLynskey/Hardware) — parent hub
- [Arm Cortex-M Presentation Series](https://github.com/BrendanJamesLynskey/Cortex_M) — sibling deck set on the M-profile CPU
- [AXI4 Crossbar](https://github.com/BrendanJamesLynskey/AXI4_Crossbar) — synthesisable RTL companion for Presentation 03
- [Modern SoC Design](https://github.com/BrendanJamesLynskey/SoC) — same visual style, complementary topics

## License

Educational use. Content © Brendan Lynskey. Fonts and Reveal.js retain their own licenses.

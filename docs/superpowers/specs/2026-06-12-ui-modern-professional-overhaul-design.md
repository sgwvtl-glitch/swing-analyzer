---
name: ui-modern-professional-overhaul
date: 2026-06-12
status: approved
---

# UI Modern Professional Overhaul Design

## Goal
Improve the visibility and professional aesthetic of the Fibonacci Swing Analyzer. The current muted beige/gray scheme lacks sufficient contrast, making labels and backgrounds difficult to see.

## Visual Strategy
Transition from a muted, low-contrast neutral palette to a high-contrast "Modern Professional" Slate and Navy system. This system leverages deep navy backgrounds and crisp, off-white typography to create a a "Trading Terminal" look.

## Color Palette Mapping

### Core Surfaces & Typography
| Element | Light Mode | Dark Mode | Purpose |
| :--- | :--- | :--- | :--- |
| Page Background | `#f8fafc` | `#0f172a` | Ice White $\rightarrow$ Deep Navy |
| Card Background | `#ffffff` | `#1e293b` | Pure White $\rightarrow$ Slate Blue |
| Card Borders | `#e2e8f0` | `#334155` | Subtle Slate contrast |
| Primary Text | `#0f172a` | `#f8fafc` | Deep Slate $\rightarrow$ Off-White |
| Labels (`.lbl`) | `#64748b` | `#94a3b8` | High-contrast Slate Gray |
| Section Titles | `#64748b` | `#94a3b8` | Clean, readable anchors |

### Trading Signals (Saturated Terminal Colors)
| State | Light Mode (BG $\rightarrow$ Text) | Dark Mode (BG $\rightarrow$ Text) | Tone |
| :--- | :--- | :--- | :--- |
| Bullish (`.bg`) | `#dcfce7` $\rightarrow$ `#166534` | `#064e3b` $\rightarrow$ `#34d399` | Emerald |
| Bearish (`.br`) | `#fee2e2` $\rightarrow$ `#991b1b` | `#7f1d1d` $\rightarrow$ `#f87171` | Crimson |
| Warning (`.bw`) | `#fef3c7` $\rightarrow$ `#92400e` | `#78350f` $\rightarrow$ `#fbbf24` | Amber |
| Info (`.bi`) | `#dbeafe` $\rightarrow$ `#1e40af` | `#1e3a8a` $\rightarrow$ `#60a5fa` | Royal Blue |
| Neutral (`.bn`) | `#f1f5f9` $\rightarrow$ `#475569` | `#334155` $\rightarrow$ `#cbd5e1` | Slate |

### Major Signal Blocks (`.sig`)
- **Long (`.sig-long`):** Uses the Emerald palette (Dark Mode: `#064e3b` bg, `#34d399` text).
- **Short (`.sig-short`):** Uses the Crimson palette (Dark Mode: `#7f1d1d` bg, `#f87171` text).
- **None (`.sig-none`):** Uses the Neutral Slate palette (Dark Mode: `#334155` bg, `#cbd5e1` text).

## Implementation Notes
- The changes will be implemented directly within the `<style>` block of `index.html`.
- All existing CSS classes (`.lbl`, `.val`, `.card`, `.bg`, `.br`, etc.) will be retained to avoid breaking the JavaScript rendering logic.
- Focus will be on ensuring the `@media(prefers-color-scheme:dark)` block is fully aligned with the new Navy/Slate system.

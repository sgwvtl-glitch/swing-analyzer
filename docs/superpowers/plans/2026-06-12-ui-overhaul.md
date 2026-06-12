# UI Modern Professional Overhaul Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Transition the UI from a muted beige/gray scheme to a high-contrast Modern Professional Slate & Navy theme to improve visibility and aesthetics.

**Architecture:** Updates are applied exclusively to the inline CSS within `index.html`. No changes to HTML structure or JavaScript logic are required.

**Tech Stack:** HTML, CSS.

---

## File Map
- Modify: `C:\My_Codes\swing-analyzer\swing-analyzer\index.html` (CSS block)

---

### Task 1: Core Surfaces & Typography Update

**Files:**
- Modify: `C:\My_Codes\swing-analyzer\swing-analyzer\index.html`

- [ ] **Step 1: Update Light Mode Body and Card Styles**
Replace:
```css
  body{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;background:#f5f5f0;color:#1a1a18;padding:1.5rem;max-width:720px;margin:0 auto}
```
With:
```css
  body{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;background:#f8fafc;color:#0f172a;padding:1.5rem;max-width:720px;margin:0 auto}
```

Replace:
```css
  .card{background:#fff;border:1px solid #e8e6df;border-radius:12px;padding:1rem 1.25rem;margin-bottom:10px}
```
With:
```css
  .card{background:#ffffff;border:1px solid #e2e8f0;border-radius:12px;padding:1rem 1.25rem;margin-bottom:10px}
```

- [ ] **Step 2: Update Light Mode Typography**
Replace:
```css
  .sub{font-size:12px;color:#888780;margin-bottom:1.25rem}
```
With:
```css
  .sub{font-size:12px;color:#64748b;margin-bottom:1.25rem}
```

Replace:
```css
  .s-title{font-size:11px;font-weight:500;color:#888780;letter-spacing:.05em;text-transform:uppercase;margin-bottom:8px}
```
With:
```css
  .s-title{font-size:11px;font-weight:500;color:#64748b;letter-spacing:.05em;text-transform:uppercase;margin-bottom:8px}
```

Replace:
```css
  .lbl{font-size:12px;color:#5f5e5a;margin-bottom:3px}
```
With:
```css
  .lbl{font-size:12px;color:#64748b;margin-bottom:3px}
```

- [ ] **Step 3: Update Dark Mode Body and Card Styles**
In `@media(prefers-color-scheme:dark)`:
Replace:
```css
    body{background:#1e1e1c;color:#e8e6df}
```
With:
```css
    body{background:#0f172a;color:#f8fafc}
```

Replace:
```css
    .card{background:#2c2c2a;border-color:#444441}
```
With:
```css
    .card{background:#1e293b;border-color:#334155}
```

- [ ] **Step 4: Update Dark Mode Typography**
In `@media(prefers-color-scheme:dark)`:
Replace:
```css
    .lbl{color:#b4b2a9}
```
With:
```css
    .lbl{color:#94a3b8}
```

Replace:
```css
    .val{color:#e8e6df}
```
With:
```css
    .val{color:#f8fafc}
```

Replace:
```css
    .s-title{color:#888780}
```
With:
```css
    .s-title{color:#94a3b8}
```

- [ ] **Step 5: Commit**
```bash
git add C:\My_Codes\swing-analyzer\swing-analyzer\index.html
git commit -m "ui: update core surfaces and typography to Slate/Navy professional theme"
```

### Task 2: Trading Signal Colors (Badges)

**Files:**
- Modify: `C:\My_Codes\swing-analyzer\swing-analyzer\index.html`

- [ ] **Step 1: Update Light Mode Badge Colors**
Replace:
```css
  .bg{background:#eaf3de;color:#27500a}
  .br{background:#fcebeb;color:#791f1f}
  .bw{background:#faeeda;color:#633806}
  .bi{background:#e6f1fb;color:#0c447c}
  .bn{background:#f1efe8;color:#444441}
```
With:
```css
  .bg{background:#dcfce7;color:#166534}
  .br{background:#fee2e2;color:#991b1b}
  .bw{background:#fef3c7;color:#92400e}
  .bi{background:#dbeafe;color:#1e40af}
  .bn{background:#f1f5f9;color:#475569}
```

- [ ] **Step 2: Update Dark Mode Badge Colors**
In `@media(prefers-color-scheme:dark)`:
Replace:
```css
    .bg{background:#173404;color:#c0dd97}
    .br{background:#501313;color:#f09595}
    .bw{background:#412402;color:#fac775}
    .bi{background:#042c53;color:#85b7eb}
    .bn{background:#3a3a38;color:#b4b2a9}
```
With:
```css
    .bg{background:#064e3b;color:#34d399}
    .br{background:#7f1d1d;color:#f87171}
    .bw{background:#78350f;color:#fbbf24}
    .bi{background:#1e3a8a;color:#60a5fa}
    .bn{background:#334155;color:#cbd5e1}
```

- [ ] **Step 3: Commit**
```bash
git add C:\My_Codes\swing-analyzer\swing-analyzer\index.html
git commit -m "ui: implement high-contrast saturated trading signal colors"
```

### Task 3: Signal Banners and Special Boxes

**Files:**
- Modify: `C:\My_Codes\swing-analyzer\swing-analyzer\index.html`

- [ ] **Step 1: Update Signal Block Backgrounds (Light Mode)**
Replace:
```css
  .sig-long{background:#eaf3de}
  .sig-short{background:#fcebeb}
  .sig-none{background:#f1efe8}
```
With:
```css
  .sig-long{background:#dcfce7}
  .sig-short{background:#fee2e2}
  .sig-none{background:#f1f5f9}
```

- [ ] **Step 2: Update Signal Block Text (Light Mode)**
Replace:
```css
  .sig-long .sv{color:#27500a}
  .sig-short .sv{color:#791f1f}
  .sig-none .sv{color:#444441}
```
With:
```css
  .sig-long .sv{color:#166534}
  .sig-short .sv{color:#991b1b}
  .sig-none .sv{color:#475569}
```

- [ ] **Step 3: Update Signal Block Backgrounds (Dark Mode)**
In `@media(prefers-color-scheme:dark)`:
Replace:
```css
    .sig-long{background:#173404}
    .sig-short{background:#501313}
    .sig-none{background:#3a3a38}
```
With:
```css
    .sig-long{background:#064e3b}
    .sig-short{background:#7f1d1d}
    .sig-none{background:#334155}
```

- [ ] **Step 4: Update Signal Block Text (Dark Mode)**
In `@media(prefers-color-scheme:dark)`:
Replace:
```css
    .sig-long .sv{color:#c0dd97}
    .sig-short .sv{color:#f09595}
    .sig-none .sv{color:#b4b2a9}
```
With:
```css
    .sig-long .sv{color:#34d399}
    .sig-short .sv{color:#f87171}
    .sig-none .sv{color:#cbd5e1}
```

- [ ] **Step 5: Update Special UI Components**
Replace:
```css
  .sz-box{padding:10px;background:#f5f5f0;border-radius:8px;font-size:13px;line-height:1.6}
```
With:
```css
  .sz-box{padding:10px;background:#f1f5f9;border-radius:8px;font-size:13px;line-height:1.6}
```

Replace:
```css
  #st{font-size:13px;color:#5f5e5a;min-height:18px;margin-bottom:8px}
```
With:
```css
  #st{font-size:13px;color:#64748b;min-height:18px;margin-bottom:8px}
```

In `@media(prefers-color-scheme:dark)`:
Replace:
```css
    .sz-box{background:#3a3a38}
```
With:
```css
    .sz-box{background:#334155}
```

Replace:
```css
    #st{color:#888780}
```
With:
```css
    #st{color:#94a3b8}
```

- [ ] **Step 6: Commit**
```bash
git add C:\My_Codes\swing-analyzer\swing-analyzer\index.html
git commit -m "ui: update signal banners and special UI components to new palette"
```

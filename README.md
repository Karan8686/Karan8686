# Hi there, I'm Karan Palav 👋

<div align="left">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=38BDF8&width=620&lines=Flutter+%26+Mobile+App+Engineer;Full-Stack+TypeScript+%26+React+Architect;AI+Integration+%26+Multi-Model+LLM+Pipelines;Creator+of+caveman-plus+%26+adaptive_image_picker;Architect+%26+Developer+of+CV+Bucket" alt="Typing SVG" />
  </a>
</div>

<br />

<p align="left">
  <a href="https://pub.dev/publishers/karan8686/packages"><img src="https://img.shields.io/badge/Pub.dev-Package%20Author-0175C2?style=for-the-badge&logo=dart&logoColor=white" alt="Pub.dev Author" /></a>
  <a href="https://karan8686.github.io/caveman-plus/"><img src="https://img.shields.io/badge/AI%20Tooling-caveman--plus-8A2BE2?style=for-the-badge&logo=openai&logoColor=white" alt="AI Tooling" /></a>
  <a href="mailto:Kpalav098@gmail.com"><img src="https://img.shields.io/badge/Contact-Get%20In%20Touch-10B981?style=for-the-badge&logo=gmail&logoColor=white" alt="Get In Touch" /></a>
</p>

---

## ⚡ Featured Project Spotlights

### 📄 1. [CV Bucket](https://github.com/usesinspiration-ship-it/Cv_bucket) — Multi-Model AI Resume Indexing Platform
> **Sole Architect & Full-Stack Developer**  
> An intelligent resume parsing, indexing, and search engine built with **React 19**, **Express**, **Supabase (PostgreSQL)**, and **Cloudflare R2**. Features a resilient **OCR fallback layer** and a **3-Tier AI model pipeline** (Groq $\to$ Gemini Vision $\to$ Local Regex) to parse digital, scanned, and Canva resumes with zero data loss.

#### ☁️ End-to-End System & AI Architecture
```mermaid
flowchart TD
    User([Recruiter / Candidate]) -->|Upload PDF, DOCX, or Scanned CV| UI[React 19 + Tailwind CSS]
    UI -->|Multipart Upload Stream + Auth| API[Express TypeScript Backend]
    
    API -->|Async Binary Storage| R2[(Cloudflare R2 Object Storage)]
    API --> Extractor{Format & Text Layer Check}
    
    Extractor -->|DOCX / DOC| DocParser[mammoth / word-extractor]
    Extractor -->|Digital PDF| PDFParser[pdfjs-dist Text Engine]
    
    PDFParser --> Check{Sparse / Image-Only PDF?<br/>&lt; 250 chars / 40 words}
    Check -->|No| AI_Tiers
    Check -->|Yes: Canva / Scanned| OCR[OCR.space Dual Engine<br/>Engine 2 with Engine 1 Failover]
    
    OCR --> OCR_Check{OCR Extracted Text?}
    OCR_Check -->|Yes| AI_Tiers
    OCR_Check -->|No| Tier2_Vision
    
    subgraph AI_Tiers ["3-Tier Multi-AI Intelligence Pipeline"]
        Tier1[Tier 1: High-Throughput LLMs via Groq<br/>gpt-oss-120b / gpt-oss-20b]
        Tier2_Vision[Tier 2: Gemini Multimodal Vision<br/>gemini-3.5-flash Native PDF Vision]
        Tier3[Tier 3: Local Deterministic Engine<br/>Offline RegEx / NLP Fallback]
        
        Tier1 -->|Fallback on Rate Limit/Error| Tier2_Vision
        Tier2_Vision -->|Fallback on Failure| Tier3
    end
    
    DocParser --> AI_Tiers
    
    AI_Tiers --> Normalizer[Data Normalization & Null Sanitization]
    Normalizer --> Dedupe{SHA-256 Hash Deduplication}
    Dedupe --> DB[(Supabase PostgreSQL<br/>Indexed Records + Full-Text Search)]
    
    UI -->|Real-Time Candidate Search| FTS[PostgreSQL FTS Query Engine]
    FTS --> DB
```

---

### 📸 2. [adaptive_image_picker](https://github.com/Karan8686/adaptive_image_picker) — Zero-Permission Media Picker & Cropper
> **Published Flutter / Dart Package** on [pub.dev](https://pub.dev/packages/adaptive_image_picker)  
> Solves traditional storage permission issues by pairing native zero-permission system pickers with a pure-Dart interactive cropper and binary-search file compressor.

<div align="center">

| ✂️ Pure-Dart Gesture Cropper & Filter | 📱 Full Adaptive Workflow |
| :---: | :---: |
| <img src="https://raw.githubusercontent.com/Karan8686/adaptive_image_picker/main/doc/demo.gif" width="350" alt="Interactive Cropper" style="border-radius: 8px;" /> | <img src="https://raw.githubusercontent.com/Karan8686/adaptive_image_picker/main/doc/demo_full.gif" width="350" alt="Full Workflow" style="border-radius: 8px;" /> |

</div>

#### 🏛️ Zero-Permission Architecture Flow
```mermaid
flowchart LR
    A[User Action] --> B{Adaptive Source}
    B -->|Gallery| C[Zero-Permission PhotoPicker<br/>Android 13+ & iOS 14+]
    B -->|Camera| D[Native Camera Capture]
    B -->|Remote| E[HTTP Image Downloader]
    
    C --> F[Raw Image Stream]
    D --> F
    E --> F
    
    F --> G[Pure-Dart Interactive Cropper<br/>Pinch, Pan, Aspect Ratios, Circle Mask]
    G --> H[Binary-Search Compressor<br/>Guaranteed byte limit ≤ maxBytes]
    H --> I[Optimized Output File]
```

---

### 🪨 3. [caveman-plus](https://github.com/Karan8686/caveman-plus) — AI Token Compression Engine
> **Published npm Package & CLI** • [Try the Live Interactive Playground →](https://karan8686.github.io/caveman-plus/)  
> Programmatic text compression engine for LLMs and AI pipelines. Strips 40–70% of redundant tokens while preserving 100% of code, errors, and technical meaning.

```text
Input:  "This is basically just a really verbose sentence that could definitely be compressed quite a bit."
Output: "This is a verbose sentence that could be compressed a bit."  (-54% tokens saved)
```

#### 🔄 Token Compression Pipeline
```mermaid
flowchart LR
    Prompt[Verbose AI Prompt / Context] --> Parser[Syntactic & AST Classifier]
    Parser --> Guard{Code or Log Block?}
    Guard -->|Yes| Raw[Preserve Verbatim]
    Guard -->|No| Engine[Pattern Normalizer & Filler Stripper]
    Raw --> Output[Compressed Stream / Payload<br/>40-70% Cost Reduction]
    Engine --> Output
```

---

### 🖼️ 4. [adaptive_image_loader](https://github.com/Karan8686/adaptive_image_loader) — Edge CDN Image Resolver
> **Published Flutter / Dart Package** on [pub.dev](https://pub.dev/packages/adaptive_image_loader)  
> High-performance drop-in replacement for `Image.network` that converts Google Drive and Dropbox links into direct Edge CDN streams with 0 redirects and on-the-fly server downscaling.

| Challenge with `Image.network` | `AdaptiveImage` Solution ⚡ | Impact |
| :--- | :--- | :--- |
| **Google Drive Links Fail / 302 Redirect** | Resolves directly to `lh3.googleusercontent.com` | **0 Redirects & Instant First Byte** |
| **Massive 15MB Photos cause OOM** | Edge CDN dynamic resizing parameter (`=s400`) | **Saves up to 95% device RAM** |
| **Dropbox Shared Links Show HTML Preview** | Auto-converts to raw media stream (`?dl=1`) | **Zero broken images** |
| **Re-downloading on every view** | Built-in disk cache with programmatic eviction | **Offline-ready caching** |

---

## 🛠️ Tech Stack & Capabilities

<table>
  <tr>
    <td align="center" width="180"><strong>Mobile & Cross-Platform</strong></td>
    <td>
      <img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter" />
      <img src="https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white" alt="Dart" />
      <img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android" />
      <img src="https://img.shields.io/badge/State_Management-Riverpod_%2F_Bloc-blue?style=for-the-badge" alt="State Management" />
    </td>
  </tr>
  <tr>
    <td align="center"><strong>Frontend & Web</strong></td>
    <td>
      <img src="https://img.shields.io/badge/React_19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React 19" />
      <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
      <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind" />
      <img src="https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite" />
    </td>
  </tr>
  <tr>
    <td align="center"><strong>AI & LLM Pipelines</strong></td>
    <td>
      <img src="https://img.shields.io/badge/Google_Gemini_Vision-8E75C2?style=for-the-badge&logo=google&logoColor=white" alt="Gemini" />
      <img src="https://img.shields.io/badge/Groq_LLMs-F55036?style=for-the-badge&logo=fastapi&logoColor=white" alt="Groq" />
      <img src="https://img.shields.io/badge/OCR.space-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white" alt="OCR" />
      <img src="https://img.shields.io/badge/Prompt_Engineering-333333?style=for-the-badge&logo=openai&logoColor=white" alt="Prompts" />
    </td>
  </tr>
  <tr>
    <td align="center"><strong>Backend, Cloud & Database</strong></td>
    <td>
      <img src="https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white" alt="Supabase" />
      <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
      <img src="https://img.shields.io/badge/Cloudflare_R2-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" alt="Cloudflare" />
      <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js" />
      <img src="https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white" alt="Express" />
      <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" />
    </td>
  </tr>
</table>

---

## 📊 GitHub Analytics

<div align="center">
  <img src="https://github-readme-stats-eight-theta.vercel.app/api?username=Karan8686&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" alt="Karan's GitHub Stats" height="165" />
  &nbsp;
  <img src="https://github-readme-stats-eight-theta.vercel.app/api/top-langs/?username=Karan8686&layout=compact&theme=tokyonight&hide_border=true" alt="Top Languages" height="165" />
</div>

<div align="center" style="margin-top: 10px;">
  <img src="https://streak-stats.demolab.com/?user=Karan8686&theme=tokyonight&hide_border=true" alt="Karan's Streak" height="165" />
</div>

---

## 📬 Connect & Collaborate

<div align="left">
  <a href="mailto:Kpalav098@gmail.com">
    <img src="https://img.shields.io/badge/Email-Kpalav098@gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
  </a>
  &nbsp;
  <a href="https://github.com/Karan8686">
    <img src="https://img.shields.io/badge/GitHub-Karan8686-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  </a>
  &nbsp;
  <a href="https://karan8686.github.io/caveman-plus/">
    <img src="https://img.shields.io/badge/Demo-caveman--plus%20Live-8A2BE2?style=for-the-badge" alt="Demo" />
  </a>
</div>

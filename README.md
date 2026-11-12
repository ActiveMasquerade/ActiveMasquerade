<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=190&section=header&text=Kanishk%20Sagar&fontColor=ffffff&fontSize=52&fontAlignY=36&desc=ML%20%C2%B7%20systems%20%C2%B7%20things%20built%20from%20scratch&descAlignY=58&descSize=17" alt="Kanishk Sagar" />

<p align="center">
  <a href="https://github.com/ActiveMasquerade">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=19&duration=2800&pause=900&color=4FC3F7&center=true&vCenter=true&width=560&lines=Fine-tuning+small+LLMs+that+punch+up;Writing+databases+and+emulators+in+C%2B%2B23;Building+RAG+you+can+actually+measure;Shipping+the+model%2C+not+just+the+notebook" alt="Typing intro" />
  </a>
</p>

<p align="center">
  <a href="https://github.com/ActiveMasquerade?tab=repositories"><img src="https://img.shields.io/badge/Repositories-181717?style=flat-square&logo=github&logoColor=white" alt="Repositories" /></a>
  <a href="https://www.kaggle.com/elderhu"><img src="https://img.shields.io/badge/Kaggle-20BEFF?style=flat-square&logo=kaggle&logoColor=white" alt="Kaggle" /></a>
  <a href="https://www.instagram.com/classycorpse"><img src="https://img.shields.io/badge/Instagram-E4405F?style=flat-square&logo=instagram&logoColor=white" alt="Instagram" /></a>
  <img src="https://komarev.com/ghpvc/?username=ActiveMasquerade&style=flat-square&color=2c5364&label=profile+views" alt="Profile views" />
</p>

---

```python
class Kanishk:
    focus     = ["LLM fine-tuning", "retrieval", "systems in C++"]
    stack     = ["Python", "PyTorch", "C++", "FastAPI", "JavaScript"]
    currently = "distilling a multilingual tool-calling agent (Lexsi AI hackathon)"
    habit     = "if there's no benchmark, it doesn't count yet"
    fun_fact  = "adult orcas have no natural predators 🐋"
```

## 🧰 Toolbox

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=py,pytorch,cpp,fastapi,js,react,tailwind,mongodb,cmake,vite,git,linux&perline=12" alt="Skills" />
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Hugging%20Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black" />
  <img src="https://img.shields.io/badge/QLoRA%20%2F%20PEFT-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" />
  <img src="https://img.shields.io/badge/ChromaDB-FF6446?style=flat-square" />
  <img src="https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white" />
  <img src="https://img.shields.io/badge/GoogleTest-4285F4?style=flat-square&logo=google&logoColor=white" />
  <img src="https://img.shields.io/badge/Kaggle%20GPUs-20BEFF?style=flat-square&logo=kaggle&logoColor=white" />
</p>

| Area | What I reach for |
|---|---|
| **ML / LLMs** | PyTorch, Hugging Face Transformers, PEFT/QLoRA, SFT → GRPO, eval harnesses |
| **Backend** | FastAPI, MongoDB, ChromaDB, JWT auth, streaming responses |
| **Systems** | Modern C++ (C++23, `std::expected`, `std::span`), CMake, GoogleTest, Google Benchmark |
| **Frontend** | JavaScript, React, Vite, Tailwind |

---

## 🚀 Featured work

### 🗄️ [VectorLite](https://github.com/ActiveMasquerade/mini_database): an embedded SQL database with vector search, from scratch
<img src="https://img.shields.io/badge/C++23-00599C?style=flat-square&logo=cplusplus&logoColor=white" /> <img src="https://img.shields.io/badge/B%2B%20Tree-555?style=flat-square" /> <img src="https://img.shields.io/badge/HNSW-555?style=flat-square" /> <img src="https://img.shields.io/badge/WAL-555?style=flat-square" />

SQLite-style embedded engine (one library, one file, no server) where a `VECTOR(384)` column and a `WHERE author = 'Alice'` filter live in the **same query plan**. Relational predicates narrow the candidates before any distance math runs.

**~89 ms → ~0.3 ms** p50 vector search with HNSW · **recall@10 = 1.00** on a 10k × 384 corpus · WAL with redo/undo crash recovery

<details>
<summary><b>Under the hood</b></summary>
<br/>

- A real B+Tree with split, merge, redistribution and root collapse, sitting on 4 KB pages behind an LRU buffer pool. Pages are read through `std::span` views and never copied on the hot path.
- `BEGIN` / `COMMIT` / `ROLLBACK` backed by a write-ahead log embedded in the database file.
- HNSW only becomes the default search path once its recall clears a fixed threshold against the exact-scan baseline.
- Property-based fuzzing of B+Tree invariants over randomized insert/delete sequences.
- Every public API returns `Result<T>` (`std::expected`), so no exception ever crosses a module boundary.
</details>

---

### 🌌 [Constellation](https://github.com/ActiveMasquerade/RAG_personal): personal RAG with a built-in evaluation dashboard
<img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" /> <img src="https://img.shields.io/badge/React%2019-20232A?style=flat-square&logo=react&logoColor=61DAFB" /> <img src="https://img.shields.io/badge/ChromaDB-FF6446?style=flat-square" /> <img src="https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white" /> <img src="https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white" />

Upload PDFs, Markdown and CSVs, then chat over them with citations, explore a similarity graph of your library, and **score your own retrieval**. The app writes golden questions from your chunks and runs them through the production pipeline (query rewrite → vector search → Cohere rerank).

**Hit rate 100% · MRR 1.00** on a 2,635-chunk technical corpus · **83.3%** on an adversarial set where two different PDFs share the same filename

---

### ⚖️ [fine-tuning-gemma](https://github.com/ActiveMasquerade/fine-tuning-gemma): Gemma 3 1B for legal reasoning
<img src="https://img.shields.io/badge/Gemma%203%201B-4285F4?style=flat-square&logo=google&logoColor=white" /> <img src="https://img.shields.io/badge/QLoRA%204--bit-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" /> <img src="https://img.shields.io/badge/CaseHOLD-555?style=flat-square" />

QLoRA fine-tune of a 1B instruct model on CaseHOLD (LexGLUE): pick the correct holding out of five candidates, on consumer and Colab-class GPUs.

**18.0% → 27.0% accuracy** (+50% relative) from 5,625 training examples with only LoRA adapters trained

---

### 🕹️ [Chip8++](https://github.com/ActiveMasquerade/chip8_emu): a deterministic CHIP-8 emulator
<img src="https://img.shields.io/badge/C++23-00599C?style=flat-square&logo=cplusplus&logoColor=white" /> <img src="https://img.shields.io/badge/SDL2-1D4E89?style=flat-square" /> <img src="https://img.shields.io/badge/GoogleTest-4285F4?style=flat-square&logo=google&logoColor=white" />

All **35 opcodes** follow the original COSMAC VIP behavior. The four ambiguous "quirk" instructions each get a documented default instead of whatever the last tutorial did. The core is headless with **zero SDL dependency**, so the full test suite runs anywhere, and SDL2 is just an optional frontend.

---

### 🗣️ [Desi Agent](https://github.com/CyberRik/desi-agent): multilingual banking agent *(in progress, with [@CyberRik](https://github.com/CyberRik))*
<img src="https://img.shields.io/badge/tiny--aya--global-6236FF?style=flat-square" /> <img src="https://img.shields.io/badge/SFT%20%E2%86%92%20GRPO-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" /> <img src="https://img.shields.io/badge/Kaggle-20BEFF?style=flat-square&logo=kaggle&logoColor=white" />

Lexsi AI Safety & Alignment Hackathon 2026, Track 3. We're distilling reliable tool calling into a ~3B open model for English, Hindi, Bengali, Hinglish and Banglish ("mera card block kar do"), and scoring it per language, including **false actions** the user never asked for. I own the training and shipping lane.

---

## 📈 Activity

<p align="center">
  <img src="https://streak-stats.demolab.com?user=ActiveMasquerade&theme=tokyonight&hide_border=true&border_radius=10" alt="GitHub streak" />
</p>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:203a43,100:0f2027&height=110&section=footer" alt="" />

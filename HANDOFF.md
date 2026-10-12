# HANDOFF.md – Session Continuation Guide for Next AI

**Date of handoff:** 2026-10-12  
**Previous AI:** Grok (xAI)  
**GitHub repo:** https://github.com/imanbarati/session-handoff-textbooks-asr-scrapes  
**User language preference:** Mix of English + Persian (Farsi). Respond in the language the user uses.

---

## 1. Overall Conversation Arc

1. User asked about hardware to run `mehdi-hf/nemotron-asr-streaming-farsi` (Persian streaming ASR) with Hermes.
2. Discussed phone / Steam Deck feasibility → provided clean Linux/Steam Deck install script.
3. Asked whether the Farsi ASR could make phone calls with Gemini → clarified it cannot; Gemini Live API + Twilio is the proper path.
4. Requested clean install script + cheaper alternatives.
5. Switched to scraping tasks:
   - Iranian official textbook portals (chap.oerp.ir / chap.sch.ir / chap.roshd.ir)
   - Ayrik Service product pages (POS + ATM parts)
   - Global trending topics suitable for SEO content (NOT articles about SEO itself)

---

## 2. Key Assets Already Produced

### Farsi ASR
- Model: `mehdi-hf/nemotron-asr-streaming-farsi` (600M, FastConformer + RNNT, cache-aware streaming)
- Works on CPU / Apple Silicon / NVIDIA. Steam Deck = CPU only.
- Clean install script for Steam Deck / Linux was given (uses `uv` + CPU PyTorch + Transformers).
- Live-mic and file-transcription Python snippets provided.

### Iranian Textbook Sites (پایگاه کتاب‌های درسی)
Mirrors (same content):
- http://chap.oerp.ir/
- http://chap.sch.ir/
- http://chap.roshd.ir/

Official body: اداره کل نظارت بر نشر و توزیع مواد آموزشی

**Already scraped & structured:**
- Full lists for **پایه ۱ تا ۶** (ابتدایی) with book codes
- Full lists for **پایه ۷ تا ۹** (متوسطه اول) with book codes
- Partial lists for **پایه ۱۰–۱۲** (by stream)

Book codes are stable (e.g. 101 = آموزش قرآن اول, 112201 = فارسی ۳).

### Ayrik Service Scrapes
- POS parts page 7: https://ayrikservice.com/product-category/pos-parts/page/7/ (84 items total)
- NCR ATM: https://ayrikservice.com/product-category/atm-parts/ncr/ (137 items)
- Hyosung ATM: https://ayrikservice.com/product-category/atm-parts/hyosung-parts/ (20 items)

### Clarification on “SEO articles”
User did **not** want articles *about* SEO/AEO/GEO.  
They wanted **global trending topics** that would perform well as SEO content worldwide (high search volume evergreen + timely subjects).

See `TRENDING_TOPICS_FOR_SEO.md` in this repo.

---

## 3. Open / Next Tasks

1. Finish complete textbook lists for grades 10–12 across all streams.
2. Extract PDF download links where available.
3. Full pagination of Ayrik POS + ATM categories into clean lists.
4. Expand trending topics into short original articles if requested.
5. Optionally create structured JSON/CSV of books and products.

---

## 4. Technical Notes

- Textbook sites can be slow / timeout. Prefer chap.sch.ir.
- Useful paths: `/guide-books`, grade category pages, `/glossary/...`
- Ayrik is WooCommerce – straightforward to paginate.
- Never copy full copyrighted articles; create original summaries/entries only.

---

**Repo URL:** https://github.com/imanbarati/session-handoff-textbooks-asr-scrapes

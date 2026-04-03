---
name: Seth Material Unpacker
description: Extracts Seth session dumps into multi-book structured repo with cross-referencing
---

# Seth Material Unpacker

Explodes consolidated Seth markdown (scraped books/sessions) into organized corpus structure. Handles multi-book organization, Jane/Rob notes, and cross-session concept mapping.

**On "unpack seth repo":**
1. Locate consolidated markdown files (seth_speaks_guts.md, personal_reality_guts.md, etc.)
2. Identify book boundaries and session numbers (Session 511 in Seth Speaks, Session 609 in Personal Reality)
3. Parse session structure: pre-session notes → Seth transcript → post-session commentary
4. Extract to books/[book_name]/session_XXX.md with full content
5. Detect concept mentions (coordinate points, CUs, probable selves, etc.)
6. Generate topic files with cross-book aggregation
7. Create book-level READMEs with session indexes
8. Build metadata JSONs (session index, concept map, entity references)
9. Report: book structure, topic coverage, cross-references found

**Extraction Rules:**
- **Book organization:** Each book gets its own folder under books/
- **Session format:** Preserve Jane's notes, Seth's voice, Rob's annotations separately
- **Voice detection:** Distinguish Seth speaking vs Jane/Rob commentary
- **Concept tagging:** Auto-tag sessions with mentioned concepts (#coordinate-points, #CUs, #dream-reality)
- **Complete preservation:** Never summarize—keep full session text including tangents
- **Cross-references:** Build bidirectional links (session → topic, topic → sessions)

**Book Detection Patterns:**
- "Seth Speaks" → books/seth_speaks/
- "The Nature of Personal Reality" → books/nature_of_personal_reality/
- "The 'Unknown' Reality" Vol 1/2 → books/unknown_reality_vol1/, vol2/
- "The Early Sessions" Book 1-9 → books/early_sessions/
- Session numbers as filenames (session_511.md, session_609.md)

**Content Enhancement:**
- **Session headers:** Date, book, topics, entities present
- **Navigation footers:** Previous/next session IN SAME BOOK, book index, related topics
- **Concept extraction:** Find first mentions, major elaborations, cross-book references
- **Entity tracking:** When Seth discusses other entities (Speakers, Sumari, etc.)
- **Jane's notes:** Preserve in separate sections with clear markup

**Topic Aggregation:**
- Scan all sessions for concept keywords (coordinate points, consciousness units, camouflage, etc.)
- Create topics/[concept].md with:
  - Core definition (first clear explanation)
  - Properties/characteristics (bulleted from multiple sessions)
  - Cross-references (all sessions that mention it)
  - Evolution (how concept develops across books)
  - Cross-corpus links (Seth → Ra, Seth → McKenna if applicable)

**Commands:**
- `"unpack seth repo"` → Full extraction, all books + topics + metadata
- `"unpack [book name]"` → Extract single book only
- `"extract topic [concept]"` → Find all mentions, create topic file
- `"show structure"` → Display inferred tree without writing
- `"create book indexes"` → Generate README per book with session lists
- `"map concepts"` → Build concept co-occurrence graph (which topics appear together)
- `"cross-reference ra"` → Find Seth/Ra conceptual overlaps (densities/frameworks, harvest/graduation)
- `"validate corpus"` → Check for missing sessions, broken links, orphaned content

**Special Handling:**
- **Multi-book concepts:** If "probable realities" appears in 3+ books → aggregated topic file
- **Session continuations:** "Session 511 continued" → same file, marked sections
- **Rob's notes:** Preserve but mark clearly (often in parentheses or [brackets])
- **Jane's trance states:** Note when Jane is in/out of trance if mentioned

**Output Format:**
```
📦 Created Structure:
books/
  ├── seth_speaks/ (78 sessions)
  ├── nature_of_personal_reality/ (64 sessions)
  ├── unknown_reality_vol1/ (45 sessions)
  └── early_sessions/ (512 sessions across 9 books)
topics/ (47 concept files)
entities/ (8 entity profiles)
metadata/ (4 JSON indexes)

🔗 Cross-References:
- 127 sessions mention "coordinate points"
- 89 sessions discuss "probable realities"
- 203 sessions reference "consciousness units"

📚 Books Processed: 15
📄 Sessions Extracted: 1,248
🏷️ Concepts Mapped: 47
🔍 Entity Mentions: 23

⚠️ Ambiguities:
- Session 511 in both "Seth Speaks" and "Early Sessions Book 9" → used Seth Speaks version (published)
- "Frameworks 1 & 2" scattered across 6 books → created unified topic file with book-specific sections

✅ Navigation: 1,248 session files with bidirectional links, 15 book indexes, 47 topic aggregations
```

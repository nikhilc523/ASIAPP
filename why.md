Below is a **Notion-ready, “god-level” plan** for the **CSUEB ASI Mobile App**—built around *real* CSUEB/ASI web content (Minutes/Agendas, Resolutions, Officers/Office Hours, ASI Presents) and your **RAG “Ask ASI”** requirement.

I’m using CSUEB’s official brand typography guidance (Montserrat + Roboto Serif) ([California State University, East Bay][1]), official ASI pages for minutes/agendas, resolutions, ASI Presents, and officers ([California State University, East Bay][2]), plus ASI governance docs (Admin Manual, Office Hours Policy) ([California State University, East Bay][3]) and your signed resolution packet example .

---

# CSUEB ASI Mobile App — Notion Master Plan (V1 → V2)

## 1) Product Definition

### 1.1 One-liner

**ASI Mobile** is the student-facing hub for **ASI governance transparency + services**: upcoming meetings, agenda summaries, official documents, officer directory/office hours, ASI Presents events, and a citation-based **Ask ASI** search assistant.

### 1.2 Core outcomes (measurable)

* Students can **find upcoming meetings in <10 seconds** (Home swipe cards).
* Students can **understand agenda topics in <60 seconds** (auto agenda item summaries + “what it means”).
* Students can **pull the official doc instantly** (agenda/minutes/resolution viewer + share link).
* Students can **find the right ASI person to contact** (directory + RAG routing).
* **Search answers always cite sources** (minutes/agendas/resolutions PDFs/Word docs).

---

## 2) Real Source Inventory (What we’re building on)

### 2.1 “Meetings” content sources (authoritative)

* **ASI Minutes & Agendas** landing page ([California State University, East Bay][2])
* Year pages like **2025–26** (patterned archive structure) ([California State University, East Bay][4])
  **What this implies:** the app can ingest by *year → committee → meeting date → agenda/minutes links*.

### 2.2 “Resolutions” content sources (authoritative)

* **ASI Resolutions archive page** (multi-year list; links open docs) ([California State University, East Bay][5])
  **What this implies:** resolutions can be a first-class searchable library (filter by year/body/type).

### 2.3 “People” content sources (authoritative)

* **Government Officers** page includes names/roles/emails and **office hours schedules** ([California State University, East Bay][6])
* **Office Hours Policy** (effective Aug 2025; minimum office hours by role + where/how hours should be held) ([California State University, East Bay][7])
  **What this implies:** the app can enforce consistent display rules and educate students on how office hours work.

### 2.4 “ASI Presents / Events” (authoritative)

* ASI Presents mission page ([California State University, East Bay][8])
* ASI Presents “Upcoming Events” page ([California State University, East Bay][9])
  **What this implies:** a dedicated events feed module is realistic without inventing content.

### 2.5 Governance structure / responsibilities (authoritative)

* ASI Government overview page (mission & what ASI Gov does) ([California State University, East Bay][10])
* ASI Administrative Manual (committees/roles/policies; governance rules) ([California State University, East Bay][3])
  **What this implies:** we can build a “How ASI works” section + committee explanations from official governance docs.

### 2.6 Your “example resolution” ingestion

* Signed “TA Tuition and Fee Waiver” resolution packet (local PDF) 
  **What this implies:** your RAG can answer “Explain the TA fee waiver resolution” with a real source and citation.

---

## 3) Brand + UX Requirements (CSUEB-aligned)

### 3.1 Typography (must)

* Use **Montserrat** (headers) and **Roboto Serif** (body) per CSUEB brand guidance ([California State University, East Bay][1])

### 3.2 Colors and identity (must)

* Use CSUEB brand identity system and official assets page(s) for lockups/logos ([California State University, East Bay][11])
* If using ASI logo assets, pull from CSUEB-hosted ASI logo PDFs (official) ([California State University, East Bay][12])
* Respect CSUEB trademark/licensing guidance (important for a public app and marketing visuals) ([California State University, East Bay][13])

### 3.3 Accessibility (must)

* Follow CSUEB’s emphasis on contrast-safe pairing guidance (the fonts/colors page references ADA contrast pairing) ([California State University, East Bay][1])
* App requirements:

  * Dynamic type scaling
  * 44px minimum tap targets
  * VoiceOver labels on cards/buttons
  * High-contrast “document reading” mode for agendas/minutes

---

## 4) User Personas + Top Jobs-to-be-Done

### Persona A — “Busy student who wants to be heard”

* Wants: “What meeting matters to my issue? Who do I contact? When can I show up?”
* App solves: Ask ASI → recommended person + next relevant meeting + sources.

### Persona B — “Student org / leader”

* Wants: “Funding process, deadlines, what was decided last time?”
* App solves: Funding tile + resolution/minutes retrieval + shareable official docs.

### Persona C — “New student curious about ASI”

* Wants: “What is ASI? What do they do? What events happen?”
* App solves: ASI tab overview + ASI Presents feed ([California State University, East Bay][8])

### Persona D — “Officer / staff / advisor”

* Wants: “Less repetitive questions; direct students to the correct source”
* App solves: citation-first knowledge base, stable deep links, share buttons.

---

## 5) App Information Architecture (IA)

### Bottom tabs (V1)

1. **Home**
2. **Meetings**
3. **Ask ASI (Search)**
4. **People**
5. **ASI**

### Global utilities (always available)

* Notifications
* Saved items (bookmarks)
* Share link
* “Open in browser” fallback
* Report an issue / incorrect data

---

## 6) Screen-by-Screen Functional Spec (V1)

## 6.1 Home (The “Swipeable Meetings” experience)

**Goal:** students instantly see what’s coming up.

**Components**

* “This Week in ASI” header
* **Swipe cards**: each card = a meeting (committee + time + location + status)
* “Top agenda items” (2–4 bullets) auto-generated from agenda parsing
* Quick actions: All Meetings, Ask ASI, Find My Rep, ASI Presents

**Card data fields**

* committee_name
* meeting_datetime_start/end
* location + zoom link (if present on source)
* agenda_url(s), minutes_url(s)
* status chips: Agenda Posted / Minutes Posted / Vote Likely (heuristic)

---

## 6.2 Meetings (Directory + Meeting Detail)

### 6.2.1 Meetings Directory

* Filters:

  * Committee
  * Date range
  * Agenda posted / Minutes posted
  * Year selector (mirrors ASI archive structure) ([California State University, East Bay][4])
* Committee cards show:

  * purpose (from ASI Admin Manual or Gov page) ([California State University, East Bay][3])
  * next meeting date (if available)
  * follow toggle (subscribe to notifications)

### 6.2.2 Meeting Detail (Most important screen)

**Sections**

1. Header

* Committee name
* Date/time/location
* Add to calendar
* Share

2. “Agenda Summary” (auto)
3. “Agenda Items” (parsed list)

* Each item is a collapsible card:

  * title
  * 1–2 sentence summary
  * tags: action/info/discussion; “vote expected” if motion language detected
  * attachments list (if extracted)

4. “Official Documents”

* Open agenda doc (Word/PDF viewer)
* Open minutes doc (when posted)
* Open in browser fallback

5. Participation guide (simple)

* how to attend / how to comment (if published anywhere; otherwise keep generic)

**Document viewer behavior**

* In-app viewer
* Download/share link
* text selection + “quote with citation” (for RAG transparency)

---

## 6.3 Ask ASI (RAG Search)

### 6.3.1 Ask Screen

* Search bar
* Suggested chips:

  * “What’s on the next BOD agenda?”
  * “Who do I contact about ___?”
  * “Summarize the TA fee waiver resolution”
  * “What happened in [date] meeting?”
* Filters: People / Meetings / Resolutions / Events

### 6.3.2 Answer Screen (must be citation-forward)

* **Answer card** (plain language)
* **Citations** (always visible)

  * links to minutes/agendas/resolutions sources
* **Recommended contact**

  * officer card (from Government Officers page) ([California State University, East Bay][6])
  * office hours + email + “next relevant meeting”

**Non-negotiable rule**

* No answer is “final” unless it includes at least 1 citation (doc link) from:

  * Minutes/Agendas ([California State University, East Bay][2])
  * Resolutions ([California State University, East Bay][5])
  * ASI governance docs ([California State University, East Bay][3])
  * Or a verified local document like your resolution packet 

---

## 6.4 People (Officer Directory + Profiles)

### 6.4.1 People Directory

Source = Government Officers page ([California State University, East Bay][6])

* Categories: Exec / Directors / Senators / At-Large
* Each person:

  * photo (if available; if not, initials)
  * role
  * email
  * office hours summary
  * “Check availability” link if provided

### 6.4.2 Officer Profile

* About / Responsibilities (pulled from Admin Manual where applicable) ([California State University, East Bay][3])
* Office Hours (policy-aligned display) ([California State University, East Bay][7])
* “What I can help with” tags (curated + learned from queries)
* “Recent work”:

  * resolutions sponsored (if you later tag authorship)
  * recent meetings / agenda items referencing them (optional)

---

## 6.5 ASI Tab (Services + Events)

### 6.5.1 ASI Overview

* Mission statement + “what ASI funds/supports” (from ASI homepage) ([California State University, East Bay][14])
* Quick links tiles:

  * ASI Presents ([California State University, East Bay][8])
  * Resolutions ([California State University, East Bay][5])
  * Minutes/Agendas ([California State University, East Bay][2])
  * Government Officers ([California State University, East Bay][6])

### 6.5.2 ASI Presents

* Pull event cards from “Upcoming Events” page ([California State University, East Bay][9])
* Event detail: date/time/location, add-to-calendar, share, accessibility notes.

---

# 7) Data + Content Engineering Plan (the “don’t miss anything” part)

## 7.1 Content types we must support

1. Meeting (committee meeting instance)
2. Agenda document (PDF/Word)
3. Minutes document (PDF/Word)
4. Resolution (PDF/Word)
5. Officer (person profile + office hours)
6. Event (ASI Presents)
7. Governance docs (Admin Manual, policies)

## 7.2 Ingestion strategy (hybrid, realistic)

### Tier 1 — Structured scraping (fast + stable)

* Crawl ASI pages that already have structured lists:

  * Minutes/Agendas landing and year pages ([California State University, East Bay][2])
  * Resolutions archive ([California State University, East Bay][5])
  * Government Officers ([California State University, East Bay][6])
  * ASI Presents events ([California State University, East Bay][9])

### Tier 2 — Document parsing (the “agenda item summaries” feature)

* Download docs (PDF/Word)
* Extract:

  * headings
  * agenda item numbering
  * motions/votes keywords
  * attachments references
* Generate:

  * agenda item summaries
  * “what it means” explanation
  * tags (“Action”, “Discussion”, “Vote likely”)

### Tier 3 — Human curation (small but important)

* Provide an “Admin Console” (even a simple web dashboard) to:

  * correct parsing errors
  * pin “highlight items”
  * set committee descriptions (if docs are vague)
  * add contact routing rules (“Athletics attendance” → Senator at Large + communities committee, etc.)

## 7.3 Update frequency

* Officers/office hours: daily check (office hours can change) ([California State University, East Bay][6])
* Meetings pages: 2–4 times/day during semester peak
* Resolutions: daily/weekly
* ASI Presents: daily ([California State University, East Bay][9])

## 7.4 Source-of-truth and trust ranking

* **Highest trust:** csueastbay.edu PDFs and pages (Minutes/Agendas, Officers, Admin Manual, Policies) ([California State University, East Bay][2])
* **Acceptable:** CSUEB official subdomains hosting docs/logos ([California State University, East Bay][12])
* **Avoid as truth:** mirror domains (.com clones) unless used only as fallback (some exist, but not authoritative).

---

# 8) RAG System Design (Ask ASI done right)

## 8.1 Knowledge base structure

**Chunks should be anchored to citations**, e.g.:

* meeting_id + agenda_item_id
* resolution_id + section headings
* officer_id + office_hours lines

## 8.2 Metadata (critical)

* doc_type: agenda | minutes | resolution | policy | officer | event
* committee_name
* meeting_date
* academic_year
* source_url
* last_verified_timestamp
* extract_confidence score

## 8.3 Answer format rules (non-negotiable)

Every answer must output:

1. **Direct answer** (3–8 lines)
2. **Sources** (clickable; minimum 1)
3. **Recommended next action**

   * “Attend [meeting]”
   * “Email [officer]”
   * “Read [resolution section]”
4. **Confidence**

   * High/Medium/Low + why (e.g., missing minutes, agenda not posted yet)

## 8.4 Examples (your exact use cases)

* “What happened March 12, 2024 BOD?”
  → return meeting minutes/agenda citations + top outcomes
* “Explain TA fee waiver resolution”
  → cite the signed resolution PDF  and summarize sections

---

# 9) Compliance, Risk, and Governance (important for a campus org app)

## 9.1 Brand / trademark usage

* Use official CSUEB brand system & request/approved assets when needed ([California State University, East Bay][15])
* Respect trademark licensing guidance for any public release/marketing ([California State University, East Bay][13])

## 9.2 Data privacy

* The app can be public-read for most content (agendas/minutes/resolutions are public).
* If adding sign-in later:

  * clearly separate “public governance content” vs “personalized student features”
  * store minimal user data (followed committees, bookmarks)

## 9.3 Reliability and “officialness”

* Always show “Open on ASI Website” so students can verify source.
* Add “Last updated” timestamp per meeting/doc.

---

# 10) Analytics (so you can prove value)

Track:

* Home → Meeting Detail click-through
* Agenda doc open rate
* Search queries volume + top intents
* “Recommended contact” click rate (email/office hours)
* Most viewed resolutions and meetings
* Time-to-find (search success metric)

---

# 11) Delivery Plan (Milestones)

## Phase 0 — Proof of concept (1–2 weeks)

* Scrape:

  * Minutes/Agendas index + current year ([California State University, East Bay][2])
  * Resolutions index ([California State University, East Bay][5])
  * Government Officers page ([California State University, East Bay][6])
* Build:

  * Home swipe cards (static from scraped data)
  * Meeting detail with doc viewer links
  * People directory
* Demo: “Find next meeting + open agenda + find officer hours”

## Phase 1 — V1 MVP (4–6 weeks)

* Document parsing for agenda item extraction
* Agenda summary generation
* Search (basic keyword + citations)
* Bookmarks + share
* ASI Presents feed ([California State University, East Bay][9])

## Phase 2 — RAG V1 (4–6 weeks)

* RAG index for:

  * agendas, minutes, resolutions, policies, officers
* Answer screen with citation rules + recommended contacts
* Admin review queue for low-confidence docs

## Phase 3 — V2 “Student impact” features

* Notifications: agenda posted / meeting reminders
* Issue intake form → routed to committee/officer
* Resolution tracker (proposed → passed → implemented)

---

# 12) Notion Implementation (copy this structure into Notion)

**Database 1: Screens**

* Name
* Tab
* Priority (P0/P1/P2)
* Status
* User story
* Acceptance criteria
* Dependencies (data source / parsing / RAG)

**Database 2: Data Sources**

* Source name
* URL
* Type (page/pdf/doc)
* Update frequency
* Parser needed? (Y/N)
* Notes (edge cases)

**Database 3: Content Objects**

* Object type (Meeting/Agenda/Minutes/Resolution/Officer/Event)
* ID
* Source URL
* Parsed fields
* Last verified
* Confidence
* Owner (who fixes parsing)

**Database 4: RAG Prompts + Evaluations**

* Prompt template
* Required citations
* Failure modes
* Test questions (like your examples)
* Quality score rubric

---

## Quick “next step” I’d do immediately

If you want this to be *execution-ready*, the best next deliverable is:

* a **Notion PRD + Acceptance Criteria** for each P0 screen (Home, Meeting Detail, Meetings Directory, People Directory, Ask ASI Answer screen),
* plus a **Data Source Map** listing every URL pattern to ingest (minutes/agendas by year, resolutions, officers, events) based on the official pages we identified ([California State University, East Bay][2]).

If you tell me what stack you’re leaning toward (Flutter vs React Native vs native Android/iOS), I’ll tailor the “implementation notes” sections to match—but the plan above works regardless.

[1]: https://www.csueastbay.edu/universitycommunications/brand/fonts-and-colors.html?utm_source=chatgpt.com "Type Fonts and Colors - California State University, East Bay"
[2]: https://www.csueastbay.edu/asi/asi-government/minutes-and-agendas/index.html?utm_source=chatgpt.com "Minutes and Agendas - California State University, East Bay"
[3]: https://www.csueastbay.edu/asi/files/docs/asi-government/board-documents/administrative-manual-of-asi.pdf?utm_source=chatgpt.com "Administrative-Manual-of-ASI.pdf - California State University, East Bay"
[4]: https://www.csueastbay.edu/asi/asi-government/minutes-and-agendas/2025-26.html?utm_source=chatgpt.com "CSUEB ASI MINUTES AND AGENDA 2025-2026 - csueastbay.edu"
[5]: https://www.csueastbay.edu/asi/asi-government/resolutions.html?utm_source=chatgpt.com "Resolutions - California State University, East Bay"
[6]: https://www.csueastbay.edu/asi/asi-government/government-officers.html?utm_source=chatgpt.com "Government Officers - California State University, East Bay"
[7]: https://www.csueastbay.edu/asi/asi-government/asi-student-government-office-hours-policy.pdf?utm_source=chatgpt.com "ASI Student Government Office Hours Policy - csueastbay.edu"
[8]: https://www.csueastbay.edu/asi/asi-presents/index.html?utm_source=chatgpt.com "ASI Presents - California State University, East Bay"
[9]: https://www.csueastbay.edu/asi/asi-presents/news-and-events.html?utm_source=chatgpt.com "ASI Presents Upcoming Events - California State University, East Bay"
[10]: https://www.csueastbay.edu/asi/asi-government/index.html?utm_source=chatgpt.com "ASI Government - California State University, East Bay"
[11]: https://www.csueastbay.edu/universitycommunications/brand/downloads.html?utm_source=chatgpt.com "Downloads - California State University, East Bay"
[12]: https://www.csueastbay.edu/asi/files/docs/resources/logos/asi-red.pdf?utm_source=chatgpt.com "www.csueastbay.edu"
[13]: https://www.csueastbay.edu/universitycommunications/brand/licensing-guidelines.html?utm_source=chatgpt.com "Licensing Guidelines - California State University, East Bay"
[14]: https://www.csueastbay.edu/asi/?utm_source=chatgpt.com "CSU East Bay ASI - Associated Students, Inc."
[15]: https://www.csueastbay.edu/universitycommunications/brand/index.html?utm_source=chatgpt.com "Cal State East Bay Brand - California State University, East Bay"

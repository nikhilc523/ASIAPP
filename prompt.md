Design a premium iOS-first mobile app called “CSUEB ASI” (Associated Students, Inc.). The app is the official student-facing hub for ASI governance transparency + ASI services.

BRAND + VISUAL STYLE (must follow)
- Typography: Montserrat for headings, Roboto Serif for body text (CSUEB brand guidance).
- Palette: CSUEB red as primary accent, charcoal/near-black text, white backgrounds, neutral grays for dividers and surfaces. Keep colors minimal and official. Maintain high contrast.
- Tone: modern, calm, official, Apple-level clarity; card-based layout; generous whitespace; soft shadows; rounded corners; clean iconography.
- Accessibility: readable sizes, strong hierarchy, large tap targets, clear focus/pressed states.

APP STRUCTURE
Use a bottom tab bar with 5 tabs:
1) Home
2) Meetings
3) Ask ASI (Search)
4) People
5) ASI

GLOBAL RULES
- Every meeting/resolution view must show a “Sources / Official Documents” section with clickable links.
- All AI answers must show citations in a “Sources” block.
- Include “Open in browser” fallback on any document.
- Include empty states (“No meetings this week”, “Minutes not posted yet”) with calm helpful copy.
- Add skeleton loaders for pages that fetch data.

SCREENS TO CREATE (hi-fi)
A) Splash
- ASI logo centered, subtle CSUEB red accent, clean background.

B) Onboarding (2 screens)
1) “Welcome to ASI” + short mission copy + “Continue”
2) Preferences: campus selector + notification toggles for meeting reminders + “Finish”

C) Home (Upcoming Meetings)
- Header “This Week in ASI”
- Horizontal swipeable carousel of “Meeting Cards” showing:
  committee name, date/time, location or Zoom badge, status chips (Agenda Posted / Minutes Posted), and 2–3 “Top agenda item” bullets.
- Below: Quick Actions row (All Meetings, Ask ASI, Find My Rep, Funding & Forms)
- Below: “Recent Highlights” list (last 3 resolutions or major motions)

D) Meetings Directory
- Search bar + filters (committee, date range, agenda posted, minutes posted)
- Year selector (2025–26, 2024–25, etc.)
- List of upcoming meetings and archive entries as clean cards.

E) Meeting Details (most important)
- Hero header with committee name, date/time, location/Zoom, Add to Calendar, Share.
- Section: “Agenda Summary” bullets.
- Section: “Agenda Items” as collapsible cards:
  item title, 1–2 sentence plain-English explanation, tags (Action / Discussion / Info), “Vote expected” badge if relevant, attachments row.
- Section: “Official Documents” with buttons: View Agenda, View Minutes (if available), Open in Browser.
- Section: “Participation” short guidance.

F) Agenda Item Detail
- Full plain-English explanation + key points
- References/attachments list
- Link back to meeting + official doc citation

G) Ask ASI (Search Home)
- Search bar with placeholder: “Ask anything about ASI…”
- Suggested query chips:
  “Who do I contact about ___?”
  “Summarize the next BOD agenda”
  “Explain the TA fee waiver resolution”
  “What happened in the March 12, 2024 BOD meeting?”
- Filter toggles: People / Meetings / Resolutions / Events / Policies

H) Ask ASI Results
- AI Answer card (short, clear)
- “Sources” block with 2–5 clickable citations (meeting docs/resolutions/policies)
- “Recommended Contact” card (officer headshot, role, office hours, email CTA)
- “Recommended Next Step” row (Attend next meeting / Email officer / Read doc)

I) People Directory
- Segmented control tabs: Board of Directors / Senators / Committees / Staff
- Person list rows: headshot, name, role, office hours badge, email icon.

J) Officer Profile
- Hero: photo, name, role, email
- Sections: About, Office Hours (schedule), Responsibilities (“What I can help with”), Work (resolutions sponsored / key updates)
- CTA buttons: Email, Share profile, Ask ASI about this role.

K) ASI Tab Home
- Grid tiles: ASI Presents, Funding & Forms, Resolutions, Minutes & Agendas, Government Officers, About ASI, Policies.

L) ASI Presents (Events Feed)
- Featured event hero
- Upcoming events list cards with date/time/location, add-to-calendar, share.

M) Funding & Forms
- Wizard-like layout:
  Step 1 eligibility
  Step 2 funding type
  Step 3 deadlines
  Step 4 submission links
- FAQs accordion.

COMPONENTS TO DESIGN (include as a UI kit page)
- Meeting Card (compact + expanded)
- Agenda Item Card (collapsed/expanded)
- Source/Citation block component
- Officer card (small + large)
- Status chips (Agenda posted, Minutes posted, Vote expected)
- Quick action buttons
- Empty states + skeleton loaders
- Document viewer header (title, download/share/open browser)

DELIVERABLE
Produce high-fidelity mockups for all screens + a small style guide page with tokens (type scale, spacing scale, corner radius, shadow, primary/secondary buttons, chips, card styles).
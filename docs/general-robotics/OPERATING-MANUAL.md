# General Robotics Operating Manual

Companion to `PROJECT-INSTRUCTIONS.md`. This is the day-to-day: what is
connected, the four routines, and the prompts to trigger them.

---

## 1. Connection map (tested 7 September 2026)

| Tool | Status | What it holds for General Robotics |
|---|---|---|
| Gmail | Live | Cédric (`cedric@general-robotics.com`), Sophie (`admin@general-robotics.com`), GTM renewal thread Aug to Dec 2026, invoice INV-2026-08-GR005, LinkedIn page alerts |
| Notion | Live | 🤖 General Robotics page, `Weekly Cedric` database, `🤝 Robotics Summit — Contacts May 2026` (19 contacts), Competitors, IP / Patent, Production/Produit/Indus |
| Google Drive | Live | `/General Robotics` folder: investor deck 2026 (PDF and PPTX), Presentation v9, GTM proposal, actuator target map, robotics_companies_v2_2.xlsx, subfolders `exec summary`, `Prospection/Leads`, `Investor Decks and material`, `Linkedin - Strat&posts` |
| Google Calendar | Live (owner) | Meetings and reminders |
| Granola | Live | Transcripts including `Borgwarner - General Robotics` (26 Aug), `Robotics and AI perception` (4 Sep) |
| FullEnrich | Live, 1371 credits | Contact enrichment: verified emails and phones |
| HubSpot | Connected, empty | Portal 245320761 under `remi@aiworld.eu`. Onboarding not started |

### Two things to fix before they cost you

1. **Your calendar timezone is set to Europe/Paris while you work Eastern Time.**
   Every time suggestion Claude makes will be six hours off until you change it
   in Google Calendar settings.
2. **HubSpot is empty and sits under a different identity (`remi@aiworld.eu`).**
   Right now Notion is your real CRM. Decide deliberately: either commit to
   HubSpot and migrate the 19 summit contacts into it, or keep Notion and stop
   treating HubSpot as pipeline. Running both half-way is how contacts get lost.

---

## 2. The four routines

### Routine A: Morning scan (10 minutes)

> **Prompt:** `GR morning scan`

Claude does:
1. Reads Gmail for anything from General Robotics addresses or robotics
   prospects since yesterday.
2. Reads today and tomorrow on the calendar.
3. Checks Granola for a transcript from yesterday with no follow-up sent yet.
4. Returns: what needs a reply today, what needs prep, what is slipping.

Output is a maximum of six lines. No summary of newsletters.

### Routine B: Meeting follow-up (5 minutes, same day)

> **Prompt:** `Follow up on [meeting name]`

Claude does:
1. Pulls the Granola transcript.
2. Extracts what was actually committed, by whom, by when.
3. Drafts the follow-up email in GR voice as a Gmail draft.
4. Proposes the Notion update: contact category, next step, date.

Rule: the email quotes something specific from the conversation. A follow-up
that could have been written before the meeting is a wasted follow-up.

### Routine C: Prospect qualification (15 minutes)

> **Prompt:** `Qualify [company] for RS series`

Claude does:
1. Checks whether they are already in the Notion contact list or the Drive
   target map.
2. Researches: what they are building, what joints and torque range it needs,
   who they buy actuators from today, funding stage.
3. Scores the fit against the RS series and says plainly if it is a no.
4. If yes: names the right person to reach, drafts the opening email.
5. Offers to enrich the contact via FullEnrich before you spend a credit.

The scoring question that matters: does their robot need 15 to 30 kg of
manipulation capacity at a joint where size and weight are constrained? If not,
they are not a buyer yet.

### Routine D: Weekly Cédric prep (20 minutes, before your weekly)

> **Prompt:** `Prep Weekly Cedric`

Claude does:
1. Reads the last entry in the Notion `Weekly Cedric` database.
2. Lists what you committed to last week and whether it happened.
3. Pulls US pipeline movement since then from Gmail and Granola.
4. Drafts this week's agenda: three decisions Cédric needs to make, not a
   status report.
5. After the call, writes the new Weekly Cedric entry back into Notion.

---

## 3. Fundraising support prompts

| Ask | Prompt |
|---|---|
| Refresh the investor list | `Build the US investor target list for the pre-series, ranked by robotics hardware thesis fit` |
| Prep Cédric for an investor call | `Prep Cedric for [investor]: their thesis, their robotics portfolio, the three questions they will ask, our weak answer` |
| Stress-test the deck | `Read GR_Investor_Deck_2026 in Drive and tell me the three slides an investor will push back on` |
| Data room gap check | `What is missing from the Investor Decks and material folder that a pre-series investor will ask for` |
| Traction narrative | `Turn the Mass Robotics test plan and the Borgwarner conversation into two paragraphs of traction proof` |

The honest state of the raise, from your own Notion: investors are waiting on
validated actuator performance before they commit. That makes the Mass Robotics
test plan the single highest-leverage item you own. Every fundraising
conversation is downstream of it.

---

## 4. GTM prompts

| Ask | Prompt |
|---|---|
| Work the summit list | `Who from the Robotics Summit contact list has no next step, and what should it be` |
| Write outreach | `Draft an RS90 opening email to [name] at [company]` |
| LinkedIn post | `Draft a GR LinkedIn post on [topic], 150 to 250 words` |
| Competitor check | `What changed at [Harmonic Drive / Unitree / Robstride / Cubemars] this month and does it affect our pitch` |
| Partner mapping | `Map the tier-2 actuator buyers and integrators in the US we have not contacted` |

### Your live pipeline segments (from the summit list)

- **Buyers:** Collin Barack (HEBI Robotics, wants reducers), Chris Norman
  (ENJVARE, Cubemars buyer), David Holmes.
- **Partners:** Gonzalo Buelta O'Donnell (Synapticon, CGO), Drew Hickcox
  (Odic Inc), Ronald Valenzuela (KHK USA, gears), James Fox (Spring PD,
  thermo-mechanical testing).
- **Investors:** Scott Walter (Robostrategy), Claudio Jordan (ABB),
  Stuart Matsumoto (Redpoint), Frank Perrou.
- **Competition:** Harmonic Drive (Allison Morlock, Susan Zheng).

Most of these have an empty Next Steps column. That is the first hour of work.

---

## 5. Rules Claude will not break

1. No email leaves without you seeing the draft.
2. No number goes in a deck or an email without a named source.
3. No em dash, ever. No banned words from the brand book.
4. Notion is the source of truth for pipeline until you say otherwise.
5. FullEnrich credits are spent only on your explicit go.
6. Anything touching the contract or the invoice goes through Sophie and gets
   flagged to you before it is drafted.

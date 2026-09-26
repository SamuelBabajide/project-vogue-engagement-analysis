# project-vogue-engagement-analysis
Interactive Power BI report analysing participation, retention and satisfaction across 16 Yoruba cultural heritage sessions.

# Project Vogue — Engagement Across Cultural Heritage Events

An interactive Power BI report analysing participation, retention and satisfaction across 16 Yoruba cultural heritage sessions delivered by MYEC between October 2024 and April 2025.

**Tools:** Microsoft Power BI (data model, DAX measures, cross-filtering, drill-through) · Excel (data preparation)  
**Role:** Data Analyst

**Deliverables:** [Presentation](https://docs.google.com/presentation/d/1tl-TPSjMVn28lOxle57ZVBwVHxOHzICa/edit?usp=drive_link&ouid=114818397241570940294&rtpof=true&sd=true)

Project Vogue Dashboard — Summary Page
<img width="1300" height="650" alt="image" src="https://github.com/user-attachments/assets/48a06ad5-3674-4ce9-af59-9cba22f9279b" />

---

## Contents

- [Programme context](#programme-context)
- [Dataset](#dataset)
- [Data cleaning and preprocessing](#data-cleaning-and-preprocessing)
- [Data quality findings](#data-quality-findings)
- [Key findings](#key-findings)
- [Report interactivity](#report-interactivity)
- [Recommendations](#recommendations)
- [Measure design notes](#measure-design-notes)

---

## Programme context

Project Vogue delivers Yoruba cultural heritage sessions across three programme events. Every attendee completes a short exit survey covering what they learned, what they would improve, and how likely they are to recommend the programme.

| Events | Sessions | Attendances | Focus |
|---|---|---|---|
| Storytelling | 8 | 300 | Folktales, proverbs, Aroko symbolic messaging, Yoruba greetings |
| Rehearsal | 7 | 250 | Performance preparation, costume, camera work, cultural practice |
| Oral History | 1 | 10 | Recorded testimony and heritage transmission |

Heritage programmes are usually evaluated on headcount alone. Because Project Vogue records the same participants across repeated sessions, this dataset can measure something more useful than reach: whether people came back.

---

## Dataset

| Attribute | Detail |
|---|---|
| Survey responses | 517 (analysis extract) |
| Fields | 13 |
| Period | October 2024 – April 2025 |
| Missing values | None |

Fields cover participant identity, gender, self-described audience type, programme event, attendance date, referral score, and two free-text responses that were categorised into standard themes.

---

## Data cleaning and preprocessing

**1. Name correction** — Incomplete and misspelt participant names reconciled to a single canonical form so unique participants could be counted reliably.

**2. Gender standardisation** — Misspelt and inconsistent gender values normalised to Male and Female.

**3. Programme standardisation** — Programme names aligned to three strands and mapped to short codes (ST, RE, OH).

**4. Date formatting** — Attendance dates converted to DD/MM/YYYY and session years verified against the delivery calendar.

**5. Response standardisation** — Free-text learning and feedback responses grouped into consistent themes for aggregation.

**6. Validation** — Programme totals reconciled against the participation headline and referral scores confirmed within the 0–10 range.

---

## Data quality findings

Two issues surfaced during preparation. Both would have produced plausible-looking but wrong results if left uncorrected.

### Identity fragmentation

**169 distinct name strings resolved to 66 real people.** Participants wrote their names differently at each session — misspellings, partial surnames, inconsistent spacing. 177 of 517 rows required correction.

Taken at face value, the register would have reported roughly **2.6 times more unique participants** than the programme actually reached, and every retention measure would have collapsed. This single step changed the analysis more than any other.

### Session year recorded incorrectly

**Eight of fifteen sessions carried a 2024 year stamp for dates falling in 2025** — the two January Storytelling sessions and all six Rehearsal sessions from March and April.

The delivery sequence makes the error clear: Storytelling ran October to December 2024 and continued into January 2025 before Rehearsal began that March. Left uncorrected, the programme would appear to have run Rehearsal six months before Storytelling began.

---

## Key findings

### Retention, not reach, is what this data measures

**560 attendances came from just 66 people** — roughly 8.5 visits each.

| Sessions attended | Participants |
|---|---|
| 10 or more | 33 |
| 5 to 9 | 10 |
| 2 to 4 | 6 |
| 1 only | 17 |

Half the cohort attended ten or more sessions across seven months; eight attended fourteen or fifteen of the sixteen delivered. This is not a programme that reached a large audience once — it reached a small audience repeatedly.

**The clearest improvement opportunity:** 17 participants appear exactly once and never returned.

### Satisfaction is strong but selectively sampled

Across 517 responses on a 0–10 scale, **the lowest score recorded was 8**. There are no detractors in the dataset at all.

| Strand | Referral rating |
|---|---|
| Oral History | 9.80 |
| Rehearsal | 9.45 |
| Storytelling | 9.43 |
| **Overall (weighted)** | **9.45** |

Worth reading honestly: exit surveys collected in the room from an audience largely made up of returning regulars will skew positive. The people most likely to give a low score are the seventeen who never came back, and most answered once at most.

### What participants remember

| Learning theme | Mentions |
|---|---|
| Traditional outfit styles and their meanings | 116 |
| History and lessons of proverbs | 78 |
| How Aroko conveys messages | 66 |
| Greetings for different occasions | 62 |
| Yoruba folktales and proverbs | 61 |

Material culture leads. Tangible, visual heritage lands more memorably than oral heritage, though language-based content still accounts for 206 mentions combined.

### What participants ask for

| Improvement theme | Mentions |
|---|---|
| Next rehearsal | 128 |
| New friends | 109 |
| More of the delicious meals | 94 |
| More of the beautiful costumes | 49 |
| Next workshop | 47 |

The top requests are not complaints — asked what could be improved, the largest body of feedback is a request for more of the same.

Two things stand out. **Food** appears in 109 mentions across meals and appetizers, ranking above costume. And **109 people cited making new friends**, meaning peer connection is doing as much work as the cultural content for a programme aimed at young people.

### Demographics

- **93%** of attendances are young people (479 of 517); volunteers account for 36 and trustees 2
- Gender splits roughly 55% male in every strand, holding regardless of programme content

---

## Report interactivity

The report uses two interaction mechanisms that compound: cross-filtering within a page, and drill-through between pages.

### The baseline state

Every session opens here — 560 attendances, 66 participants, 9.45 rating, 16 sessions. All nine visuals are live, and clicking any element cross-filters the rest.

Summary page, unfiltered
<img width="1300" height="650" alt="image" src="https://github.com/user-attachments/assets/48a06ad5-3674-4ce9-af59-9cba22f9279b" />

### Cross-filtering: one click, nine visuals

Selecting a slice of the event donut filters the KPI cards, session bars, learnings table and word cloud simultaneously. The filter tag beside the title is the report's own confirmation the interaction is active.

**Rehearsal selected** — participation falls from 560 to 250, unique participants from 66 to 50, and Storytelling sessions drop to 0.

Summary page cross-filtered to Rehearsal
<img width="1300" height="650" alt="image" src="https://github.com/user-attachments/assets/738093de-b17f-42ae-9939-39e3ae907a48" />

**Storytelling selected** — 300 attendances, 55 participants, and the learnings table rescopes so "Traditional outfit styles" (77 mentions) is now Storytelling-only.

Summary page cross-filtered to Storytelling
<img width="1300" height="650" alt="image" src="https://github.com/user-attachments/assets/d8ce3012-3432-401e-ac75-10944244b896" />

**Oral History selected** — at 10 attendances the word cloud stops being a cloud. With only three comments remaining, each is fully readable. Filtering here changes what the visual is useful for, not just its scale.

Summary page cross-filtered to Oral History
<img width="1300" height="650" alt="image" src="https://github.com/user-attachments/assets/6d95ec23-d4db-4bde-b119-66d005f2d8f2" />

### Drill-through: strand pages, filtered further

The left-hand navigation moves to a dedicated page per strand. Those pages can then be cross-filtered again, stacking the two mechanisms.

**Rehearsal — isolating a single recommendation.** Clicking the "Next rehearsal" bar shows that 119 of 250 attendances (47.6%) requested it, across 39 unique participants.
<img width="1262" height="545" alt="image" src="https://github.com/user-attachments/assets/defc9779-47a9-4ff8-8dbe-e6de0ada7caf" />

**Storytelling — isolating the final two sessions.** The clearest read in the report: filtering to the last two sessions drops "Next workshop" from 56 mentions to **zero**. Once the strand's final session had passed, nobody asked for another one.
<img width="1255" height="535" alt="image" src="https://github.com/user-attachments/assets/6715d8bb-703d-4a07-89f7-77d75042f1db" />

**Oral History — a perfect score emerges.** Every participant who asked for more costumes or villain stories gave a 10.00 referral score; the four who asked for more hero stories are the only reason the strand average sits at 9.80. With six people, this is suggestive rather than conclusive — a thread worth following up, not a settled finding.
<img width="1256" height="536" alt="image" src="https://github.com/user-attachments/assets/e71742ba-f533-4131-8d1f-6480139763f1" />

---

## Recommendations

**1. Follow up the single-visit group.** 17 participants attended exactly once. Their absence from the feedback pool is precisely why the 9.45 rating should carry a caveat, and this is the highest-value unanswered question in the dataset.

**2. Scale Oral History deliberately.** One session and 10 attendees is a pilot, not a strand. Its 9.80 rating is encouraging but rests on a very small base; schedule three to four further sessions before drawing conclusions about demand.

**3. Treat catering as programme design.** Food draws 109 mentions, ranking above costume among improvement requests. Protect the catering budget rather than treating it as a discretionary extra.

**4. Report reach and contact separately.** Publish 66 participants and 560 attendances as two distinct measures with their definitions attached. A funder asking "how many people did you reach" should be told 66; one asking "how much cultural contact did you deliver" should be told 560.

---

## Measure design notes

**The overall referral rating is participation-weighted**, not an average of the three strand averages. Averaging 9.45, 9.43 and 9.80 unweighted returns 9.56 — a different and misleading figure, since Oral History's 10 attendances would carry the same weight as Storytelling's 300.

**Unique Participants and Total Participation are deliberately distinct measures.** The same person attending multiple sessions counts once in the former and multiple times in the latter. Collapsing them is the most common way this kind of report goes wrong.

**Colour identity is fixed per strand** across all four pages — Storytelling gold (`#C9A227`), Rehearsal green (`#6FA287`), Oral History blue (`#7FB2D9`) — so a colour never means two different things.

---

## Author

**Samuel Babajide** — Data Scientist specialising in applied analytics and predictive modelling within complex, regulated environments.

[Website](https://samuelbabajide.github.io/) · [LinkedIn](https://linkedin.com/in/samuelbbabajide) 

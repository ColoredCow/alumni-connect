# Yearbook — Data Collection Reference

> What data points matter for an alumni record, using the IIT Delhi Yearbook as a reference. Feeds directly into the **data-collection module** (V1). Field list is current thinking, not locked — the team decides what actually goes in. See [architecture.md](architecture.md) for where this fits and [research.md](research.md) for the data-source questions.

## Reference — IIT Delhi Yearbook (ColoredCow)

ColoredCow built a data-collection tool for IIT Delhi ~8–9 years ago. The purpose: collect alumni data and publish it as a physical coffee-table booklet — one dedicated page per alumni — distributed at the 25-year reunion of each passing batch.

Each alumni page contained the fields below, grouped by how confident we are about them.

### Confirmed (from the discussion + the sample page)

- **Photo** — a recent photo of the alumni
- **Name**
- **Batch year** — year of passing out
- **Branch / department** — which engineering department
- **Hostel / residence** — where they lived during college
- **Current city**
- **Life after college** — what they've been doing since graduating
- **Favorite memories** — a short personal note (authored by the alumni)
- **Life lessons** — something they'd tell their younger self (authored by the alumni)
- **Old photos** — scanned memories from college days
- **New photos** — recent life photos
- **Character sketch** — a short blurb *about* the person (on the sample page: "He-man, hyper-enthu… started off shy…"). Note: this was written **by peers**, not the alumni themselves — so it's a different collection workflow from the self-authored fields above. **TODO:** decide who authors this.

## Extended Fields — IIT Delhi Yearbook

- **Current role and company**
- **College stories** — personal memories from their time at college
- **Family** — family details
- **Email**
- **Contact number**
- **College nickname** — what they were famously called in college or friend circle

## Design note — keep it generic

KEC is our **first deployment, not the definition** (layer 2). So:

- Fields like **Branch/department** and **Hostel/residence** are generic fields; the *actual values* (KEC's departments, KEC's hostel names) are **config/data**, not hardcoded into the schema.
- A field that only makes sense for one college doesn't belong here. If KEC needs something specific, it should still be expressible as config on a generic field.

This keeps the same data model working when we move to other Uttarakhand colleges and beyond.

## Privacy note

Some of these fields are **sensitive** — contact number, email, family details, exact location. They should not be public by default; gate them behind connection/consent or admin-only visibility. **TODO:** confirm per-field visibility with V1 scope.

Also: any reference material from the real Yearbook (the sample page has a real name, phone, email, and family details) must be **redacted or replaced with synthetic data** before it goes into the repo or any demo. Don't commit real PII.

## What this means for KEC

The IIT Delhi reference gives us a proven starting point for what's worth collecting. Not every field applies directly — KEC's context differs — but this is the baseline to work from.

## Open questions

- Which of the above fields make sense for our alumni?
- Are there fields to add beyond the reference list? (kept generic, expressed as config where college-specific)
- Which fields are **mandatory vs. optional** during data collection?
- Who authors the **character sketch** — peers, or the alumni themselves?
- Do we want a **physical booklet output** like IIT Delhi, or just a digital directory? (maps to the Yearbook / Book Export module marked "later" in [architecture.md](architecture.md))

> **TODO:** team to review and decide which fields go into the alumni profile. This decision feeds directly into the data model in [architecture.md](architecture.md).

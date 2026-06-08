# The IIT Delhi Yearbook (ColoredCow)

The story of the alumni booklet ColoredCow built for IIT Delhi ~8–9 years ago.

---

## What it was

IIT Delhi publishes a physical booklet for each batch completing 25 years since graduation. It's a thick, coffee-table-style hardcover book, distributed at the reunion and around the college. Every alumnus in the batch gets a dedicated page (sometimes two): a photo, what they're doing 25 years on, college stories, which branch and hostel they were from, family, and so on.

The point was twofold — nostalgia (a batch sees who ended up where) and keeping the alumni network alive.

## How ColoredCow got involved

ColoredCow was originally brought in just to design the book — page layout, how the information would be arranged, how photos would sit on the page.

But while scoping the design, the team saw the real problem was upstream. Producing the book meant collecting data on a huge number of people: a single batch spans many branches, so a year's book could mean chasing data for 1,000+ alumni. That data was being wrangled in spreadsheets, and it was painful — entries arrived in pieces (a name now, the photo and write-up weeks later), and finding or updating a half-complete record in a spreadsheet was a mess.

So ColoredCow's designer proposed a tech solution for the basic problem underneath the design job: a tool to collect and manage the data.

## What they built — "Yearbook"

A deliberately minimal app, named Yearbook, focused on data collection and management — not a social network, not a public portal.

What it did:

- **Create an alumni record** — name, branch, hostel, city, photos, plus free-text write-ups (life after IIT, favorite memories, life lessons, etc.)
- **Two data-entry paths** — a web form and a mobile app. Staff visiting alumni in person could enter details or grab photos straight from their phone (or off WhatsApp); the web flow handled the rest.
- **Search and filtering** — find a record fast among hundreds, and filter by hostel, branch, etc. (the book itself was organized hostel-wise, so filters mirrored that).
- **Handle partial data gracefully** — because data came in chunks, the tool made it easy to find and update an existing record rather than hunting through a spreadsheet.

It was admin-managed — only the small team working on the booklet had access and did the data entry. It wasn't opened up to alumni as a self-serve platform.

## How it was reused year after year

The tool became a one-time investment that paid off repeatedly. Each year the workflow was:

1. Back up the current batch's data.
2. Clean it up.
3. Start fresh data collection for the next batch hitting their 25-year mark.

So the same tool served a new batch reaching their 25-year mark every year.

## Scope: what it did and didn't do

- It **did** solve data collection, management, filtering, and categorization — and provided good-quality photos for the designers to pull from.
- It **did not** auto-generate the booklet. Because of budget and time constraints at the time, the team didn't go deep into integrating data collection with automated page layout. The book was still designed manually by ColoredCow from the collected data — the tool just made sure the data was clean, complete, and easy to pull.

## Status today

- **Archived.** It ran in production for several years, then was retired.
- It was built ~8–9 years ago — a pre-AI piece of software, with no AI in it.

## Reference Page from the IIT-Delhi Booklet

A filled sample page from the booklet:

![Filled sample page from the IIT Delhi Yearbook](yearbook-page-sample.png)

The blank page-layout template behind it:

![Blank page-layout template](yearbook-page-layout.png)

# Research

> Open questions, things to investigate, references to explore. Questions stay framed **as questions** until they're actually answered — don't write answers in here that haven't been verified.
>
> Owners of this thread: see [TEAM.md](../TEAM.md) (Requirement / research).

## Open Questions

> One status per item: **Open** → **Investigating** → **Answered** (with a link or note).

### Data — the questions that shape V1

1. Where will the alumni data come from — what sources actually exist today? — **Open**
2. Does the college already hold student/alumni data in an ERP or any existing system? — **Open**
3. If an existing system holds the data, is integration with it possible — technically and politically? — **Open**
4. Who uploads the data, and how — alumni self-serve, a student team doing data entry, the college/TPO handing over records? — **Open**
5. Will the college share data, or will users upload it themselves? Is uploading actually easy for them? — **Open**
6. What alumni data does the TPO already have, and will they share it? — **Open**

### Product & reference

7. What's reusable from the IIT Delhi Yearbook tool — both the code and the booklet process? — **Open**
8. How do IITs manage their alumni networks? (IIT Delhi as reference) — **Open**
9. What existing alumni portal products are out there? (Pros/cons vs building our own) — **Open**
10. What does a "college-agnostic" data model look like? (for scaling beyond KEC) — **Open**

### Technical (feeds the stack decision)

11. Authentication options — Google SSO, college email login? — **Open**
12. Mobile-first vs web-first for alumni data entry? — **Open**

## Inputs

- Initial thinking, ideas, and early requirement docs are kept in [artifacts/](../artifacts/) — raw material for the questions above.

## Reference Projects

### IIT Delhi Yearbook Tool (ColoredCow)

- Built ~8–9 years ago for IIT Delhi's 25-year alumni booklet
- Features: profile creation, photo upload, search, hostel/branch filters, mobile + web data entry
- Purpose: data collection and management for printing physical alumni booklets
- Status: archived, codebase available for reference and reuse as a starting point
- Lesson: start with data collection, everything else comes after

## Market Context

- Alumni networking is largely unsolved for tier 2/3 colleges
- KEC founded 1992 — 30+ years of alumni across many domains
- Opportunity to expand beyond KEC → other Uttarakhand colleges → other institutions

## AI Integration Ideas (early thoughts, not commitments)

- AI-assisted profile completion (suggest what to fill based on partial data)
- Smart matching between students and relevant alumni mentors
- Auto-categorization of alumni by domain/role from LinkedIn-style data

## Use Cases — Why a Portal Over the Status Quo

These are the value propositions we expect a portal to deliver for each group, set against today's status quo of scattered Google Forms and WhatsApp groups. They are working hypotheses to validate against the open questions above — not yet verified findings.

### For the college

A college needs an alumni portal to manage all alumni-related activities in a more organized and efficient way. It replaces scattered tools like Google Forms and WhatsApp groups with a single secure system. The points below explain how an alumni portal is better than WhatsApp groups in key areas like data management, fundraising, events, volunteer coordination, and measuring engagement.

#### Data Management and Insights

- **Alumni Portal:** Allows the college to securely collect, store, and analyze alumni data in a centralized manner, eliminating the need for multiple Google Forms and ensuring data consistency. Provides valuable insights for targeted engagement strategies and enables authorized administrators, such as the Director or Dean, to easily access and manage alumni data in one secure location.
- **WhatsApp Group:** Offers limited data management capabilities, making it difficult for the college to track alumni information, preferences, and engagement levels. Relies on scattered Google Forms, leading to data fragmentation and manual consolidation efforts.

#### Fundraising and Donor Management

- **Alumni Portal:** Can integrate secure online donation forms, track donor history, and streamline fundraising campaigns, making it easier for alumni to support the college. Allows for granular access controls to ensure sensitive donor data is only accessible to authorized personnel.
- **WhatsApp Group:** Provides no structured way for the college to solicit donations, manage donor relationships, or track giving history. Lacks centralized data management, hindering effective fundraising strategies.

#### Event Planning and Management

- **Alumni Portal:** Enables the college to create event pages, manage registrations, and communicate event details to alumni, all in one place. Facilitates data-driven event planning and follow-up based on centralized alumni data.
- **WhatsApp Group:** Can be used to share event information, but lacks the tools for formal event registration, ticketing, or attendee management. Decentralized data makes it challenging to plan and assess events effectively.

#### Volunteer Coordination

- **Alumni Portal:** Allows the college to recruit, manage, and recognize alumni volunteers for various initiatives, from mentoring to event support. Provides a centralized platform for tracking volunteer participation and engagement.
- **WhatsApp Group:** Makes it challenging for the college to formally coordinate volunteer opportunities or track alumni involvement due to lack of centralized data management.

#### Measuring Alumni Engagement and ROI

- **Alumni Portal:** Provides the college with metrics and analytics based on centralized alumni data, allowing them to track engagement, measure the impact of alumni programs, and demonstrate the ROI of alumni relations efforts.
- **WhatsApp Group:** Offers limited data and insights, making it difficult for the college to assess the effectiveness of its alumni engagement initiatives. Decentralized data hinders comprehensive reporting and analysis.

### For alumni

Alumni need a portal because a casual WhatsApp group cannot help them stay connected, grow their network, or give back in an organized way. A portal gives every alumnus one official place to find old friends, help students, support the college, and see what others from their college are doing. The points below explain how a portal is better than a WhatsApp group for the alumni themselves.

#### Finding and Connecting With Each Other

- **Alumni Portal:** Lets an alumnus search and find other alumni by batch, city, company, or field, so it is easy to reconnect with old friends and meet useful contacts. Profiles can be updated in one place, so the information stays far more current than a casual group.
- **WhatsApp Group:** Has no way to search people. You can only see whoever is in the group, and there is no easy way to find a specific person by city, job, or batch.

#### Jobs, Internships and Hiring

- **Alumni Portal:** Lets alumni post job openings, internships, and part time work in one clear place where the right students and juniors can see them. Alumni can also use it to hire trusted juniors from their own college for their company.
- **WhatsApp Group:** A job message gets lost in normal chat within minutes. There is no proper place to post openings or for students to find them later.

#### Mentoring and Helping Students

- **Alumni Portal:** Gives alumni a simple way to mentor students, share guidance, and support the next batch in a structured manner. The college can match the right alumnus with the right student.
- **WhatsApp Group:** Makes real mentoring hard because chats are casual and mixed. There is no proper way to connect one alumnus with one student.

#### Donations and Giving Back

- **Alumni Portal:** Lets alumni donate safely through one official college account, with a clear record and proof of where the money went. They can trust that the money is going to the right place.
- **WhatsApp Group:** Money is collected through random forms and personal QR codes. The alumnus is never sure who they are paying or whether it is official.

#### Events and Reunions

- **Alumni Portal:** Shows all upcoming events and reunions in one place, with proper registration so alumni know what is happening and can easily join. They never miss an event because of a lost message.
- **WhatsApp Group:** Event details get buried under other messages, and there is no proper way to register or confirm who is coming.

#### Seeing What Other Alumni Are Doing

- **Alumni Portal:** Lets alumni see the journeys of others from their college, where they are working, what they have achieved, and how they are contributing. This builds pride, motivation, and a sense of community.
- **WhatsApp Group:** Shows only random updates from whoever chooses to post. There is no clear picture of how the wider alumni community is doing.

### For students

Students need a portal because their future depends a lot on guidance and opportunities, and a casual WhatsApp group cannot give them this in a reliable way. A portal gives every student one place to reach seniors and alumni, find jobs and internships, learn from real career journeys, and join college events without confusion. The points below explain how a portal is better than a WhatsApp group for the students themselves.

#### Jobs, Internships and Career Help

- **Alumni Portal:** Lets students see jobs, internships, and part time work posted directly by alumni, in one clear place they can check anytime. They can also reach alumni in the company or field they want to join.
- **WhatsApp Group:** A useful opportunity gets lost in chat within minutes, and there is no way to search old messages or find openings later.

#### Guidance and Mentorship From Seniors

- **Alumni Portal:** Gives students a proper way to ask seniors and alumni for advice on careers, studies, and skills, and to get matched with a mentor. The help is organized instead of random.
- **WhatsApp Group:** Asking for guidance in a busy group is awkward and usually ignored. There is no way to connect with the right senior for your specific need.

#### Finding the Right Person to Ask

- **Alumni Portal:** Lets students search alumni by company, field, or city, so they can find exactly the right person to learn from or ask for a referral. The right contact is easy to reach.
- **WhatsApp Group:** You can only talk to whoever is in the group, and there is no way to find a specific alumnus working in the area you care about.

#### Learning From Real Career Journeys

- **Alumni Portal:** Shows students where alumni are working and how they reached there, which gives them real role models and a clear idea of what is possible. This builds motivation and direction.
- **WhatsApp Group:** Shows only random posts from a few people, with no clear picture of different career paths.

#### Events, Talks and Workshops

- **Alumni Portal:** Shows all events, talks, and workshops in one place with proper registration, so students never miss a chance to learn or meet alumni. Everything is clear and in order.
- **WhatsApp Group:** Event details get buried under other messages, and there is no proper way to register or know what is coming up.

#### Getting Noticed by Alumni and Recruiters

- **Alumni Portal:** A student fills their profile once, and every alumnus can see the same updated version in one place, instead of sending the same resume to each person separately. The same profiles are also what let search and mentorship work.
- **WhatsApp Group:** A resume sent in chat reaches only one person and is quickly lost, and there is no way for others to find it later.
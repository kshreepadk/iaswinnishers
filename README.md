# IAS Winnishers — Website Starter Kit

This is a fresh, warm, energetic marketing website for IAS Winnishers, built to replace the current WordPress site and act as the foundation for your future LMS and mobile app. It's plain HTML/CSS/JS on purpose — no build tools, no dependencies — so it's easy for you or any developer to edit and easy to host anywhere.

## What's in the box

```
site/
  index.html                          Homepage
  about.html                          About Us — story, name origin, coaching philosophy, team
  programs.html                       IMP MBA Program, Prelims/Mains Mastery, Geography/Economy/Current Affairs Made Easy, Interview Guidance
  resources.html                      Free NCERT booklist, PYQs by topic, syllabus map + career counselling nudge
  career-counselling.html             Plan B / psychometric-assessment-based career counselling
  contact.html                        Counselling booking form + map
  blog.html                           Blog listing page
  blog-post.html                      "12-Month Study Plan" article
  answer-writing-framework.html       Blog article
  staying-steady-managing-stress.html Blog article
  daily-current-affairs-habit.html    Blog article
  choosing-upsc-optional-subject.html Blog article
  week-before-upsc-interview.html     Blog article
  login.html                          Placeholder — not linked from nav yet (no LMS backend)
  register.html                       Placeholder — not linked from nav yet (no LMS backend)
  robots.txt                          Tells search engines to crawl the site
  sitemap.xml                         Lists every page for search engines
  assets/
    style.css                        Master reference copy of the site's CSS (see note below)
    script.js                        Master reference copy of the site's JS
    logo.png                         Your logo file
```

Open `index.html` in any browser to preview the site immediately — no installation needed.

**A note on how the pages are built:** each HTML page carries its own copy of the CSS, JavaScript, and logo embedded directly inside it (rather than linking out to `assets/style.css`). This was a deliberate choice made partway through building the site, so that any single page can be opened, previewed, or shared on its own and always render correctly — it doesn't depend on the `assets/` folder sitting next to it. The `assets/` folder is kept as a master reference copy for convenience, but if you edit colors or layout, remember to make the same edit inside each page's own `<style>` block (or ask a developer to convert the site to link to `assets/style.css` externally instead, which is a quick change once you're past the editing phase).

## Design decisions, explained

- **Colors:** a warm cream canvas (`#FBF3E6`) throughout, deep near-black (`#26180F`) for headlines and dark structural blocks (footer, CTA banner, LMS teaser), coral (`#FF5A36`) as the primary action color (buttons, top bar, key emphasis), and marigold (`#FFB627`) as a secondary accent used mainly on the dark blocks so it pops. Green (`#166A4C`) is reserved only for success states (checkmarks, progress bars). Headings use Fraunces, body text uses Inter, and small uppercase labels use IBM Plex Mono. All colors are defined once at the top of each page's `<style>` block under `:root` — change a value there (and repeat in every page) to update it everywhere.
- **The staircase illustration** in the hero (Foundation → Prelims → Mains → Interview, rising to a flag) is the visual signature — a simple, literal read of "climbing toward your winning finish."
- **Fonts:** Fraunces (headings — warm, characterful) and Plus Jakarta Sans (body text — clean, friendly), loaded free from Google Fonts.
- The nav bar is Home · Programs · Resources · Career Counselling · Blog · About Us, with Contact pulled out to the far right edge, and the logo sitting almost flush against the left edge.
- Login and Register pages exist (`login.html`, `register.html`) but are currently unlinked from the navigation, since there's no live student account system yet — bring them back into the nav once the LMS is ready.
- I removed the words **"self-love"** and **"NLP"** everywhere, including the original testimonial that referenced an "NLP coach" — I rewrote it to describe the same supportive outcome without that term.

## How to edit things yourself (no coding experience needed)

Every page is a single `.html` file you can open in any text editor (Notepad, TextEdit, or free tools like **VS Code** or **Sublime Text**). Text you want to change is almost always sitting in plain English between tags like `<h1>...</h1>` or `<p>...</p>`.

1. **Change text:** Open the relevant `.html` file, find the sentence in the browser preview, search for a snippet of that same text in the file (Ctrl+F / Cmd+F), and edit it directly between the tags.
2. **Change a phone number, email, or address:** These appear in the top bar and footer of *every* page, so use "Find and Replace across files" in VS Code to update all pages in one go.
3. **Replace placeholder content:** Search the files for square brackets like `[Add fee]`, `[Add Coach Name]`, `[Add duration]` — these mark spots where I used a placeholder because I didn't have your real numbers, bios, or fees.
4. **Swap in your real logo:** Right now the header uses a simple SVG mark (an ascending path with a small flag) as a stand-in — you mentioned attaching a logo, but it didn't come through in our chat. To add it: save your logo file into `assets/` (e.g. `assets/logo.png`), then in each HTML file replace the `<svg class="brand-mark">...</svg>` block with `<img src="assets/logo.png" class="brand-mark" alt="IAS Winnishers logo">`.
5. **Change colors:** Open `assets/style.css`, edit the hex values inside `:root` at the top of the file.
6. **Add a new blog post:** Duplicate `blog-post.html`, rename it (e.g. `answer-writing-framework.html`), replace the title, meta description, and article content, then add a card linking to it in `blog.html`.
7. **Add real photos:** Replace the gradient placeholder blocks (coach portraits, blog thumbnails) with real `<img>` tags once you have professional photos — always add descriptive `alt` text for SEO and accessibility.

## Publishing the site (hosting)

Since it's plain HTML, you have easy, low-cost options:
- **Netlify or Vercel (free tier):** drag-and-drop the `site` folder in their dashboard — live in minutes, includes a free SSL certificate and a global CDN (fast loading everywhere, and ready to scale as traffic grows).
- **Your existing hosting/WordPress host:** upload the files via FTP, replacing what's there. You can keep your current domain (`iaswinnishers.com`) either way.
- Point your domain's DNS to whichever host you choose; both Netlify and Vercel walk you through this with clear instructions.

## Connecting your forms (lead magnets, counselling booking)

The forms currently show a friendly "Thanks!" message but don't send data anywhere yet — that needs a backend. The fastest options, roughly easiest to hardest:
1. **Formspree or Google Forms** — paste a form endpoint URL into the `<form>` tag's `action` attribute; emails land in your inbox or a spreadsheet within an hour of setup, no code.
2. **A CRM like Zoho CRM, LeadSquared, or HubSpot** (popular with Indian coaching institutes) — captures leads directly into a sales pipeline your counsellors can follow up on.
3. **Custom backend** — once you build the LMS (see below), route these same forms into that system so a "free mock test" signup automatically creates a student account.

## SEO — what's already done, and what to do next

**Already built in:**
- Unique, keyword-rich `<title>` and meta description on every page (e.g. "Personalised UPSC Coaching, One Aspirant at a Time" rather than generic titles).
- Semantic HTML structure (proper heading hierarchy, `<nav>`, `<main>`, `<footer>`).
- `sitemap.xml` and `robots.txt` so search engines can find and index every page.
- Structured data (`schema.org` JSON-LD) marking the site as an `EducationalOrganization` and the sample post as a `BlogPosting`, which helps rich results in Google.
- Mobile-responsive layout (Google ranks mobile experience directly).
- Fast-loading by design: no heavy frameworks, no unnecessary images.

**Do next, roughly in priority order:**
1. Replace placeholder graphics with real, compressed photos (use `.webp`, add descriptive `alt` text) — real photos of your coaches and classes will also just convert better.
2. Publish blog posts regularly (aim for 2–4/month) targeting real search terms your aspirants use — "UPSC optional subject comparison," "Bengaluru IAS coaching fees," "how to start UPSC preparation," etc. Competitors like Legacy IAS and Drishti IAS publish extensively; this is one of the highest-leverage things you can do.
3. Set up and verify a **Google Business Profile** for your Bengaluru location — this is what makes you show up in "IAS coaching near me" searches and Google Maps.
4. Get listed on relevant directories and get a few genuine backlinks (education directories, local Bengaluru business listings, guest posts).
5. Once traffic grows, add Google Analytics / Search Console to see what's working.

## How this compares to leading IAS institutes

I reviewed your current site and the leading national and Bengaluru institutes (Vajiram & Ravi, Drishti IAS, Vision IAS, Plutus IAS, and Legacy IAS in Bengaluru) to make sure nothing important was missing. Here's what stood out and how this site addresses it:

| What top institutes do well | How this site handles it |
|---|---|
| Free "readiness test" / mock test as a lead magnet (Legacy IAS) | Free Prelims Mock Test + Free Starter Kit + Free Coach Call, all on the homepage and Contact page |
| Small batch / personalised mentoring as a differentiator (Legacy IAS, Plutus IAS) | Made the *entire site's spine* — the 1-coach-per-aspirant model is the headline, not a footnote |
| Daily current affairs integration (Drishti, Vision IAS, Legacy) | Called out in Foundation program + a dedicated blog category + weekly email lead magnet |
| Structured test series with analysis (all major institutes) | Prelims and Mains test series each have their own program section explaining the format |
| Topper videos / success stories (Vajiram, First IAS) | Testimonials section on the homepage — add video testimonials here once you have them |
| Content-rich blog for SEO (Legacy IAS, Drishti, ClearIAS) | Full blog section with a working sample post as your content template |
| Hostel / offline infrastructure (Vajiram, Delhi institutes) | Not applicable to your model — your differentiator is personal coaching, not infrastructure, so the site leans into that instead |

Your biggest genuine point of difference against all of them is the **one-coach, whole-journey model with wellbeing built in** — every other institute either rotates faculty or treats mentoring as an add-on. The site is built to make that the first thing anyone sees.

## The LMS and mobile app — a realistic path to build it

A plain website cannot run a real learning platform (logins, video streaming, test scoring, coach messaging) — that needs an actual backend and database. Here's a scalable path:

### Phase 1 — now (done)
This marketing website: SEO-friendly, lead-generating, and ready to publish immediately.

### Phase 2 — MVP LMS (recommended: 2–4 months)
Two realistic routes:
- **Buy a white-label LMS** (faster, cheaper to start): platforms built for coaching institutes (e.g. Graphy, Teachmint, Classplus — popular with Indian coaching institutes) give you web + mobile app, live classes, tests, and payments out of the box, usually via subscription. Fastest way to get a working product live.
- **Custom-built LMS** (more control, more scalable long-term): a small dev team builds on a modern stack — e.g. **Next.js** for the web app, **React Native** or **Flutter** for one shared mobile codebase (iOS + Android), a Postgres database, and a hosting platform like **AWS**, **Vercel**, or **Supabase**. This is what lets you build your specific coach-assignment model exactly as you've designed it, rather than adapting to someone else's template.

Given your coach-matching model is your core differentiator, a custom build (or a white-label platform you can deeply customise) will serve you better long-term than a generic course-hosting tool.

### Phase 3 — scaling as traffic and students grow
- **API-first architecture:** build one backend API that both the website and the mobile app call — so you maintain one system, not two.
- **CDN + cloud hosting** for video and static content (AWS CloudFront, Cloudflare) so class videos load fast regardless of how many students are watching.
- **Managed database with room to grow** (e.g. managed Postgres on AWS RDS or Supabase) rather than a single server that gets overwhelmed at scale.
- **Separate services as you grow:** authentication, video delivery, and test-scoring can become independent services so one heavy feature (e.g. live class traffic) doesn't slow down the rest of the platform.

### What I'd suggest as your next concrete step
Publish this website first — it's ready now and will start generating leads and improving your SEO immediately. In parallel, get 2–3 quotes from developers or LMS platforms for Phase 2, using this site's coaching-model description as the brief, since it captures exactly what the LMS needs to reflect.

## Full checklist before you publish

- [ ] Replace the placeholder logo mark with your real logo
- [ ] Fill in every `[Add ...]` placeholder (fees, durations, coach bios, optional subjects)
- [ ] Replace gradient placeholder photos with real coach and campus photos
- [ ] Connect the lead-magnet and counselling forms to a real inbox/CRM
- [ ] Verify phone numbers, email, and address are correct across all pages
- [ ] Set up Google Business Profile and Google Search Console
- [ ] Publish 2–3 real blog posts before launch so the blog doesn't look empty

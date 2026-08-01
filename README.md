<div align="center">

<a href="https://www.abhijeetchandak.me/">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=26&pause=1200&color=22D3EE&center=true&vCenter=true&width=820&height=60&lines=Full-Stack+Software+Engineer;Node.js+%7C+TypeScript+%7C+React+%7C+AWS;4%2B+years+shipping+production+web+apps;Now+bringing+AI+features+into+real+products" alt="Full-Stack Software Engineer — Node.js, TypeScript, React, AWS" />
</a>

# Abhijeet Chandak

I build production web applications end to end — from API design and data modeling,
through React frontends and AWS deployments, to the live debugging that comes after.

<img src="https://img.shields.io/badge/Location-Mumbai%2C_India-22D3EE?style=flat-square&labelColor=1F2937" alt="Location: Mumbai, India" />
<img src="https://img.shields.io/badge/Experience-4%2B_years-22D3EE?style=flat-square&labelColor=1F2937" alt="Experience: 4+ years" />
<img src="https://img.shields.io/badge/Status-Open_to_opportunities-10B981?style=flat-square&labelColor=1F2937" alt="Status: open to opportunities" />

<br /><br />

<img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript" />
<img src="https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white" alt="Node.js" />
<img src="https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB" alt="React" />
<img src="https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js" />
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL" />
<img src="https://img.shields.io/badge/AWS-FF9900?style=flat-square" alt="AWS" />

<br /><br />

<a href="https://www.abhijeetchandak.me/"><img src="https://img.shields.io/badge/Portfolio-abhijeetchandak.me-22D3EE?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" /></a>
<a href="https://www.linkedin.com/in/abhijeet-chandak"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="mailto:abhijeetchandak10@gmail.com"><img src="https://img.shields.io/badge/Email-Say_hello-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>

</div>

---

## About

I'm a full-stack engineer with **4+ years** of experience, currently at **Response Informatics**,
building enterprise client products on a five-person team — Node.js/TypeScript services backed by
PostgreSQL and MongoDB, React frontends, and deployments I own on AWS.

Before that I spent two years building and running the web platform behind a Saudi sustainability
company's operations — **50,000+ users**, owned end to end, working directly with stakeholders
across timezones without a PM buffer. That role is where I learned that shipping a feature is
maybe half the job; the other half is everything that happens to it in production afterwards.

Lately I've been focused on taking **LLM-powered features** from API integration through the
hardening that makes them dependable enough to put in front of real users.

> My professional work lives in private client repositories, so none of it is published here.
> What's on this profile is side projects, experiments, and tools I built for myself.

---

## Something I built

Most of my work sits behind private repositories, so here's the shape of one instead —
**Docnify**, a PDF toolkit I wrote. The interesting problem wasn't the PDF manipulation;
it was that Ghostscript compression takes long enough to block a request. So it doesn't
run in one:

```mermaid
flowchart LR
    U["Browser<br/>React + Vite"]
    API["Express API"]
    DB[("MongoDB<br/>file metadata")]
    Q["Redis + BullMQ<br/>job queue"]
    W["Worker pool"]
    GS["Ghostscript<br/>compression"]
    PL["pdf-lib<br/>split · merge · reorder"]
    TTL["TTL sweeper<br/>purges uploads after 1h"]

    U -->|upload| API
    API --> DB
    API -->|enqueue| Q
    Q --> W
    W --> GS
    W --> PL
    W -->|progress| Q
    API -.->|poll status| U
    TTL -.->|delete| DB

    classDef accent fill:#22D3EE,stroke:#0891B2,color:#0B1220,font-weight:bold
    classDef muted fill:#334155,stroke:#64748B,color:#F1F5F9
    class U,API accent
    class DB,Q,W,GS,PL,TTL muted
```

The upload returns immediately, the heavy work happens on a worker, and the browser polls
for progress — so a 40 MB compression never holds a connection open. Uploaded files are
nobody's business but the uploader's, so a sweeper deletes them an hour later whether the
job finished or not.

---

## Currently learning

Mostly in the gaps between what I've had to build and what I haven't yet:

- **System design** — caching strategies, load balancing, queue-backed workloads, and the
  trade-offs behind distributed systems. Working through HLD and LLD for real applications
  rather than toy examples.
- **Cloud architecture** — going deeper than the EC2/RDS/S3 surface I use day to day, into
  deployment patterns, cost, and failure modes.
- **AI engineering** — prompt design, evaluation, and the production hardening that separates
  a demo from a feature people can rely on.

---

## Projects

| Project | What it does | Built with | |
|---|---|---|---|
| **Docnify PDF** | Browser-based PDF toolkit — compress, split, extract, reorder and remove pages, with batch processing. Architecture above. | `React` `Node.js` `Express` `MongoDB` `Redis` `BullMQ` `Ghostscript` | *private* |
| **AI Knowledge Quiz Builder** | Generates a five-question multiple-choice quiz on any topic using Google Gemini, grounded with Wikipedia context to keep questions factual. JWT auth scopes history and per-question review to each user. | `React` `Vite` `Node.js` `Express` `MySQL` `Gemini` | **[Code](https://github.com/abhijeet-chandak/ai-knowledge-quiz-builder)** · [Demo](https://ai-knowledge-quiz-builder.vercel.app) |
| **ApplyTracker** | Chrome extension that captures job applications straight off the listing page — it recognises LinkedIn, Indeed, Greenhouse, Lever and Workday — then tracks each through to offer with reminders and CSV/JSON export. Everything lives in local storage: no account, no server, nothing to leak. | `JavaScript` `Manifest V3` `Chrome APIs` | *private* |
| **MeetNotes** | Chrome extension putting a floating notes panel inside Google Meet, Zoom and Teams — agenda planning, timestamped notes, exportable action items. Entirely local: no backend, no analytics, no login. | `JavaScript` `Manifest V3` `Chrome APIs` | *private* |

<sub>Write-ups and screenshots at **[abhijeetchandak.me/#projects](https://www.abhijeetchandak.me/#projects)**</sub>

---

## Tech Stack

<table>
<tr><td><b>Backend</b></td><td>

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)

</td></tr>
<tr><td><b>Frontend</b></td><td>

![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Tailwind](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)

</td></tr>
<tr><td><b>Data</b></td><td>

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

</td></tr>
<tr><td><b>Cloud&nbsp;&&nbsp;DevOps</b></td><td>

![AWS](https://img.shields.io/badge/AWS_EC2_·_RDS_·_S3_·_CloudFront-FF9900?style=flat-square)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)

</td></tr>
<tr><td><b>AI</b></td><td>

![LLM](https://img.shields.io/badge/LLM_API_Integration-D97757?style=flat-square&logo=claude&logoColor=white)
![Prompt Engineering](https://img.shields.io/badge/Prompt_Engineering-10A37F?style=flat-square)

</td></tr>
</table>

---

## Experience

| Role | Company | Period | Location |
|---|---|---|---|
| **Software Engineer (Full Stack)** | Response Informatics | Sep 2025 – Present | Hyderabad · On-site |
| **Full Stack Developer** | Yadgreen Saudi Arabia | Jun 2023 – Aug 2025 | India · Remote |
| **Software Engineer Intern** | Mindbody | Jan 2023 – Jun 2023 | Pune · Hybrid |
| **Software Engineering Intern** | Magna Automotive India | Jul 2022 – Jan 2023 | Pune · Hybrid |
| **Web Developer** | Sarasvan Infosolutions | Nov 2020 – Dec 2021 | Nashik · On-site |

> **Recognition** — selected for a three-month on-site assignment at Yadgreen's Bahrain
> headquarters, in recognition of consistent high-quality delivery.

<sub>B.E. Information Technology, Pimpri Chinchwad College of Engineering — CGPA 9.59/10 ·
Full responsibilities at **[abhijeetchandak.me/#experience](https://www.abhijeetchandak.me/#experience)**</sub>

---

<div align="center">

<img src="https://my-readme-stats.vercel.app/api/top-langs/?username=abhijeet-chandak&layout=compact&theme=tokyonight&hide_border=true&border_radius=8&langs_count=6" height="150" alt="Most used languages" />

<br /><br />

**Open to opportunities** — if you're hiring, have a question, or just want to talk shop.

**[Portfolio](https://www.abhijeetchandak.me/)** · **[LinkedIn](https://www.linkedin.com/in/abhijeet-chandak)** · **[Email](mailto:abhijeetchandak10@gmail.com)**

</div>

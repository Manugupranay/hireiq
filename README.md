# HireIQ — AI Hiring Platform

Live app: https://robotinsighthireiq.netlify.app

---

I built this at Robot Insight Technologies because resume screening is genuinely broken. HR teams spend days going through resumes manually, and most of that time is wasted on candidates who clearly don't fit the role. HireIQ solves that — you upload resumes, describe what you need, and the AI scores and ranks every candidate in under a minute.

---

## What it does

The app has two sides — one for HR and one for candidates.

On the HR side, you fill in the job title, required skills, and a brief description of the role. You upload resumes — up to 10 at a time, any format. The AI reads each one, pulls out the relevant skills and experience, scores the candidate from 0 to 100 based on how well they match your requirements, and ranks everyone automatically. Once it's done, a full report lands in your inbox without you doing anything extra.

On the candidate side, you fill in your details, list your skills, write a short summary of your background, and upload your resume. The AI evaluates your application, gives you a match score, tells you what's working in your profile and what's not, and sends the full feedback to your email.

---

## How I built it

The core of the app is the Claude AI API. When a resume gets uploaded, the text is extracted in the browser using the File Reader API and sent to Claude along with the job requirements. Claude reads both, figures out the overlap, and returns a structured score and assessment. I chose Claude because it actually understands context — it does not just look for keyword matches, it reasons about whether the candidate's experience is genuinely relevant.

For the emails I used EmailJS, which lets me send from the frontend without needing a backend server. Both the HR report and the candidate feedback get sent automatically once the AI finishes.

The frontend is plain HTML, CSS, and JavaScript — no frameworks. I wanted to keep it lean and fast. The design uses Space Grotesk as the font and an emerald green color system. Hosted on Netlify, connected to GitHub so every push deploys automatically.

---

## Tech stack

- Claude AI API — resume analysis and candidate scoring
- Vanilla JavaScript — frontend logic and API integration
- HTML and CSS — UI and layout
- EmailJS — automated emails to HR and candidates
- File Reader API — in-browser resume text extraction
- Netlify — deployment and hosting
- GitHub — version control

---

## Run it locally

```bash
git clone https://github.com/Manugupranay/hireiq.git
cd hireiq
open index.html
```

You will need your own Claude API key and EmailJS credentials. Update the values at the top of the script section in index.html.

---

## What I would add next

The current version handles text-based resumes well. The next thing I want to tackle is better PDF parsing — right now if a PDF is heavily formatted or image-based, the text extraction is limited. I also want to add a way for HR to export the ranked results as a CSV, and eventually connect it to common ATS platforms.

---

Built by Pranay Bhaskar, Senior Developer at Robot Insight Technologies.

If this is useful to you, a star on the repo goes a long way.

> **Built at Robot Insight Technologies** by Pranay Bhaskar · Senior Developer

[![Live Demo](https://img.shields.io/badge/Live%20Demo-robotinsighthireiq.netlify.app-brightgreen?style=for-the-badge&logo=netlify)](https://robotinsighthireiq.netlify.app)
[![Built with Claude AI](https://img.shields.io/badge/AI-Claude%20by%20Anthropic-orange?style=for-the-badge)](https://anthropic.com)
[![Deployed on Netlify](https://img.shields.io/badge/Deployed-Netlify-00C7B7?style=for-the-badge&logo=netlify)](https://netlify.com)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow?style=for-the-badge&logo=javascript)
![HTML CSS](https://img.shields.io/badge/HTML%20%2F%20CSS-Modern-blue?style=for-the-badge)

---

## 🚀 What is HireIQ?

HireIQ is a **complete AI-powered hiring platform** that eliminates hours of manual resume screening. Upload resumes, define your ideal candidate, and let AI do the rest — ranking, scoring, and reporting in under 60 seconds.

### The Problem
Companies spend **23 hours on average** screening resumes per hire. HR teams manually read hundreds of resumes, often missing great candidates due to fatigue and bias.

### The Solution
HireIQ uses **Claude AI** to read every resume intelligently, score candidates 0–100 against your exact requirements, and deliver a ranked report — automatically.

---

## ✨ Features

### 👔 HR Portal
- Post a job with title, required skills, and job description
- Upload up to **10 resumes** at once (PDF, DOCX, TXT)
- AI reads and extracts skills, experience, and education from each resume
- Every candidate scored **0–100** against job requirements
- Candidates ranked as **Top Match / Good Match / Needs Review**
- Full ranked report **auto-emailed to HR** instantly

### 🎯 Candidate Portal
- Fill in personal details and skills
- Upload resume for AI evaluation
- Get an instant **AI match score** with detailed feedback
- Personalized **strengths, improvement areas & interview tips**
- Results **auto-emailed to the candidate**

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **Claude AI API** (claude-sonnet) | Resume analysis, scoring & candidate evaluation |
| **Vanilla JavaScript (ES6+)** | Frontend logic, file handling, API calls |
| **HTML5 / CSS3** | UI with Space Grotesk font, Emerald Green theme |
| **EmailJS** | Automated email delivery to HR & candidates |
| **File Reader API** | In-browser resume text extraction |
| **GitHub** | Version control & source code management |
| **Netlify** | Live deployment with CI/CD |

---

## 🎬 How It Works

```
HR uploads resumes + job description
        ↓
File Reader API extracts text from each resume
        ↓
Claude AI analyzes each resume against job requirements
        ↓
AI scores candidate 0-100 + determines match level
        ↓
Results ranked and displayed on screen
        ↓
EmailJS sends full report to HR automatically
        ↓
Candidate receives their score + feedback by email
```

---

## 📸 Screenshots

### HR Portal — Resume Screening
![HR Portal](https://robotinsighthireiq.netlify.app)

### Candidate Portal — Apply & Get Scored
![Candidate Portal](https://robotinsighthireiq.netlify.app)

---

## 🚦 Getting Started

### Option 1 — Use the Live App
👉 **[robotinsighthireiq.netlify.app](https://robotinsighthireiq.netlify.app)**

No setup needed. Works instantly in any browser.

### Option 2 — Run Locally
```bash
# Clone the repository
git clone https://github.com/Manugupranay/hireiq.git

# Open in browser
open index.html
```

> ⚠️ You'll need your own Claude API key and EmailJS credentials to run locally.

---

## 🔑 Configuration

To run with your own API keys, update these values in `index.html`:

```javascript
// EmailJS Configuration
const EJ_KEY     = 'your_emailjs_public_key';
const EJ_SERVICE = 'your_service_id';
const EJ_TEMPLATE = 'your_template_id';

// Claude AI is called via fetch — add your API key if running locally
```

---

## 📊 AI Scoring Logic

HireIQ's AI evaluates candidates on:

| Factor | Weight |
|---|---|
| Skill match (required vs candidate skills) | 45% |
| Experience level alignment | 30% |
| Overall profile quality & summary | 25% |

**Score Interpretation:**
- 🟢 **80–100** → Top Match — Highly Recommended
- 🔵 **60–79** → Good Match — Worth Interviewing
- 🟡 **Below 60** → Needs Review — Partial Match

---

## 🏗️ Project Structure

```
hireiq/
└── index.html          # Complete single-file application
                        # Contains HTML, CSS, JavaScript & AI integration
```

---

## 🌟 Key Highlights

- ⚡ **60-second screening** — AI analyzes resumes instantly
- 🤖 **Real AI reasoning** — not keyword matching, actual language understanding
- 📧 **Dual email automation** — HR report + candidate feedback
- 🎨 **Production-grade UI** — Space Grotesk font, Emerald Green design system
- 📱 **Fully responsive** — works on desktop, tablet & mobile
- 🔒 **No database needed** — serverless, privacy-friendly architecture

---

## 👨‍💻 Built By

**Pranay Bhaskar** · Senior Developer  
🏢 **Robot Insight Technologies**  
🌐 [robotinsighthireiq.netlify.app](https://robotinsighthireiq.netlify.app)

---

## 🤝 Contributing

Feel free to fork this project and submit pull requests! Ideas for improvement:
- [ ] Add support for bulk CSV export of candidate scores
- [ ] Integrate with ATS (Applicant Tracking Systems)
- [ ] Add interview scheduling feature
- [ ] Support for video resume analysis

---

## 📄 License

MIT License — free to use and modify.

---

⭐ **If you found this useful, please give it a star!** It helps others discover the project.

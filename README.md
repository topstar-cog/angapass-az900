# AngaPass: AZ-900 Study Coach (Unofficial)

*Your sky-high shortcut to AZ-900.* ("Anga" is Swahili for "sky".)

Smart Quiz Builder + Readiness Tracker for the Microsoft Azure Fundamentals (AZ-900) exam.
Built for the **Vibe Coding Hackathon: AZ-900 Exam Prep Edition** (#1MillionDevs).

> \*\*Unofficial study tool.\*\* Not affiliated with or endorsed by Microsoft. Microsoft and Azure are trademarks of Microsoft. No Microsoft logos are used, and no real exam questions are included.

**Live demo:** https://topstar-cog.github.io/angapass-az900/
**Pitch deck:** https://canva.link/6rkmsmn3fpmu3xi

## The problem

Many learners can recite AZ-900 definitions but still miss exam-style questions, because:

* Azure services with similar jobs blur together (Azure Policy vs RBAC, Azure Monitor vs Azure Advisor, Service Health vs Resource Health).
* IaaS, PaaS, SaaS and shared responsibility are easy to memorise but hard to apply to a real situation.
* Most practice tools mark an answer wrong without explaining why.

## The solution

AngaPass teaches learners to tell similar services apart. Every question is a short scenario, and after answering, **every option is explained**: why the right one fits and what each wrong one actually is.

## Features

* **96 original scenario questions** across the three AZ-900 domains (26 cloud concepts, 36 architecture and services, 34 management and governance)
* **Learn mode** by domain with instant feedback and a note under every option
* **Mock exam** (all questions, 30 minutes, no hints until the end) with a mistakes review
* **Weak-spot mode** that replays questions you last got wrong
* **Readiness dashboard** with accuracy per domain and an overall score weighted by the exam's domain weights. It is a study estimate, not an official score
* Question types: single choice and "choose two" (multiple response)
* Mobile-friendly, dark mode, no sign-up, progress saved on the device
* Clearly labelled **Unofficial** in the app

## Quick start

Open `index.html` in any browser. There is nothing to install and no backend.

## How it was built

* One file of plain HTML, CSS and JavaScript. Progress is stored with `localStorage`
* Free hosting on GitHub Pages, so it costs learners and the author nothing
* Questions live in a simple `Q` array inside `index.html`:

```js
{d:2, t:"Storage", q:"Scenario text...", o:\["Right answer","Wrong A","Wrong B","Wrong C"], a:\[0], e:"Why the right answer is right."}
```

`d` is the domain (1 to 3), `t` the topic, `o` the options, `a` the index (or indexes) of the correct option(s), `e` the explanation. Options are shuffled when shown. A small glossary in the code supplies the "why this wrong option doesn't fit" note, and a question can override it with an optional `w` field per option.

## Prompt engineering

I built AngaPass with Claude (Claude.ai) using prompts that were specific, constrained and checked. These are paraphrased from the real conversation.

1. **Grounding in my own material.** I uploaded my AZ-900 study guide and the hackathon rules and asked Claude to build a tool from them using only free tools. This kept the content tied to what I actually studied.
2. **Analyse the exam, then design.** I asked Claude to analyse how the AZ-900 exam is structured, using Microsoft's public study guide and skills outline, and to design our own questions from that structure without copying any real exam questions. The result was a blueprint: 96 questions split by domain weight (26 / 36 / 34).
3. **Scenario style over definitions.** I asked for questions that describe a real situation (for example a Nairobi sacco, a Lagos shop, a Kigali clinic) and ask which concept or service fits, because that is how the real exam tests understanding.
4. **Explain every option.** I asked that, once an answer is chosen, the app explains why the correct one is correct and why each of the others is not. This drove the per-option feedback.
5. **Check, don't trust.** After each batch of questions I had Claude validate the code and the question data with a script (valid syntax, counts per domain, no duplicates, answer indexes in range), and I checked the content against the public skills outline.
6. **Small, confirmed steps.** I worked in batches (24, 26, 24, 21 questions) and confirmed each step before moving on, which kept the build reliable under a tight deadline.

Prompt qualities I aimed for: a clear goal, hard constraints (free tools, original content, unofficial label), a named output format, and a check at the end.

## Accuracy and originality

* All questions are **original**, written from my own study guide and the **public AZ-900 skills outline on Microsoft Learn** (study guide updated July 2026). No real exam questions were copied.
* Questions on topics my guide covers thinly (for example Zero Trust, Defender for Cloud and Purview) are written from the public outline and marked "Outline-based" in their explanations.
* Always confirm details on Microsoft Learn before sitting the exam. Azure services and the exam outline change.

## Known limitations

* Some wrong options that are full sentences get a generic note instead of a specific one.
* The readiness score is an estimate from your answers in this app, not an official or predicted exam score.
* Only single-choice and choose-two formats are implemented so far.
* Progress is saved per browser, so clearing site data or switching devices resets it.

## How AngaPass maps to the hackathon

|Criterion|What AngaPass does|
|-|-|
|Learning value|Scenario questions with an explanation for every option, organised by exam domain|
|Prompt engineering|See the section above|
|User experience|Clean, mobile-first, dark mode, progress ring and domain bars|
|Rapid prototyping|Working app, live demo and repo built within the hackathon window|
|Technical creativity|One-file app, glossary-driven option feedback, domain-weighted readiness score|
|Documentation|This README, a live demo and a public repository|

## Roadmap

* Yes/No statement, dropdown ("complete the sentence") and match question formats, like the real exam
* Custom explanations for every wrong option, and more questions on easily confused pairs (including Resource Health vs Service Health)
* Flashcard mode and spaced repetition
* Swahili explanations
* Question packs for other fundamentals certifications
* Community-contributed scenarios

## Author

Built by Topister Were, a learner in the Power Learn Project / 1 Million Devs community, with help from Claude.


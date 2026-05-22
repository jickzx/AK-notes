---
notion-id: 296982ca-e761-8083-a25a-e0b4cc82ef0d
---
[[pimento’s notes]]

# **Project Roadmap — “Sass Translator”**

## **Objective**

Build a playful text transformation tool that rewrites messages into different humorous tones (e.g., passive aggressive, corporate HR, toddler, Shakespearean, <u>**brainrot**</u>) while preserving meaning. The system supports multiple languages via translation APIs and includes a back-translation check to show semantic consistency.

---

## **Core Features**

1. **Language Detection**
Automatically identify the input language.
2. **Translation Pipeline**
Convert text into English for consistent tone manipulation.
3. **Tone Rewriting Engine**
Apply selected style rules to reshape phrasing while retaining the original message.
4. **Back-Translation**
Convert the styled text back into the user’s original language.
5. **User Interface**
A simple, interactive web interface using Streamlit.

---

## **Team Roles & Responsibilities**

| Member | Role | Responsibilities |
| --- | --- | --- |
| **Alex** | **Pipeline & Integration Lead** | Define function interfaces and module boundaries, implement the end-to-end processing pipeline, coordinate integration and resolve blockers. |
| Pimentel | **Translation API & Caching Lead** | Implement language detection, translation calls, retry logic and caching; ensure resilience and stable performance. |
| Yusuf | **Tone Style Engine Developer** | Implement individual tone transformation functions and intensity scaling options. |
| James | **UI & Presentation Developer** | Build Streamlit interface, input/output layout, style selection controls and back-translation display. |

---

## **Work Breakdown by Module**

```plain text
/core/styles.py            → Tone rewriting logic (C)
/integrations/translate.py → Translation client + caching (B)
/core/pipeline.py          → Orchestration from input to output (A)
/app.py                    → Streamlit UI (D)

```

---

## **Timeline (25 hours)**

| Hours | Milestone | Description |
| --- | --- | --- |
| **0–1** | Architecture Setup | A defines function signatures and creates empty module structure. |
| **1–5** | Independent Development | Each member implements their assigned module. |
| **5–7** | Pair Integrations | A ↔ B integrate translation pipeline; C ↔ D connect UI to style engine. |
| **7–9** | Full System Connection | All modules linked, input flows through pipeline and displays output. |
| **9–12** | Debug & Stabilise | Fix interface mismatches, add graceful error handling. |
| **12–18** | Feature Refinement | Style intensity slider, optional translation toggle, improved UI display. |
| **18–22** | Polishing & Testing | Final cleanup, performance checks, add sample demo messages. |
| **22–25** | Demo Preparation | Record fallback demo, prepare short pitch and final presentation. |

---

## **Stretch Enhancements (If Time Allows)**

- Style intensity slider to control linguistic “spice”
- Side-by-side before/after comparison view
- Support for multiple translation providers
- Small semantic similarity score for meaning preservation display

---

## **Demo Plan**

6. Paste a neutral message
7. Apply different tones to show contrast and humour
8. Demonstrate translation and back-translation
9. Let a judge enter a message live for effect

---

## Tech Stack

| Component | Technology | Reasoning |
| --- | --- | --- |
| **Primary Language** | **Python** | Shared familiarity, fast iteration, strong library support |
| **Web Interface** | **Streamlit** | Rapid UI development with minimal boilerplate, good for live demos |
| **Translation Service** | **LibreTranslate API** (with optional swap to Google/DeepL) | Simple HTTP interface, multilingual support, free tier friendly |
| **Tone Manipulation Engine** | Pure Python string transformation functions | Transparent logic, easy to extend with new tones |
| **Caching Layer** | Custom in-memory cache | Reduces repeated translation calls, improves responsiveness during demos |
| **Version Control / Collaboration** | Git + GitHub | Branch-based workflow with peer review |
| **Testing** | `pytest` | Quick validation of module behaviour and integration points |

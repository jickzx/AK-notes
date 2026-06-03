---
notion-id: 27f982ca-e761-80eb-bf8e-d2f6106140c0
base: "[[Project Planner.base]]"
Status: Not started
Parent item: []
Sub-item: []
Deadline: 2025-10-28
---
[[Sass SaaS]]

# IDEA 1: Spotify Medieval Classifier

We could use flask and python to write something that takes in a playlist and pulls data from the Spotify API to determine what kind of medieval character your playlist represents.

# IDEA 2: Side-On Jousting Game

Reaction time game of two jousters

# IDEA 3: Mystic Predicts the weather

# IDEA 4: Web extension that turns text into Old English

## **Top Project Concepts**

### **1) *****The Sass Translator Bot***

Take any message and make it:

- passive aggressive
- overly academic
- corporate HR tone
- toddler whining tone

**API:** use *DeepL* or *Google Translate* + a small tone-conversion prompt model (or just rule-based style transforms)

**Example:**

Input: `Bro finish the slides`

Output (corporate): `Circling back to gently remind you of your ongoing slide deck responsibilities`

Funny + judge-friendly + easy to demo

---

### **2) *****Spotify Vibe Judge***

Reads a person’s Spotify listening history and **roasts their personality** based on their top genres / songs.

**API:** Spotify Web API

**Example Output:**

“Oh wow, 47 hours of sad piano playlists… do you need a hug or a therapist?”

---

### **3) *****Cat Facts as a Service — but Dramatic***

Call the **Cat Facts API**, but rewrite the facts like:

- Shakespeare monologue
- Aggressive drill sergeant
- Biblical prophecy

**API:** Cat Facts API

**Bonus:** Add a text-to-speech API so it *announces* them dramatically

---

### **4) “Will This Message Get Me Cancelled?” Checker**

User inputs a message → your app checks:

- Sentiment analysis
- Toxicity score
- Keyword flags

**API:** Google Perspective API (free)

Then output something like:

> “Risk Level: High
> This tweet will haunt your career. Touch grass.”

---

### *5) **Meme Generator Based on News Headlines**

Pull current headlines, detect tone, generate the *most fitting meme template*, overlay the text.

**APIs:**

- News API
- Meme Generator API

This gets applause if you make it **auto-refresh** every minute.

---

## **Recommended Stack (Simple + Works Fast)**

| Part | Tool |
| --- | --- |
| Backend logic | Python |
| API calls | `requests` |
| Quick UI | **Streamlit** (super easy) |
| Optional Bot | `discord.py` |

---

## **Demo Structure (for judges)**

1. Show input (Spotify user, text message, etc)
2. Show your transformation/analysis
3. Show hilarious output
4. End with audience participation (they type something → instant laugh)

This **wins rooms**.

---

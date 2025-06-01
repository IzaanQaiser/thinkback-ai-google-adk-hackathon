🔗 [google-adk-hackathon-technical](https://chatgpt.com/c/6837caba-9288-8011-908b-78f1c56a88d4) <br>
🔗 [google-adk-hackathon-design](https://chatgpt.com/g/g-p-68398ad2d004819189e4eb95f7f3e602-google-adk-hackathon/c/6838ce55-b514-8011-9273-674dca2168d8)

# execution-plan (010625-230625):
## ✅ **Phase 0 — Setup + Planning + Foundation + Branding (June 1)**

### 🧠 Ideation & Final Planning
- [ ] Finalize agent list (5 total: classification, nlp, search, conversation, context)
- [ ] Finalize 3 core use case scenarios
- [ ] Finalize MVP feature list (for June 1–23)
- [ ] Finalize execution-plan (build phases + goal for each)
- [ ] Make a file called `execution-plan.md` and push it to GitHub

<br>

### 🛠️ Repo + Project Setup

* [ ] Create GitHub repo (`thinkback-ai`)
* [ ] Initialize with README + MIT License
* [ ] Add folders:

  * `/documentation`
  * `/agents`
  * `/frontend`
  * `/backend`
* [ ] Create `.gitignore`, `.env.example`, and initial commit

<br>

### 📚 Learn the Tech & Platform (Google ADK)

* [ ] [Read Google Hackathon Resources](https://googlecloudmultiagents.devpost.com/resources)

<br>

### ☁️ Google Cloud Setup

* [ ] Go to [Google Cloud Console](https://console.cloud.google.com/)
* [ ] Create project called `thinkback-ai`
* [ ] Enable **Cloud Run**
* [ ] Enable **Firestore**
* [ ] Enable **Firebase Authentication**
* [ ] Enable **Gemini API (Generative AI)**
* [ ] Create service account + download credentials JSON
* [ ] Store in `/infra/credentials/service-account.json`

<br>

### 🧪 Local Dev Tools

* [ ] Install Node.js (via nvm or directly)
* [ ] Install Python 3.11+
* [ ] Install Firebase CLI (`npm i -g firebase-tools`)
* [ ] Install Google Cloud CLI
* [ ] Install ADK CLI (`pip install agentkit` or follow GitHub)
* [ ] Clone ADK sample repo and run it locally
* [ ] Confirm it works (i.e. run example with 2 agents)

<br>

### 🔁 Diagrams for System Planning

* [ ] Sketch **System Flow Diagram** (how data moves end-to-end)
* [ ] Upload `system-flow-diagram.png` to `/docs/`
* [ ] Sketch **Agent Interaction Diagram** (who talks to who)
* [ ] Upload `agent-interaction-diagram.png` to `/docs/`
* [ ] Sketch **Dataflow Diagram** (Firestore, Gemini, etc.)
* [ ] Upload `dataflow-diagram.png` to `/docs/`

<br>

### 🎨 Branding & Storytelling

* [ ] Create `/branding` folder
* [ ] Inside, write `problem.md` → 3–5 bullets about the core inspiration + pain
* [ ] Write 2–3 strong **taglines**, e.g.:

  * "Save the media that matters. Retrieve it when it counts."
  * "Your memory for the internet."
* [ ] Pick font from Google Fonts (e.g. Satoshi, Inter, or Space Grotesk)
* [ ] Pick color palette (background, text, accent)
* [ ] Save in `branding/branding-guide.md`

<br>

### 📝 Blog Prep (for +0.4 bonus points)

* [ ] Pick blog platform: Dev.to, Medium, Hashnode, Substack
* [ ] Create account and title for post:

  * “How I built a multi-agent AI memory system with Google Cloud”
* [ ] Create blog outline (intro, pain point, agents, tech stack, lessons)
* [ ] Save as `blog-outline.md`

<br>

### 📹 Demo Prep

* [ ] Install screen recording tool (pick one):

  * OBS Studio
  * Loom
  * Screen Studio (paid, cleanest)
* [ ] Do 1 test recording (30 sec walkthrough)

<br>

### 🧾 Submission Checklist (start draft)

Create a file `submission-checklist.md` and add the following:

- [ ] Hosted URL
- [ ] GitHub repo (public)
- [ ] Architecture diagram
- [ ] Agent interaction diagram
- [ ] Demo video (<3 min)
- [ ] Text description (features, tools, Google Cloud usage)
- [ ] Blog post
- [ ] ADK GitHub contribution link
- [ ] Region: North America

<br>
<br>

## 🧱 **Phase 1 — Project + Agent Scaffolding (June 2)**

### 🔧 Backend Setup (ADK + API Base)

* [ ] `cd backend/`
* [ ] Create Python virtual environment:
  `python3 -m venv venv && source venv/bin/activate`
* [ ] Install dependencies:
  `pip install agentkit fastapi uvicorn python-dotenv`
* [ ] Create files:

  * `main.py` (entrypoint for FastAPI)
  * `agent_registry.py` (central agent loader)
  * `router.py` (handles external API calls like /save, /search)
* [ ] Run:
  `uvicorn main:app --reload`
  Confirm: `http://localhost:8000` works

<br>

### 🤖 ADK Agent Scaffolding

* [ ] `cd agents/`
* [ ] Create folders:

  * `classification_agent/`
  * `nlp_agent/`
  * `search_agent/`
  * `conversational_agent/`
  * `context_agent/`
* [ ] Inside each folder, create:

  * `agent.py`
  * `__init__.py`
* [ ] Inside `agent.py`, create base skeleton:

```python
from agentkit import Agent

class [AgentName](Agent):
    def __init__(self):
        super().__init__(name="[agent_name]")

    def run(self, message):
        # Placeholder logic
        return {"response": "placeholder"}
```

(Do this for all 5 agents)

* [ ] Import each agent into `agent_registry.py` so they can talk

<br>

### 💻 Frontend Bootstrap

* [ ] `cd frontend/`
* [ ] Run:
  `npx create-next-app@latest . --typescript`
* [ ] Install Tailwind:
  `npm install -D tailwindcss postcss autoprefixer`
  `npx tailwindcss init -p`
* [ ] Configure `tailwind.config.js` and `globals.css`
* [ ] Install Shadcn/UI:
  `npx shadcn-ui@latest init`

<br>

### 🧪 Frontend Pages (Static for Now)

* [ ] `/save`: input URL, tags, notes
* [ ] `/dashboard`: list of saved content (mock data for now)
* [ ] `/chat`: input box to talk to conversational agent

<br>

### 🔁 Local Agent-API Connect

* [ ] `POST /api/save`: route to `classification_agent`
* [ ] `POST /api/search`: route to `search_agent`
* [ ] `POST /api/suggest`: route to `nlp_agent + search_agent`
* [ ] Return dummy responses for now (e.g. `{ title: "Motivation Video", url: "..." }`)

<br>

### ✅ Deliverables by End of Day (June 2)

* [ ] Backend live on `localhost:8000`
* [ ] 5 agents created as Python classes using `agentkit`
* [ ] Frontend has 3 basic pages (`/save`, `/chat`, `/dashboard`)
* [ ] One dummy API call from frontend to backend (e.g. call /search and display result)
* [ ] Push to GitHub (`dev` branch)

<br>
<br>

## 📥 **Phase 2 — Core Agent Logic + Save Flow (June 3)**

### 🤖 classification\_agent: Make It Work

#### Step 1 — Basic Content Classification

* [ ] Go to `agents/classification_agent/agent.py`
* [ ] Add logic to:

  * Accept a URL or plain text
  * Generate dummy tags (e.g. `"motivation"`, `"finance"`)
  * Return `main_tag`, `secondary_tags`, `title`, and `timestamp`

```python
def run(self, message):
    content = message["content"]
    # fake logic for now
    return {
        "main_tag": "motivation",
        "secondary_tags": ["productivity", "energy"],
        "title": "Get More Done With Less Stress",
        "timestamp": "2025-06-02T12:00:00"
    }
```

#### Step 2 — Create `/save` Route

* [ ] In `backend/router.py`, add:

```python
from fastapi import APIRouter, Request
from agent_registry import classification_agent

router = APIRouter()

@router.post("/save")
async def save_content(req: Request):
    body = await req.json()
    result = classification_agent.run({"content": body["content"]})
    return result
```

* [ ] Connect `router.py` to `main.py`:

```python
from fastapi import FastAPI
from router import router

app = FastAPI()
app.include_router(router)
```

* [ ] Test with `curl` or Postman:

```bash
curl -X POST http://localhost:8000/save -H "Content-Type: application/json" -d '{"content": "video about being disciplined"}'
```

<br>

### 🧠 Local Memory (Mock DB for Now)

#### Step 3 — Store in-memory per user

* [ ] In `backend/data.py`, create:

```python
mock_db = {
  "user_1": []
}
```

* [ ] In `router.py`, modify `/save` route:

```python
from data import mock_db

# ...
mock_db["user_1"].append(result)
```

<br>

### 💻 Frontend — Connect Save Flow

#### Step 4 — Update `/save` page

* [ ] Add input field (`textarea`) for content URL or text
* [ ] Add submit button → `POST /api/save`
* [ ] On success, show confirmation
* [ ] Add call to backend via `fetch('/api/save')`

<br>

### 📋 Dashboard Page (Read from Mock DB)

#### Step 5 — View all saved entries

* [ ] In `/dashboard`:

  * Show mock data list (you can hardcode for now)
  * Format: `title`, `tags`, `timestamp`

<br>

### ✅ Deliverables by End of Day (June 3)

* [ ] classification\_agent adds tags + metadata
* [ ] `/save` API returns that data
* [ ] Data is saved to mock DB
* [ ] Frontend `/save` → backend → save content
* [ ] `/dashboard` displays saved mock data

Perfect — June 4 = **Phase 3: Real AI Agent Logic + Conversational Search**
🗓️ **Date: June 4, 2025**
🎯 Goal: Users can talk to the AI and retrieve saved content by description or emotion.

<br>
<br>

## 💬 **Phase 3 — Conversational + Search Agents (June 4)**

### 🧠 conversational\_agent: Understand the Request Type

#### Step 1 — Recognize "direct search" vs "vibe-based" (emotional) queries

In `agents/conversational_agent/agent.py`:

```python
from agentkit import Agent

class ConversationalAgent(Agent):
    def __init__(self):
        super().__init__(name="conversational_agent")

    def run(self, message):
        query = message["query"].lower()
        if any(x in query for x in ["find", "saved", "video", "article", "about"]):
            return {"intent": "direct_search", "query": query}
        elif any(x in query for x in ["feel", "help", "motivation", "stuck", "burnt"]):
            return {"intent": "emotional_search", "query": query}
        else:
            return {"intent": "unknown", "query": query}
```

<br>

### 🔍 search\_agent: Match saved entries to request

In `agents/search_agent/agent.py`:

```python
from agentkit import Agent
from data import mock_db

class SearchAgent(Agent):
    def __init__(self):
        super().__init__(name="search_agent")

    def run(self, message):
        query = message["query"]
        entries = mock_db["user_1"]
        # naive matching — later upgrade with vector search
        matches = [e for e in entries if query.split()[0] in e["title"].lower()]
        return {"results": matches}
```

<br>

### 🧠 nlp\_agent: For emotional queries, generate related keywords

In `agents/nlp_agent/agent.py`:

```python
class NLPAagent(Agent):
    def __init__(self):
        super().__init__(name="nlp_agent")

    def run(self, message):
        if "unmotivated" in message["query"]:
            return {"keywords": ["motivation", "focus", "energy"]}
        return {"keywords": ["general help"]}
```

<br>

### 🧠 conversational\_agent: Full loop (talk → delegate → return)

In `router.py`:

```python
from agent_registry import conversational_agent, search_agent, nlp_agent

@router.post("/chat")
async def chat(req: Request):
    body = await req.json()
    intent = conversational_agent.run({"query": body["query"]})

    if intent["intent"] == "direct_search":
        results = search_agent.run({"query": intent["query"]})
    elif intent["intent"] == "emotional_search":
        keywords = nlp_agent.run({"query": intent["query"]})["keywords"]
        results = search_agent.run({"query": keywords[0]})
    else:
        results = {"results": []}

    return results
```

<br>

### 💻 Frontend `/chat` Page

#### Step 2 — Connect to Backend

* [ ] Add a chat-style input box
* [ ] On submit, call `POST /api/chat` with user query
* [ ] Show returned results in a friendly format:

  * `title`
  * `main_tag`
  * `timestamp`

Use dummy data if you have to — real AI will come soon (Gemini integration in Phase 5).

<br>

### ✅ Deliverables by End of Day (June 4)

* [ ] Conversational agent handles direct vs emotional queries
* [ ] NLP agent generates keywords for emotion-based queries
* [ ] Search agent returns matched saved entries
* [ ] `/chat` works end-to-end: input → backend → results
* [ ] Dashboard and Save flow still working
* [ ] Push latest to GitHub

<br>
<br>

## 🔐 **Phase 4 — Firebase Auth + Firestore Persistence (June 5)**

### 🧱 Step 1: Firebase Project Setup

* [ ] Go to [https://console.firebase.google.com](https://console.firebase.google.com)
* [ ] Create a new project: `thinkback-ai`
* [ ] Enable **Authentication**

  * Choose **Email/Password** and **Google Sign-In**
* [ ] Enable **Firestore Database**

  * Set to *Start in test mode* (you’ll lock it down later)
* [ ] Go to **Project Settings → General**

  * Copy the Firebase config (`apiKey`, `authDomain`, etc.)
* [ ] Go to **Project Settings → Service Accounts**

  * Generate **Admin SDK Key** (download `firebase-adminsdk.json`)

<br>

### 🔧 Step 2: Firebase SDK in Backend

* [ ] Install Firebase Admin SDK

```bash
pip install firebase-admin
```

* [ ] Add `firebase_admin` to `backend/firebase.py`

```python
import firebase_admin
from firebase_admin import credentials, auth, firestore

cred = credentials.Certificate("firebase-adminsdk.json")
firebase_admin.initialize_app(cred)
db = firestore.client()
```

<br>

### 🔐 Step 3: Secure API Routes with Firebase Auth

* [ ] In `router.py`, write a helper:

```python
from firebase_admin import auth

def verify_token(token):
    decoded = auth.verify_id_token(token)
    return decoded["uid"]
```

* [ ] Update `/save` route:

```python
@router.post("/save")
async def save_content(req: Request):
    body = await req.json()
    token = req.headers["Authorization"].split("Bearer ")[1]
    uid = verify_token(token)

    result = classification_agent.run({"content": body["content"]})
    db.collection("users").document(uid).collection("saves").add(result)
    return result
```

* [ ] Do the same for `/chat`: query from Firestore instead of `mock_db`

<br>

### 💻 Step 4: Firebase SDK in Frontend

* [ ] Install Firebase Web SDK

```bash
npm install firebase
```

* [ ] In `lib/firebase.ts`:

```ts
import { initializeApp } from "firebase/app";
import { getAuth } from "firebase/auth";

const firebaseConfig = {
  apiKey: "...",
  authDomain: "...",
  // rest of config here
};

const app = initializeApp(firebaseConfig);
export const auth = getAuth(app);
```

* [ ] Add Google Sign-In + logout button in `/dashboard`:

```ts
import { GoogleAuthProvider, signInWithPopup, signOut } from "firebase/auth";

const provider = new GoogleAuthProvider();
signInWithPopup(auth, provider).then((res) => {
  localStorage.setItem("token", res.user.getIdToken());
});
```

<br>
<br>

### 📬 Step 5: Send Token on Requests

* [ ] Update all fetch calls:

```ts
const token = await auth.currentUser.getIdToken();
fetch("/api/save", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer ${token}`,
  },
  body: JSON.stringify({ content: input }),
});
```

<br>

### ✅ Deliverables by End of Day (June 5)

* [ ] Firebase auth is live (Google + email login)
* [ ] Firestore stores all saved entries by real user UID
* [ ] All API routes verify token and use Firestore
* [ ] Frontend login and logout flow works
* [ ] You can save, chat, and view dashboard **per user**

## 🤖 Phase 5 — Gemini API + Semantic Understanding (June 6)

🗓️ **Date: June 6, 2025**
🎯 Goal: Add **real semantic processing** with **Gemini Pro**
– For classifying saved content
– For handling emotional/NLP queries
– For smarter matching in search

---

### ✅ Step 1 — Enable Gemini API in Google Cloud

* [ ] Go to [Google Cloud Console → APIs & Services](https://console.cloud.google.com/apis)
* [ ] Enable: **Vertex AI API**
* [ ] Enable: **Generative Language API**
* [ ] Go to **Credentials → Create API Key**
* [ ] Copy the API key, save it to `.env`

```env
GEMINI_API_KEY=your_key_here
```

---

### 🧠 Step 2 — Use Gemini in classification\_agent

In `agents/classification_agent/agent.py`:

```python
import requests
import os

class ClassificationAgent(Agent):
    def __init__(self):
        super().__init__(name="classification_agent")

    def run(self, message):
        content = message["content"]
        prompt = f"""
You are an AI that helps classify internet media.
Given this content:
\"\"\"
{content}
\"\"\"
Generate:
- A main category (e.g., motivational, financial, entertainment, academic)
- 3 relevant tags
- 1–2 sentences of context summary
Return it as a JSON object.
"""

        res = requests.post(
            "https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent",
            headers={"Content-Type": "application/json"},
            params={"key": os.environ["GEMINI_API_KEY"]},
            json={
                "contents": [{"parts": [{"text": prompt}]}]
            },
        )
        return res.json()["candidates"][0]["content"]["parts"][0]["text"]
```

✅ Now, `save` uses Gemini to actually understand and classify content.

---

### 💡 Step 3 — Use Gemini in NLP agent

In `agents/nlp_agent/agent.py`:

```python
class NLPAgent(Agent):
    def run(self, message):
        prompt = f"""
You are an NLP engine.
Given this user query: "{message['query']}", extract the user's emotional state and generate 3 keywords that would help them feel better.

Return a JSON with:
- emotion
- keywords
"""
        # same Gemini call structure as above
```

✅ Now, your **emotion-based search** has real understanding.

---

### 🔍 Step 4 — Smarter Matching in search\_agent

Replace naive keyword search with tag matching:

```python
def run(self, message):
    query = message["query"]
    user_entries = db.collection("users").document(uid).collection("saves").stream()
    # pull tags, context, etc., and match semantically (fuzzy match for now)
```

(You can upgrade this later with **vector embedding** if you want — let me know.)

---

### ✅ Deliverables by End of Day (June 6)

* [ ] Gemini API working
* [ ] `classification_agent` uses Gemini for tagging + summaries
* [ ] `nlp_agent` uses Gemini to detect emotion + give helpful tags
* [ ] `search_agent` matches based on Gemini-generated tags
* [ ] You can now save media → and **retrieve it smartly via chat**

<br>

💎 Optional Bonus (adds polish):

* [ ] Save original Gemini response in Firestore under `entry.analysis.rawGeminiOutput`

<br>
<br>

## 🧠 **Phase 6 — Timeline View, Smart Feed & Resurfacing (June 7)**

🗓️ **Date: June 7, 2025**
🎯 **Goal:** Display saved content in a **timeline**, and implement a **smart feed** that suggests resurfaced entries based on time, emotion, and relevance.

---

### ✅ Step 1 – Design Timeline View

* [ ] In your **Next.js frontend**, create a new `Timeline.tsx` component
* [ ] Each timeline item should show:

  * Title or summary
  * Date saved
  * Tags
  * Quick "Open" button
* [ ] Sort entries by timestamp (`created_at` from Firestore)

**Example card UI:**

```ts
{
  summary: "3 tricks to improve focus",
  tags: ["focus", "dopamine detox", "study"],
  created_at: "June 1, 2025",
}
```

<br>

### ✅ Step 2 – Design Smart Feed

* [ ] In your dashboard, create a section called **"Today’s Picks"**
* [ ] Use these criteria to pick 1–3 entries:

  * Saved exactly 7, 14, or 30 days ago
  * Has tags like "motivation", "reflection", "plan", or "reset"
  * Gemini classification score (if available)
* [ ] Use Firestore queries like:

```js
const lastWeek = today.minus(7, "days");
query where date == lastWeek and tags containsAny ["motivation", "plan"]
```

* [ ] Show: “🧠 You saved this 2 weeks ago. Want to revisit it?”

<br>

### ✅ Step 3 – Passive Resurfacing Logic

In backend (`agents/context_agent/agent.py` or central engine):

* [ ] Write a daily check for:

  * "What entries are time-relevant today?"
  * "What entries match recent user emotion queries?"
* [ ] Store `lastSuggestedAt` timestamp in each entry to avoid duplicates
* [ ] Return a list of resurfaced entries to the frontend feed

<br>

### ✅ Step 4 – Smart Feed + Timeline UI Polish

* [ ] Add filters (e.g., show only motivational entries)
* [ ] Add emoji/icon for tag category (💼 finance, 🧠 mindset, ⚡ energy)
* [ ] Optional: Add a “Rewind” button → view all entries from this day 1/2/4 weeks ago

<br>

### ✅ Step 5 – Firestore Cleanup (optional)

Make sure all saved entries in Firestore include:

* `created_at` timestamp
* `main_tag`
* `tags` (array)
* `summary` or description
* `lastSuggestedAt` (nullable)

<br>

### 🧪 Bonus Polish (Optional)

* [ ] Animate new entries fading into the feed
* [ ] Add a “why this?” tooltip to smart suggestions

<br>

### ✅ Deliverables by End of Day (June 7)

* [ ] Timeline of saved content (chronologically sorted)
* [ ] Smart Feed that suggests resurfaced entries from past
* [ ] Backend logic to filter + return suggestions
* [ ] Emojis/icons/tags for visual personality

<br>
<br>

## 🤖 Phase 7 — Agent Communication & Context Pipeline (June 8)

🗓️ **Date:** June 8, 2025
🎯 **Goal:** Stitch all 5 agents into a real working **multi-agent pipeline** using Google ADK — so they can pass messages, context, and results between each other.

---

### 🧩 Step 1 – Understand the Agent Flow

Draw this out (mentally or Figma):

> **User Message** → Convo Agent → (if emotional) NLP Agent → Global Context Agent
> → All context → Search Agent → Result → Back to Convo Agent → Back to User

There are **2 paths**:

* **Direct query** (e.g., "I saved a video about habits") → Convo → Search
* **Emotional query** (e.g., "I feel lost") → Convo → NLP → Context → Search

<br>

### 🧠 Step 2 – Define Shared Context Schema

Create a shared object called `context` that gets passed between agents:

```json
{
  "user_id": "abc123",
  "query_type": "emotional" | "direct",
  "raw_message": "i feel lost",
  "emotion_tags": ["burnout", "confusion"],
  "positive_tags": ["clarity", "motivation"],
  "global_tags": ["summer", "exam season", "AI news"],
  "final_tags_to_search": [...],
  "history": []
}
```

* [ ] Put this in a shared file like `/core/context.py`
* [ ] Update each agent to accept and mutate the `context` object

<br>

### 🔌 Step 3 – Convo Agent → NLP Agent Integration

* [ ] If user query includes emotional language (e.g., “I feel…” or “I'm struggling…”):

  * [ ] Convo agent forwards message to NLP agent
  * [ ] NLP agent extracts:

    * Emotional state
    * Opposite-positive state
    * Keywords
  * [ ] NLP agent updates `context` with those tags

<br>

### 🌐 Step 4 – Global Context Agent Integration

* [ ] NLP passes emotional tags → Global Context Agent
* [ ] Global agent pulls relevant tags from:

  * Static list (e.g., "summer", "exams", "AI layoffs", "Monday blues")
  * Gemini (optional prompt-based)
* [ ] Global agent appends global tags into context

<br>

### 🔍 Step 5 – Search Agent Logic

* [ ] Accepts final `context.final_tags_to_search`
* [ ] Queries Firestore for top-matching entries using:

```ts
where tags array-contains-any [tags]
order by score / time
limit 3
```

* [ ] Returns content IDs + summary → context.result

<br>

### 🗣️ Step 6 – Convo Agent Final Response

* [ ] If search returns nothing → respond: “Couldn’t find anything for that yet. Want to save something new?”
* [ ] If content found:

  * Show 1–3 cards with: title, summary, date
  * Respond with motivational copy like:
    *“You saved this last month. It might help now.”*
    *“Here’s what past-you thought future-you would need.”*

<br>

### ⚙️ Step 7 – Connect Agents via Google ADK (Minimal Example)

Use ADK’s **agent engine** to wire this up:

* [ ] Define all agents in `/agents.json`
* [ ] Use ADK CLI to test end-to-end communication
* [ ] Log context object at each step to verify correctness

<br>

### 🔄 Step 8 – Test Flows

**Emotional Query Test:**
“I feel like I’m falling behind”
✅ NLP → burnout → motivation → Search → 3 saved videos → Convo response

**Direct Query Test:**
“I saved a reel about dopamine detox”
✅ Search → find entry → respond

<br>

### 🧪 Bonus (Optional)

* [ ] Write unit test for `context` object
* [ ] Store `last_used_query_type` in Firestore per user
* [ ] Animate convo agent reply in frontend

<br>

### ✅ Deliverables for June 8

* [ ] Agents talk to each other using shared `context`
* [ ] Both emotional and direct queries supported
* [ ] ADK-powered agent flow fully working
* [ ] Results are returned to frontend

<br>
<br>







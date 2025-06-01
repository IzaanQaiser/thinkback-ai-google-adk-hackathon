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



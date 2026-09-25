# Career Discovery Skill

A conversational discovery skill designed to help young individuals explore and articulate who they are, what they want to do, what matters to them, what they can do, and what leverage they possess.

At its core, this skill is built on a single governing principle: **"Discover the person before defining the direction."** Instead of testing, evaluating, or prematurely prescribing job titles and career roadmaps, it guides users through organic self-reflection to build self-awareness across five core pillars.

---

## What It Does

The skill conducts an inquiry-driven discovery session organized around **The Five Pillars**:

1. **Vision**: Identifies what activities, pursuits, or things the user wants to undertake (focusing on intended action rather than occupational labels).
2. **Impact**: Uncovers what outcomes, changes, or effects they want their activities to produce for themselves or others.
3. **Interest**: Explores topics, fields, and experiences that attract their genuine curiosity and attention.
4. **Skill**: Highlights demonstrable current abilities supported by concrete examples, projects, and lived experiences.
5. **Resources**: Maps personal, social, material, institutional, and experiential support they can leverage.

Throughout the dialogue, the skill internally tracks the state of each pillar (`DEFINED`, `PARTIALLY_DEFINED`, `UNDEFINED`, `CONTRADICTORY`, or `INSUFFICIENT_EVIDENCE`) and synthesizes findings collaboratively with the user.

---

## Who It Is Useful For

- **Students & Young People**: Secondary school, high school, and early-stage college students who feel overwhelmed by traditional career pressure or uncertainty.
- **Early-Career Seekers**: Individuals entering the workforce or considering educational pathways without a fixed direction.
- **Mentors, Educators & Counselors**: Practitioners looking for a structured, non-judgmental discovery framework to facilitate exploratory conversations.
- **Agent Developers**: Builders seeking a ready-to-deploy, empathetic discovery workflow for AI mentors and assistants.

---

## Designed for Voice, Ready for Chat

### Primary: Voice Agents
This skill was designed from the ground up to excel in **spoken, real-time voice interactions**:
- **Single-Question Flow**: Asks only one question per turn to prevent cognitive overload.
- **Natural Spoken Cadence**: Avoids markdown tables, bullet dumps, and dense syntax that sound unnatural when spoken by text-to-speech (TTS) engines.
- **Pacing & Reflection**: Built to tolerate silence, uncertainty, and iterative back-and-forth dialogue.

### Secondary: Chat & Messaging Interfaces
The conversational style translates directly to text-based chat, messaging apps, and web interfaces, providing a warm, mentor-like companion experience.

---

## Repository Structure

```text
career-discovery-skill/
├── SKILL.md                 # Main agent skill definition (150 lines)
├── references/              # Conceptual knowledge base
│   ├── 01_vision.md         # Meaning, distinctions, and evidence of Vision
│   ├── 02_impact.md         # Meaning, distinctions, and evidence of Impact
│   ├── 03_interest.md       # Meaning, distinctions, and evidence of Interest
│   ├── 04_skill.md          # Meaning, distinctions, and evidence of Skill
│   └── 05_resources.md      # Meaning, distinctions, and evidence of Resources
├── templates/               # Reusable prompt templates
│   └── system_prompt.md     # Company-agnostic system prompt template
└── README.md                # Project documentation
```

---

## Installation & Setup

### 1. Antigravity Agent Workspace (Project Level)
To use this skill within an Antigravity-enabled repository or workspace:
1. Create a `.agents/skills/` directory at the root of your project if it doesn't already exist.
2. Copy the `career-discovery-skill` folder into `.agents/skills/career-discovery`:
   ```bash
   mkdir -p .agents/skills
   cp -r /path/to/career-discovery-skill .agents/skills/career-discovery
   ```
3. The agent will automatically discover `career-discovery` via progressive disclosure and activate it when prompts relate to career exploration or self-discovery.

### 2. Global Agent Installation (Machine-Wide)
To make this skill available across all projects on your machine:
- Copy the folder into your global Antigravity skills directory:
  - **Linux / macOS**: `~/.gemini/config/skills/career-discovery`
  - **Windows**: `%USERPROFILE%\.gemini\config\skills\career-discovery`

### 3. Standalone Voice / Chat Agent Integration
If integrating into a custom LLM pipeline (e.g., OpenAI Realtime API, LiveKit, ElevenLabs, or custom LangChain/LlamaIndex agents):
1. Supply `SKILL.md` as the core system instruction or persona runbook.
2. Make the five files inside [`references/`](./references/) available to the agent via tool retrieval, vector search, or bundled system context.
3. Configure your voice agent's turn-taking thresholds to allow natural pauses, as users frequently hesitate when reflecting on their aspirations.

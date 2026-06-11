# ⚖️ Indian Law Advisor
### AI-powered Indian legal guidance — Desktop App

> **Built for Cursor + Claude Agent vibe coding.**
> Open this folder in Cursor and ask Claude to add features directly.

---

## 🚀 Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Run the app
python main.py
```

Get a **free API key** at → https://console.anthropic.com

---

## 📁 Project Structure

```
IndianLawAdvisor/
│
├── .cursorrules             ← 🤖 AI agent rules (READ THIS FIRST)
├── main.py                  ← Entry point
├── requirements.txt
│
├── core/                    ← Business logic (no UI code here)
│   ├── analyzer.py          ← Claude API calls (LegalAnalyzer class)
│   ├── config_manager.py    ← config.json read/write
│   └── prompts.py           ← All AI system prompts
│
└── ui/                      ← All UI code (no API calls here)
    ├── app.py               ← Main window (IndianLawAdvisorApp)
    ├── components.py        ← Reusable widgets
    └── theme.py             ← Colors, fonts, design tokens
```

---

## 🤖 Vibe Coding with Cursor

The `.cursorrules` file tells the Claude agent everything about this project.

### Example prompts to use in Cursor:

**Add a history sidebar:**
```
Add a history sidebar panel to the left of the main layout. 
It should show the last 10 queries from config.json. 
Clicking one should reload the situation and result.
```

**Add PDF export:**
```
Add a "Save as PDF" button next to the Copy button in ResultBox.
Use the reportlab library. Save to ~/Downloads/LawAnalysis_<date>.pdf
```

**Add a follow-up question input:**
```
Below the result box, add a small input field labeled "Ask a follow-up question"
with a Send button. Wire it to the followup() method in core/analyzer.py.
```

**Add Hindi output option:**
```
Add a toggle in the header to switch output language between English and Hindi.
When Hindi is selected, append "Respond entirely in Hindi." to the system prompt.
```

**Change the colour scheme:**
```
Change the app's primary colour from deep blue to dark green (#1a5c38).
Update all relevant values in ui/theme.py.
```

---

## 🧩 Architecture Rules

| Rule | Detail |
|------|--------|
| UI → Core | UI calls `core/analyzer.py`, never `anthropic` directly |
| Config | Always use `core/config_manager.py`, never open `config.json` raw |
| Prompts | All system prompts live in `core/prompts.py` only |
| Threads | API calls always in a thread; use `self.after()` to update UI |
| Widgets | New reusable widgets → `ui/components.py` |
| Colors | All colors/fonts → `ui/theme.py` |

---

## 💰 API Cost
~₹1–3 per analysis. Monitor at https://console.anthropic.com/usage

## ⚠️ Disclaimer
Educational purposes only. Consult a qualified advocate for legal advice.

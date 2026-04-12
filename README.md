# 📖 Family Story Creator

Create beautiful, personalized family stories, poems, and multi-chapter books using AI. Features 6 story styles, character profiles, chapter templates, story continuation, and export to Markdown/HTML — treasured family keepsakes running 100% locally.

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB.svg?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Local LLM](https://img.shields.io/badge/Local_LLM-Ollama-000000.svg?style=for-the-badge&logo=ollama&logoColor=white)](https://ollama.com)
[![Privacy-First](https://img.shields.io/badge/100%25-Privacy--First-2ea043.svg?style=for-the-badge&logo=shield&logoColor=white)](#privacy-first)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![FastAPI](https://img.shields.io/badge/FastAPI-REST_API-009688.svg?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Streamlit](https://img.shields.io/badge/Streamlit-Web_UI-FF4B4B.svg?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io)

---

## ✨ Features

- **📚 Story Creation** - Write family stories using AI assistance
- **📖 6 Story Styles** - Classic, Adventure, Mystery, Romance, Historical, Fantasy
- **👥 Character Profiles** - Define family members and characters
- **📑 Multi-Chapter Books** - Create full books with table of contents
- **✍️ Smart Continuation** - AI continues your story maintaining consistency
- **📝 Chapter Templates** - Pre-structured templates for different story types
- **💾 Export Options** - Save as Markdown, HTML, or PDF
- **🎨 Rich Editing** - Web-based editor with formatting
- **🔒 100% Local** - Your family stories stay private
- **🎨 Web UI & API** - Web dashboard, CLI, or REST endpoints

---

## 🏗️ Architecture

```
┌─────────────────────┐
│   Story Details     │
│ (Plot, Characters)  │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  Story Engine       │
│ - Style Matching    │
│ - Content Gen       │
│ - Formatting        │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  Local LLM          │
│  (Ollama/Gemma)     │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  Story Output       │
│ - Markdown          │
│ - HTML              │
│ - PDF               │
└─────────────────────┘
```

---

## 📋 Project Structure

```
family-story-creator/
├── src/story_creator/
│   ├── __init__.py              # Package initialization
│   ├── core.py                  # Story creation logic
│   ├── styles.py                # 6 story style templates
│   ├── characters.py            # Character profile management
│   ├── exporters.py             # Markdown/HTML/PDF export
│   ├── cli.py                   # Click CLI interface
│   ├── api.py                   # FastAPI endpoints
│   └── web_ui.py                # Streamlit dashboard
├── templates/                   # Story templates
│   ├── classic_template.md
│   ├── adventure_template.md
│   ├── mystery_template.md
│   ├── romance_template.md
│   ├── historical_template.md
│   └── fantasy_template.md
├── tests/
│   ├── test_core.py             # Unit tests
│   └── __init__.py
├── config.yaml                  # Configuration
├── requirements.txt             # Dependencies
├── docker-compose.yml           # Docker setup
└── README.md                    # This file
```

---

## 🚀 Quick Start

### Prerequisites

- **Python 3.11+**
- **Ollama** (for local LLM)
- **Gemma 4 model** (via Ollama)

### Installation

```bash
# Clone the repository
git clone https://github.com/kennedyraju55/family-story-creator.git
cd family-story-creator

# Create and activate virtual environment
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Pull the AI model
ollama pull gemma4

# Verify installation
python -m story_creator.cli --help
```

### First Run

```bash
# Start Ollama
ollama serve &

# Create your first story
python -m story_creator.cli create \
  --title "Grandma's Adventures" \
  --style classic \
  --plot "Tell the story of grandmother's journey to America"

# Or launch web UI
streamlit run src/story_creator/web_ui.py

# Or use REST API
uvicorn src.story_creator.api:app --reload --port 8000
```

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Runtime** | Python 3.11+ | Core application |
| **CLI** | Click 8.1+ | Command-line interface |
| **Web** | Streamlit 1.28+ | Interactive editor |
| **API** | FastAPI | REST endpoints |
| **LLM** | Ollama + Gemma 4 | Creative writing AI |
| **Export** | Markdown/HTML | Multiple formats |
| **Testing** | pytest | Unit tests |
| **Deployment** | Docker | Container orchestration |

---

## 📖 Story Styles

### 1. **Classic** 📚
Traditional narrative style with descriptive prose. Best for:
- Family memoirs
- Historical accounts
- Personal journeys
- Coming-of-age tales

### 2. **Adventure** 🗺️
Action-packed narrative with plot twists. Best for:
- Travel stories
- Childhood memories
- Exploration tales
- Quest narratives

### 3. **Mystery** 🔍
Suspenseful storytelling with revelations. Best for:
- Unusual family events
- Untold stories
- Secret discoveries
- Puzzles and secrets

### 4. **Romance** 💕
Emotional and heartfelt narrative. Best for:
- Love stories
- Relationships
- Family bonds
- Touching moments

### 5. **Historical** 🏛️
Period-accurate storytelling. Best for:
- Ancestral history
- Era-specific events
- Cultural heritage
- Timeline narratives

### 6. **Fantasy** ✨
Imaginative narrative with magical elements. Best for:
- Whimsical family tales
- Legendary family stories
- Fairy tale adaptations
- Fantastical adventures

---

## 📖 CLI Reference

```bash
python -m story_creator.cli [COMMAND] [OPTIONS]
```

### Available Commands

| Command | Description | Example |
|---------|-------------|---------|
| create | Create new story | --title "..." --style classic |
| continue | Add chapters | --story-id abc --plot "..." |
| dd-character | Define characters | --name "Grandma" --role elder |
| list | Show your stories | — |
| iew | Display story | --story-id abc |
| xport | Export story | --story-id abc --format html |
| dit | Modify existing | --story-id abc |

---

## 🌐 Web UI

Launch the interactive editor:

```bash
streamlit run src/story_creator/web_ui.py
```

Access at **http://localhost:8501**

Features:
- ✍️ Rich text editor with formatting
- 👥 Character profile builder
- 📚 Story structure planner
- 🎯 Style selector with examples
- 📑 Chapter management
- 🔄 AI-powered continuation
- 💾 Auto-save functionality
- 📤 Export with preview
- 🎨 Beautiful typography

---

## ⚡ REST API

All features via FastAPI endpoints.

```bash
uvicorn src.story_creator.api:app --reload --port 8000
```

Interactive docs: **http://localhost:8000/docs**

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /health | Health check |
| POST | /stories | Create new story |
| GET | /stories/{id} | Get story |
| POST | /stories/{id}/chapter | Add chapter |
| POST | /stories/{id}/continue | AI-continue story |
| GET | /stories/{id}/export | Export story |
| POST | /characters | Add character |

---

## 📚 Python API

```python
from story_creator.core import create_story, add_chapter, continue_story
from story_creator.exporters import export_to_html

# Create a new story
story = create_story(
    title="Our Family History",
    style="classic",
    plot="Tell the story of how our family came together"
)

# Add a chapter
chapter = add_chapter(
    story_id=story['id'],
    title="Chapter 1: The Beginning",
    content="Once upon a time..."
)

# Continue the story with AI
continuation = continue_story(
    story_id=story['id'],
    prompt="What happened next?"
)

# Export to HTML
html_content = export_to_html(story_id=story['id'])
with open("family_story.html", "w") as f:
    f.write(html_content)
```

---

## 🐳 Docker Deployment

```bash
git clone https://github.com/kennedyraju55/family-story-creator.git
cd family-story-creator

docker compose up

# Access at http://localhost:8501
```

---

## 🧪 Testing

```bash
# Run all tests
pytest tests/ -v

# Run with coverage
pytest tests/ --cov=story_creator --cov-report=term-missing

# Run specific test
pytest tests/test_core.py::test_story_creation -v
```

---

## ⚙️ Configuration

Create a config.yaml:

```yaml
llm:
  model: "gemma4"
  temperature: 0.7
  max_tokens: 3000
  creative_mode: true

story:
  default_style: "classic"
  auto_save: true
  save_interval: 30

export:
  formats:
    - "markdown"
    - "html"
    - "pdf"
  include_toc: true
  include_metadata: true

characters:
  max_per_story: 20
  enable_relationships: true
```

---

## 🔒 Privacy-First

100% local processing:
- ✅ No cloud API calls
- ✅ No story data sharing
- ✅ Your family stories stay private
- ✅ Full AI control
- ✅ GDPR/HIPAA compliant
- ✅ No external tracking

---

## 💡 Ideas for Stories

- **Grandparent Memoirs** - Life stories from elder family members
- **Wedding Stories** - How you met your spouse
- **Childhood Tales** - Funny or touching childhood memories
- **Travel Adventures** - Family vacations and trips
- **Ancestral Histories** - Stories of great-grandparents
- **Family Legends** - Mythologized family events
- **Children's Tales** - Bedtime stories for grandkids
- **Letters to Future** - Messages for future generations

---

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: git checkout -b feature/amazing-feature
3. Commit changes: git commit -m 'Add amazing feature'
4. Push to branch: git push origin feature/amazing-feature
5. Open a Pull Request

---

## 📄 License

Licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 👤 Author

**Nrk Raju Guthikonda**
- GitHub: [@kennedyraju55](https://github.com/kennedyraju55)
- Dev.to: [@kennedyraju55](https://dev.to/kennedyraju55)
- LinkedIn: [Nrk Raju Guthikonda](https://linkedin.com/in/nrk-raju-guthikonda)

---

<div align="center">

**Made with ❤️ by kennedyraju55**

[⭐ Star this repo if you found it helpful!](https://github.com/kennedyraju55/family-story-creator)

</div>

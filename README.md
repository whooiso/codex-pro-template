# [Project Name]

> A brief, one-sentence description of what this project does and who it's for.

## Overview

[Provide a high-level overview of the project. What problem does it solve? What are its core features? Why does it exist?]

## Tech Stack

- **Frontend:** [e.g., React, Next.js, Tailwind CSS]
- **Backend:** [e.g., Node.js, Express, Python, FastAPI]
- **Database:** [e.g., PostgreSQL, MongoDB, SQLite]
- **Deployment:** [e.g., Vercel, Heroku, AWS]

## Getting Started

### Prerequisites

- [e.g., Node.js v18+]
- [e.g., Python 3.10+]
- [e.g., Docker]

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/PROJECT_NAME.git
   cd PROJECT_NAME
   ```

2. Install dependencies:
   ```bash
   # e.g., npm install or pip install -r requirements.txt
   ```

3. Set up environment variables:
   ```bash
   cp .env.example .env
   # Fill in the required values in .env
   ```

4. Start the development server:
   ```bash
   # e.g., npm run dev or python main.py
   ```

## Usage

[Provide basic instructions or examples on how to use the application or API.]

## AI Coding Assistant Setup (Codex / Claude Code / Cursor)

This repository uses the `AGENTS.md` standard to guide AI coding assistants.

1. Open your AI coding assistant in the project root.
2. Run the following prompt to initialize the context:
   > "Read the codebase and fill in Section 10 (Project context) of `AGENTS.md`. Find the stack, build/test/lint commands, and directory layout. Leave anything you can't confirm as `TODO`. Do not touch Section 11."
3. When the AI makes a mistake, correct it and say:
   > "Add a one-line note about this mistake to Section 11 of `AGENTS.md` so you don't do it again."

For complex, multi-hour tasks, use the `.agent/PLANS.md` template to create an ExecPlan.

## License

[e.g., MIT License - see the LICENSE file for details.]

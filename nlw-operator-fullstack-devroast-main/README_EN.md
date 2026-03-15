# DevRoast

Paste your code. Get roasted.

DevRoast is a code quality analyzer that gives a brutally honest score from 0 to 10. Submit any piece of code, enable "roast mode" for maximum sarcasm, and discover how bad (or good) your code really is.

Built during the **NLW** event from [Rocketseat](https://rocketseat.com.br), throughout the event lessons.

---

## 🌐🇧🇷 [Versão em Português](README.md)
## 🌐🇺🇸 [English Version](README_EN.md)

---

## 📸 Project Screenshots

<div align="center">
  <img src="public/Screenshot 2026-03-14 222148.png" alt="DevRoast Home" width="80%" style="margin: 16px 0; border-radius: 10px;">
  <img src="public/Screenshot 2026-03-14 222122.png" alt="DevRoast Analysis" width="80%" style="margin: 16px 0; border-radius: 10px;">
  <img src="public/Screenshot 2026-03-14 222103.png" alt="DevRoast Leaderboard" width="80%" style="margin: 16px 0; border-radius: 10px;">
</div>

---

## 🔨 Project Features

- **Code submission** — paste any snippet and receive an instant quality score
- **Roast mode** — enable brutal sarcasm for a more fun analysis
- **Detailed analysis** — specific feedback on what's wrong (and right) in your code, with severity levels (critical, warning, good)
- **Fix suggestions** — see a diff of how your code could look with improvements applied
- **Shame leaderboard** — the worst code on the internet, ranked by shame. See how yours compares

---

## ✔️ Techniques and Technologies Used

- **Framework:** Next.js 16 (App Router, React Compiler, Turbopack)
- **API:** tRPC v11 + TanStack React Query v5
- **Database:** Drizzle ORM + PostgreSQL 16
- **Validation:** Zod
- **Styling:** Tailwind CSS v4
- **Linting:** Biome 2.4
- **Package manager:** pnpm
- **Language:** TypeScript (strict)
- **AI:** AI SDK (OpenAI)
- **Others:** Shiki (syntax highlighting), Lucide React (icons)

---

## 📊 System Architecture

```mermaid
graph TB
    subgraph Client["Frontend (Next.js)"]
        UI[User Interface]
        Query[React Query]
    end
    
    subgraph API["API Layer (tRPC)"]
        Router[tRPC Router]
        Procedures[Procedures]
    end
    
    subgraph AI["AI Services"]
        Analyzer[Code Analyzer]
        Roaster[Roast Generator]
    end
    
    subgraph DB["Database (PostgreSQL)"]
        Schema[Drizzle Schema]
        Submissions[Submissions Table]
        Leaderboard[Leaderboard Table]
    end
    
    UI --> Query
    Query --> Router
    Router --> Procedures
    Procedures --> Analyzer
    Procedures --> Roaster
    Procedures --> Schema
    Schema --> Submissions
    Schema --> Leaderboard
```

---

## 📁 Project Structure

```
├── src/
│   ├── app/                    # Next.js App Router
│   │   ├── api/trpc/          # tRPC HTTP handler
│   │   └── ...                # Pages and layouts
│   ├── components/            # React components
│   │   ├── ui/               # Reusable components
│   │   └── ...               # Feature components
│   ├── db/                   # Drizzle ORM
│   │   ├── schema.ts         # Database schema
│   │   ├── client.ts         # Database client
│   │   └── seed.ts           # Database seed
│   ├── trpc/                  # tRPC infrastructure
│   │   ├── server.ts         # tRPC server
│   │   ├── client.ts         # tRPC client
│   │   └── routers/          # Domain routers
│   ├── hooks/                # Custom React hooks
│   └── lib/                  # Shared utilities
├── public/                    # Static files and images
├── specs/                    # Feature specifications
├── drizzle.config.ts        # Drizzle configuration
├── next.config.ts           # Next.js configuration
├── biome.json               # Biome configuration
├── .env.example            # Environment variables example
└── package.json            # Project dependencies
```

---

## 🛠️ Open and Run the Project

To start the project locally, follow the steps below in the **exact order**:

1. **Check Node.js version**:
   ```bash
   node -v
   ```

2. **Check pnpm version**:
   ```bash
   pnpm -v
   ```

3. **Clone the Repository**:
   ```bash
   git clone <REPOSITORY_URL>
   cd nlw-operator-fullstack-devroast-main
   ```

4. **Install dependencies**:
   ```bash
   pnpm install
   ```

5. **Check tool versions**:
   ```bash
   pnpm exec next --version
   pnpm exec tsx --version
   pnpm exec drizzle-kit --version
   ```

6. **Configure environment variables**:
   - Copy `.env.example` to `.env`
   - Fill in the required variables (see configuration section)

7. **Start the database with Docker**:
   ```bash
   docker compose up -d
   ```

8. **Run database migrations**:
   ```bash
   pnpm db:migrate
   ```

9. **Run database seed (optional)**:
   ```bash
   pnpm db:seed
   ```

10. **Start the development server**:
    ```bash
    pnpm dev
    ```

11. **Access the project**:
    - Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## ⚙️ Environment Variables Configuration

Copy the `.env.example` file to `.env` and configure the following variables:

```bash
# Database (REQUIRED - configure in Docker)
DATABASE_URL=postgresql://postgres:postgres@localhost:5432/devroast

# OpenAI (REQUIRED - needed for AI to work)
OPENAI_API_KEY=sk-...

# Next.js (REQUIRED)
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

---

## 🧪 Useful Commands

```bash
# Check Node version
node -v

# Check pnpm version
pnpm -v

# Check Next.js version
pnpm exec next --version

# Check Drizzle Kit version
pnpm exec drizzle-kit --version

# Run linting
pnpm lint

# Format code
pnpm format

# Generate migrations
pnpm db:generate

# Push schema to database
pnpm db:push

# Open Drizzle Studio
pnpm db:studio
```

---

## 🔄 Agent Workflows (NLW Full-Stack)

Modern development uses **spec-driven development** or the basics well done using a single AI agent. This project was developed following structured agentic workflows:

### Basic Development Workflow

| Workflow | Description |
|----------|-------------|
| **Brainstorming** | Activates before writing code. Refines rough ideas through questions, explores alternatives, presents design in sections for validation. Saves design document. |
| **Git Worktrees** | Activates after design approval. Creates isolated workspace on new branch, runs project setup, verifies clean test baseline. |
| **Writing Plans** | Activates with approved design. Breaks work into bite-sized tasks (2-5 minutes each). Every task has exact file paths, complete code, verification steps. |
| **Subagent-Driven Development** | Activates with plan. Dispatches fresh subagent per task with two-stage review (spec compliance, then code quality). |
| **Test-Driven Development** | Activates during implementation. Enforces RED-GREEN-REFACTOR: write failing test, watch it fail, write minimal code, watch it pass, commit. |
| **Code Review** | Activates between tasks. Reviews against plan, reports issues by severity. Critical issues block progress. |
| **Finishing Development Branch** | Activates when tasks complete. Verifies tests, presents options (merge/PR/keep/discard), cleans up worktree. |

> **Note**: The agent checks for relevant skills before any task. Mandatory workflows, not suggestions.

### Related Resources

- [Superpowers](https://github.com/obra/superpowers) - Complete software development workflow for coding agents, built on top of a set of composable "skills".
- [OpenCode](https://opencode.ai/) - AI for software development

---

## 📚 Resources and Useful Links

### Documentation
- [Pencil](https://www.pencil.dev/) - Create layouts and prototypes
- [OpenCode](https://opencode.ai/) - AI for development
- [NLW Operator - Event Guide](https://efficient-sloth-d85.notion.site/NLW-Operator-Guia-do-evento-30f395da57708093b620c5f7313bc612)

---

## 🌐 Deploy

The project can be deployed on platforms that support Next.js, such as:

- **Vercel** (recommended)
- **Netlify**
- **AWS Amplify**
- **Docker** (containerized build)

To deploy on Vercel:

1. Go to [Vercel](https://vercel.com)
2. Import the repository
3. Configure the necessary environment variables
4. The deployment will be done automatically

---

## 📄 License

This project was developed during the Rocketseat NLW event.

---

## 🤝 Acknowledgments

- [Rocketseat](https://rocketseat.com.br) for the NLW event
- DevRoast community

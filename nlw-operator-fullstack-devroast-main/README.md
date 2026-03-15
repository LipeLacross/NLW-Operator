# DevRoast

Cole seu codigo. Leve um roast.

DevRoast e um analisador de qualidade de codigo que da uma nota brutalmente honesta de 0 a 10. Envie qualquer trecho de codigo, ative o "roast mode" pra sarcasmo maximo, e descubra o quao ruim (ou bom) seu codigo realmente e.

Construido durante o evento **NLW** da [Rocketseat](https://rocketseat.com.br), ao longo das aulas do evento.

## Funcionalidades

- **Submissao de codigo** — cole qualquer trecho e receba uma nota instantanea de qualidade
- **Roast mode** — ative o sarcasmo brutal pra uma analise mais divertida
- **Analise detalhada** — feedback especifico sobre o que esta errado (e certo) no seu codigo, com niveis de severidade (critical, warning, good)
- **Sugestoes de fix** — veja um diff de como seu codigo poderia ficar com as melhorias aplicadas
- **Shame leaderboard** — o pior codigo da internet, rankeado por vergonha. Veja como o seu se compara

## Rodando o projeto
npm install -g pnpm
pnpm -v
```bash
# Instalar dependencias
pnpm install

# Rodar o servidor de desenvolvimento
pnpm dev
```

Abra [http://localhost:3000](http://localhost:3000) para ver o app.

NLW Operator | Guia do evento

https://www.pencil.dev/ para criar layouts
https://efficient-sloth-d85.notion.site/NLW-Operator-Guia-do-evento-30f395da57708093b620c5f7313bc612?source=copy\_link
https://opencode.ai/
prompt importante - me faça perguntas para entender melhor caso necessário
prompt fazer refatçoração de componententes utliizar o paptern de composição
prompt - commit using conetional commits pattern

ia para exploração - faça pesquisas sobre IA e o que ela pode fazer para buscar as melhoreso pções para ocntruir algo sem implemmntar

o dev hoje usa o spec driven development, ou o básico bem feito usando um único agente de IA
The Basic Workflow
brainstorming - Activates before writing code. Refines rough ideas through questions, explores alternatives, presents design in sections for validation. Saves design document.

using-git-worktrees - Activates after design approval. Creates isolated workspace on new branch, runs project setup, verifies clean test baseline.

writing-plans - Activates with approved design. Breaks work into bite-sized tasks (2-5 minutes each). Every task has exact file paths, complete code, verification steps.

subagent-driven-development or executing-plans - Activates with plan. Dispatches fresh subagent per task with two-stage review (spec compliance, then code quality), or executes in batches with human checkpoints.

test-driven-development - Activates during implementation. Enforces RED-GREEN-REFACTOR: write failing test, watch it fail, write minimal code, watch it pass, commit. Deletes code written before tests.

requesting-code-review - Activates between tasks. Reviews against plan, reports issues by severity. Critical issues block progress.

finishing-a-development-branch - Activates when tasks complete. Verifies tests, presents options (merge/PR/keep/discard), cleans up worktree.

The agent checks for relevant skills before any task. Mandatory workflows, not suggestions.

https://github.com/obra/superpowers
Superpowers is a complete software development workflow for your coding agents, built on top of a set of composable "skills" and some initial instructions that make sure your agent uses them.
opencode mcp list

# **Trilha Full-Stack: Workflows agênticos**

<aside>
<img src="/icons/bullseye_orange.svg" alt="/icons/bullseye_orange.svg" width="40px" />

Descrição da trilha

---

Já sabe programar? Então é hora de dominar desenvolvimento agêntico. 
Você cria uma aplicação full-stack real, estrutura workflows de desenvolvimento e aprende a trabalhar com IA em modo agente para decisões arquiteturais e implementação.

</aside>

---

### Links úteis

<aside>
<img src="/icons/color-palette_orange.svg" alt="/icons/color-palette_orange.svg" width="40px" />

Design (Pencil)

---

[devroast.pen](attachment:72275a7c-e8f0-4516-ae00-0a9e559f1f9a:devroast.pen)

</aside>

<aside>
<img src="/icons/document_orange.svg" alt="/icons/document_orange.svg" width="40px" />

Documentações

---

https://www.pencil.dev/

https://opencode.ai/

</aside>
Use exatamente nesta ordem:
node -v
pnpm -v
cd "C:\Users\felip\OneDrive\Documentos\NLW-Operator\nlw-operator-fullstack-devroast-main"
pnpm install
pnpm exec next --version
pnpm exec tsx --version
pnpm exec drizzle-kit --version
docker compose up -d
pnpm db:migrate
pnpm db:seed
pnpm dev

context7
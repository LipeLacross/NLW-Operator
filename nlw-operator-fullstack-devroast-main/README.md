# DevRoast

Cole seu código. Leve um roast.

DevRoast é um analisador de qualidade de código que dá uma nota brutalmente honesta de 0 a 10. Envie qualquer trecho de código, ative o "roast mode" para sarcasmo máximo, e descubra o quão ruim (ou bom) seu código realmente é.

Construído durante o evento **NLW** da [Rocketseat](https://rocketseat.com.br), ao longo das aulas do evento.

---

## 🌐🇧🇷 [Versão em Português](README.md)
## 🌐🇺🇸 [English Version](README_EN.md)

---

## 📸 Visual do Projeto

<div align="center">
  <img src="/Screenshot 2026-03-14 222148.png" alt="DevRoast Home" width="80%" style="margin: 16px 0; border-radius: 10px;">
  <img src="/Screenshot 2026-03-14 222122.png" alt="DevRoast Analysis" width="80%" style="margin: 16px 0; border-radius: 10px;">
  <img src="/Screenshot 2026-03-14 222103.png" alt="DevRoast Leaderboard" width="80%" style="margin: 16px 0; border-radius: 10px;">
</div>

---

## 🔨 Funcionalidades do Projeto

- **Submissão de código** — cole qualquer trecho e receba uma nota instantânea de qualidade
- **Roast mode** — ative o sarcasmo brutal para uma análise mais divertida
- **Análise detalhada** — feedback específico sobre o que está errado (e certo) no seu código, com níveis de severidade (critical, warning, good)
- **Sugestões de fix** — veja um diff de como seu código poderia ficar com as melhorias aplicadas
- **Shame leaderboard** — o pior código da internet, rankeado por vergonha. Veja como o seu se compara

---

## ✔️ Técnicas e Tecnologias Utilizadas

- **Framework:** Next.js 16 (App Router, React Compiler, Turbopack)
- **API:** tRPC v11 + TanStack React Query v5
- **Database:** Drizzle ORM + PostgreSQL 16
- **Validação:** Zod
- **Estilização:** Tailwind CSS v4
- **Linting:** Biome 2.4
- **Gerenciador de pacotes:** pnpm
- **Linguagem:** TypeScript (strict)
- **IA:** AI SDK (OpenAI)
- **Outros:** Shiki (syntax highlighting), Lucide React (ícones)

---

## 📊 Arquitetura do Sistema

```mermaid
graph TB
    subgraph Client["Frontend (Next.js)"]
        UI[Interface do Usuário]
        Query[React Query]
    end
    
    subgraph API["API Layer (tRPC)"]
        Router[tRPC Router]
        Procedures[Procedures]
    end
    
    subgraph AI["Serviços de IA"]
        Analyzer[Analisador de Código]
        Roaster[Roast Generator]
    end
    
    subgraph DB["Database (PostgreSQL)"]
        Schema[Drizzle Schema]
        Submissions[Tabela de Submissões]
        Leaderboard[Tabela de Leaderboard]
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

## 📁 Estrutura do Projeto

```
├── src/
│   ├── app/                    # Next.js App Router
│   │   ├── api/trpc/          # tRPC HTTP handler
│   │   └── ...                # Páginas e layouts
│   ├── components/            # Componentes React
│   │   ├── ui/               # Componentes reutilizáveis
│   │   └── ...               # Componentes de feature
│   ├── db/                   # Drizzle ORM
│   │   ├── schema.ts         # Schema do banco
│   │   ├── client.ts         # Cliente do banco
│   │   └── seed.ts           # Seed do banco
│   ├── trpc/                  # tRPC infrastructure
│   │   ├── server.ts         # Servidor tRPC
│   │   ├── client.ts         # Cliente tRPC
│   │   └── routers/          # Routers por domínio
│   ├── hooks/                # Custom React hooks
│   └── lib/                  # Utilitários compartilhados
├── public/                    # Arquivos estáticos e imagens
├── specs/                    # Especificações de features
├── drizzle.config.ts        # Configuração Drizzle
├── next.config.ts           # Configuração Next.js
├── biome.json               # Configuração Biome
├── .env.example            # Exemplo de variáveis de ambiente
└── package.json            # Dependências do projeto
```

---

## 🛠️ Abrir e rodar o projeto

Para iniciar o projeto localmente, siga os passos abaixo na **ordem exata**:

1. **Verifique a versão do Node.js**:
   ```bash
   node -v
   ```

2. **Verifique a versão do pnpm**:
   ```bash
   pnpm -v
   ```

3. **Clone o Repositório**:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   cd nlw-operator-fullstack-devroast-main
   ```

4. **Instale as dependências**:
   ```bash
   pnpm install
   ```

5. **Verifique as versões das ferramentas**:
   ```bash
   pnpm exec next --version
   pnpm exec tsx --version
   pnpm exec drizzle-kit --version
   ```

6. **Configure as variáveis de ambiente**:
   - Copie o arquivo `.env.example` para `.env`
   - Preencha as variáveis necessárias (veja a seção de configuração)

7. **Inicie o banco de dados com Docker**:
   ```bash
   docker compose up -d
   ```

8. **Execute as migrações do banco**:
   ```bash
   pnpm db:migrate
   ```

9. **Execute o seed do banco (opcional)**:
   ```bash
   pnpm db:seed
   ```

10. **Inicie o servidor de desenvolvimento**:
    ```bash
    pnpm dev
    ```

11. **Acesse o projeto**:
    - Abra [http://localhost:3000](http://localhost:3000) no seu navegador.

---

## ⚙️ Configuração de Variáveis de Ambiente

Copie o arquivo `.env.example` para `.env` e configure as seguintes variáveis:

```bash
# Banco de Dados (OBRIGATÓRIO - configurar no Docker)
DATABASE_URL=postgresql://postgres:postgres@localhost:5432/devroast

# OpenAI (OBRIGATÓRIO - necessário para IA funcionar)
OPENAI_API_KEY=sk-...

# Next.js (OBRIGATÓRIO)
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

---

## 🧪 Comandos Úteis

```bash
# Verificar versão do Node
node -v

# Verificar versão do pnpm
pnpm -v

# Verificar versão do Next.js
pnpm exec next --version

# Verificar versão do Drizzle Kit
pnpm exec drizzle-kit --version

# Rodar linting
pnpm lint

# Formatar código
pnpm format

# Gerar migrações
pnpm db:generate

#推送 schema para o banco
pnpm db:push

# Abrir Drizzle Studio
pnpm db:studio
```

---

## 🔄 Workflows Agênticos (NLW Full-Stack)

O desenvolvimento moderno utiliza **spec-driven development** ou o básico bem feito usando um único agente de IA. Este projeto foi desenvolvido seguindo workflows agênticos estruturados:

### Fluxo Básico de Desenvolvimento

| Workflow | Descrição |
|----------|-----------|
| **Brainstorming** | Ativado antes de escrever código. Refina ideias através de perguntas, explora alternativas, apresenta design em seções para validação. Salva documento de design. |
| **Git Worktrees** | Ativado após aprovação do design. Cria workspace isolado em novo branch, executa setup do projeto, verifica baseline de testes limpo. |
| **Writing Plans** | Ativado com design aprovado. Divide o trabalho em tarefas pequenas (2-5 minutos cada). Cada tarefa tem caminhos exatos, código completo, passos de verificação. |
| **Subagent-Driven Development** | Ativado com plano. Dispara subagentes frescos por tarefa com revisão em duas etapas (conformidade com spec, depois qualidade do código). |
| **Test-Driven Development** | Ativado durante implementação. Impõe RED-GREEN-REFACTOR: escreve teste falho, assiste falha, escreve código mínimo, assiste passar, commita. |
| **Code Review** | Ativado entre tarefas. Revisa contra o plano, reporta problemas por severidade. Problemas críticos bloqueiam progresso. |
| **Finishing Development Branch** | Ativado quando tarefas completam. Verifica testes, apresenta opções (merge/PR/keep/discard), limpa worktree. |

> **Nota**: O agente verifica skills relevantes antes de qualquer tarefa. Workflows mandatórios, não sugestões.

### Recursos Relacionados

- [Superpowers](https://github.com/obra/superpowers) - Workflow completo para agentes de código, construído sobre um conjunto de skills composáveis.
- [OpenCode](https://opencode.ai/) - IA para desenvolvimento de software

---

## 📚 Recursos e Links Úteis

### Documentações
- [Pencil](https://www.pencil.dev/) - Criar layouts e protótipos
- [OpenCode](https://opencode.ai/) - IA para desenvolvimento
- [NLW Operator - Guia do Evento](https://efficient-sloth-d85.notion.site/NLW-Operator-Guia-do-evento-30f395da57708093b620c5f7313bc612)

---

## 🌐 Deploy

O projeto pode ser implantado em plataformas que suportam Next.js, como:

- **Vercel** (recomendado)
- **Netlify**
- **AWS Amplify**
- **Docker** (build containerizado)

Para fazer deploy na Vercel:

1. Entre no [Vercel](https://vercel.com)
2. Importe o repositório
3. Configure as variáveis de ambiente necessárias
4. O deploy será feito automaticamente

---

## 📄 Licença

Este projeto foi desenvolvido durante o evento NLW da Rocketseat.

---

## 🤝 Agradecimentos

- [Rocketseat](https://rocketseat.com.br) pelo evento NLW
- Comunidade DevRoast

# pp-cli — Curso prático de Printing Press

Curso em português sobre **Printing Press** — a ferramenta que transforma sites e APIs em CLIs otimizadas para agentes de IA (Claude Code).

> **Por que isso importa?** Em benchmarks oficiais, MCP usa **35× mais tokens** que CLI na mesma tarefa, e a confiabilidade cai de 100% para 72%. CLIs são a forma mais eficiente de agentes conversarem com ferramentas externas.

## 📚 Curso

Acesse a versão web: **https://inematds.github.io/pp-cli/**

Ou navegue pelos módulos:

1. [Conceitos: CLI vs API vs MCP](docs/01-conceitos.md)
2. [Instalação (Go + binário + skills)](docs/02-instalacao.md)
3. [Primeiros passos com o starter-pack](docs/03-primeiros-passos.md)
4. [Criando sua própria CLI](docs/04-criando-cli.md)
5. [Caso prático: CLI para BrasilAPI](docs/05-caso-pratico.md)
6. [Integrações: n8n e Supabase](docs/06-integracoes.md)
7. [Publicando sua CLI no library oficial](docs/07-publicar.md)

## 🚀 Quick start

```bash
# Pré-requisitos: Go 1.26.3+, Node 18+, Claude Code

# 1. Instalar binário
go install github.com/mvanhorn/cli-printing-press/v4/cmd/printing-press@latest

# 2. Instalar starter-pack (4 CLIs prontas)
npx -y @mvanhorn/printing-press install starter-pack

# 3. Listar CLIs instaladas
npx -y @mvanhorn/printing-press list
```

Depois, no Claude Code, peça em linguagem natural:

> _"quais jogos da NBA têm hoje?"_ → invoca `pp-espn`
> _"voos baratos GRU→LIS em julho"_ → invoca `pp-flight-goat`

## 🔗 Links oficiais

- Site: https://printingpress.dev
- Repo principal: https://github.com/mvanhorn/cli-printing-press
- Biblioteca de CLIs: https://github.com/mvanhorn/printing-press-library

## 📝 Licença

Material do curso: MIT. Printing Press e CLIs derivadas seguem licenças dos repositórios oficiais.

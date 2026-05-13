# pp-cli — Curso prático de Printing Press

Curso em português sobre **Printing Press** — a ferramenta que transforma sites e APIs em CLIs otimizadas para agentes de IA (Claude Code).

> **Por que isso importa?** Em benchmarks oficiais, MCP usa **35× mais tokens** que CLI na mesma tarefa, e a confiabilidade cai de 100% para 72%. CLIs são a forma mais eficiente de agentes conversarem com ferramentas externas.

## 📚 Curso

Acesse a versão web (servida pelo GitHub Pages na raiz do `main`):

**https://inematds.github.io/pp-cli/**

### Estrutura

- [`index.html`](index.html) — landing geral
- [`curso/printing-press/index.html`](curso/printing-press/index.html) — trilha completa (mapa + 7 módulos)
- Módulos:
  1. [Conceitos: CLI vs API vs MCP](curso/printing-press/modulo-1-1.html)
  2. [Instalação completa](curso/printing-press/modulo-1-2.html)
  3. [Primeiros passos com o starter-pack](curso/printing-press/modulo-1-3.html)
  4. [Criando sua própria CLI](curso/printing-press/modulo-1-4.html)
  5. [Caso prático: BrasilAPI](curso/printing-press/modulo-1-5.html)
  6. [Integrações: n8n + Supabase](curso/printing-press/modulo-1-6.html)
  7. [Publicando no library oficial](curso/printing-press/modulo-1-7.html)

Cada módulo tem 6 tópicos com seções "O que é / Por que aprender / Conceitos-chave" e exemplos práticos reais.

## 🚀 Quick start

```bash
# Pré-requisitos: Go 1.26.3+, Node 18+, Claude Code 2.0+

# 1. Instalar binário factory
go install github.com/mvanhorn/cli-printing-press/v4/cmd/printing-press@latest

# 2. Instalar starter-pack (4 CLIs prontas)
npx -y @mvanhorn/printing-press install starter-pack

# 3. Listar CLIs instaladas
npx -y @mvanhorn/printing-press list
```

Depois, no Claude Code, peça em linguagem natural:

> _"quais jogos da NBA têm hoje?"_ → invoca `pp-espn`
> _"voos baratos GRU→LIS em julho"_ → invoca `pp-flight-goat`

## 🛠️ Servir localmente

```bash
# Qualquer servidor estático funciona, ex:
python3 -m http.server 8000
# Abra http://localhost:8000/
```

## 🔗 Links oficiais

- Site Printing Press: https://printingpress.dev
- Repo factory: https://github.com/mvanhorn/cli-printing-press
- Biblioteca de CLIs: https://github.com/mvanhorn/printing-press-library
- INEMA.CLUB: https://inema.club

## 📝 Licença

Material do curso: MIT. Printing Press e CLIs derivadas seguem licenças dos repositórios oficiais.

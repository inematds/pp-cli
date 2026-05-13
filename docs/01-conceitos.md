---
title: "Módulo 1 — Conceitos: CLI vs API vs MCP"
---

# Módulo 1 — CLI vs API vs MCP

⏱️ **10 min** · [← voltar ao índice](index.html) · [próximo: Instalação →](02-instalacao.html)

---

## O problema

Quando um agente (Claude Code, Codex, Gemini) precisa falar com um sistema externo, existem 3 caminhos:

1. **API** direto (HTTP request)
2. **MCP server** (Model Context Protocol)
3. **CLI** (Command Line Interface)

Cada um tem trade-offs. A diferença em **consumo de tokens** e **confiabilidade** é gigante.

---

## API: o jeito tradicional

```bash
curl -X GET "https://api.exemplo.com/posts?limit=10"
```

**Devolve:** JSON cru, frequentemente massivo (dezenas de KB), com campos que o agente não pediu.

| Prós | Contras |
|------|---------|
| Padrão universal | JSON gigante polui o contexto |
| Já existe pra quase tudo | Paginação manual |
| Documentação madura | Auth complexa pra agente gerenciar |

**Quando faz sentido:** integrações de código tradicional, onde você processa o JSON antes de enviar pro LLM.

---

## MCP: a promessa que não cumpriu (totalmente)

MCP (Model Context Protocol, lançado pela Anthropic em 2024) padronizou como agentes descobrem ferramentas. Você instala um MCP server e o agente vê todas as tools disponíveis.

**O problema:** todas as tools e descrições são carregadas **toda sessão**, mesmo que você não use nenhuma.

```
/context  # no Claude Code
> MCP servers: 47.000 tokens carregados (sem você invocar nada)
```

| Prós | Contras |
|------|---------|
| Descoberta automática | Overhead de tokens fixo |
| Tools tipadas | Server tem que estar rodando |
| Padronizado | Reliability cai com tarefas complexas |

**Benchmark oficial Printing Press:** MCP usa **35× mais tokens** que CLI na mesma tarefa. Reliability cai de **100% (CLI) para 72% (MCP)** conforme dificuldade aumenta.

---

## CLI: o vencedor para agentes

```bash
pp-espn games --league nba --date today
```

**Devolve:** texto curto, pré-formatado, pronto pro LLM consumir (~200 tokens em vez de 100k+).

| Prós | Contras |
|------|---------|
| Output enxuto e estável | Precisa instalar |
| Cache local em SQLite | Curva inicial |
| Sem overhead de contexto | Atualizações manuais |
| Auth resolvida 1× e armazenada | |
| Composable: `\|`, `&&`, scripts | |

### Por que o output é tão menor?

A CLI faz a request pesada, processa o JSON internamente, e **só devolve ao agente** o essencial. O JSON cru de 100k tokens **nunca entra no contexto**.

Exemplo real do vídeo de referência:
- Skool devolveu **132.000 tokens** ao binário CLI
- Apenas **~2.000 tokens** (resumo) entraram no contexto do Claude
- Economia: **98,5%**

---

## Tabela comparativa

| Critério | API | MCP | CLI |
|----------|-----|-----|-----|
| Tokens consumidos (overhead) | Alto (JSON cru) | Alto (descrições fixas) | **Baixo** |
| Confiabilidade em tarefas complexas | Variável | 72% | **100%** |
| Funciona offline (com cache) | ❌ | ❌ | ✅ |
| Composável (pipe, scripts) | Médio | ❌ | ✅ |
| Funciona sem API pública | ❌ | ❌ | ✅ (browser-sniff) |
| Setup | Zero | Médio | Médio |

---

## Quando usar cada um

- **API**: integrações de backend tradicional, processamento pesado de dados.
- **MCP**: protótipos rápidos, tools muito dinâmicas que você usa todo dia.
- **CLI**: agentes em produção, tarefas repetitivas, sites sem API.

**Regra prática:** se você está pagando por token (Claude Code Pro, Anthropic API), prefira CLI sempre que houver opção.

---

## Próximo passo

Vamos instalar tudo: [Módulo 2 — Instalação →](02-instalacao.html)

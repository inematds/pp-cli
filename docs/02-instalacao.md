---
title: "Módulo 2 — Instalação"
---

# Módulo 2 — Instalação completa

⏱️ **15 min** · [← módulo 1](01-conceitos.html) · [próximo →](03-primeiros-passos.html)

---

## Pré-requisitos

| Ferramenta | Versão mínima | Verificar |
|-----------|--------------|-----------|
| Go | **1.26.3** | `go version` |
| Node.js | 18+ | `node -v` |
| npm | 9+ | `npm -v` |
| Claude Code | 2.0+ | `claude --version` |
| git | 2.x | `git --version` |

---

## 1. Instalar Go

> Pular se já tem `go version go1.26.3` ou superior.

### Ubuntu/Debian (arm64 ou amd64)

```bash
# Descubra a arquitetura
uname -m
# arm64 (Mac M1/M2, Spark, Raspberry Pi 5) → use linux-arm64
# x86_64 → use linux-amd64

# Baixe a versão correta
cd /tmp
curl -LO https://go.dev/dl/go1.26.3.linux-arm64.tar.gz
# OU
curl -LO https://go.dev/dl/go1.26.3.linux-amd64.tar.gz

# Instale em /usr/local/go
sudo tar -C /usr/local -xzf go1.26.3.linux-*.tar.gz

# Adicione ao PATH
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> ~/.bashrc
source ~/.bashrc

# Verifique
go version
# go version go1.26.3 linux/arm64
```

### macOS

```bash
# Com Homebrew
brew install go

# Ou tarball: https://go.dev/dl/
```

> **Por que `$HOME/go/bin` no PATH?** É onde `go install` coloca binários compilados. Vai virar a casa dos seus CLIs.

---

## 2. Instalar o binário Printing Press

```bash
go install github.com/mvanhorn/cli-printing-press/v4/cmd/printing-press@latest
```

Vai baixar dependências e compilar (~1 min). Resultado:

```bash
printing-press --version
# printing-press 4.5.2
```

Esse binário é o **factory** — usado pra criar CLIs novas. Ele não é o que o agente chama no dia a dia; ele cria as CLIs específicas.

---

## 3. Instalar as skills no Claude Code

As skills (`/printing-press <app>`) são o que o agente realmente invoca.

**Opção A — Clone do repo (recomendado para estudar/contribuir):**

```bash
git clone https://github.com/mvanhorn/cli-printing-press.git
```

As skills ficam em `cli-printing-press/skills/` e o Claude Code as descobre automaticamente.

**Opção B — Instalar só as skills (mais leve):**

```bash
npx skills add mvanhorn/cli-printing-press/skills -g -a claude-code -y
```

---

## 4. Instalar o starter-pack

Pacote inicial com 4 CLIs prontas:

```bash
npx -y @mvanhorn/printing-press install starter-pack
```

Resultado esperado:

```
Bundle "starter-pack" → espn, flight-goat, movie-goat, recipe-goat
Installed espn
  binary: ~/go/bin/espn-pp-cli
  skill: pp-espn
Installed flight-goat
  ...
```

Liste o que foi instalado:

```bash
npx -y @mvanhorn/printing-press list
```

---

## 5. Verificação final

Cole tudo de uma vez:

```bash
echo "Go:        $(go version)"
echo "Node:      $(node -v)"
echo "npm:       $(npm -v)"
echo "Claude:    $(claude --version)"
echo "PP binary: $(printing-press --version)"
echo "Installed CLIs:"
npx -y @mvanhorn/printing-press list 2>/dev/null | tail -n +2
```

Se tudo retornou número de versão, está pronto.

---

## Solução de problemas

**`go: command not found`** → PATH não foi recarregado. Rode `source ~/.bashrc` ou abra novo terminal.

**`go install` falha com erro de Go version** → Sua versão de Go é antiga. Confirme `go version` ≥ 1.26.3.

**Permissão negada em `/usr/local/go`** → Use `sudo` no `tar -xzf`.

**Skills não aparecem no Claude Code** → Saia e reabra Claude Code; ele relê skills no startup.

**Atrás de proxy/firewall** → Configure `GOPROXY` ou `HTTPS_PROXY` antes do `go install`.

---

[próximo: Primeiros passos →](03-primeiros-passos.html)

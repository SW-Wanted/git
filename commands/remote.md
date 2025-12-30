# 📘 Git Remote — Guia de Referência

O comando `git remote` é usado para **gerenciar repositórios remotos** associados a um repositório local.
Ele define **de onde o código vem**, **para onde vai**, e **como o Git sincroniza estados distribuídos**.

Em termos práticos: `git remote` é o **sistema de endereçamento da rede Git**.

---

## 🔑 Função Principal

* Gerenciar URLs de repositórios remotos.
* Controlar branches remotos rastreados.
* Definir repositórios de fetch e push.
* Sincronizar múltiplas origens (origin, upstream, fork, mirror).
* Manter referências remotas limpas e atualizadas.

---

## 🧠 Conceito-Chave: O que é um Remote?

* Um *remote* é um **apelido (nome lógico)** para um repositório externo.
* Normalmente aponta para:

  * GitHub
  * GitLab
  * Servidor interno
* Cada remote mantém:

  * URLs (fetch/push)
  * Branches remotos (`origin/main`)
  * Configurações próprias

Exemplo clássico:

```
origin  → repositório principal
upstream → repositório original (fork)
```

---

## 📋 Operações Comuns

* `git remote` → lista remotes.
* `git remote -v` → lista remotes com URLs.
* `git remote add` → adiciona remote.
* `git remote remove` → remove remote.
* `git remote rename` → renomeia remote.
* `git remote show` → mostra estado detalhado.
* `git remote prune` → limpa referências obsoletas.
* `git remote update` → atualiza múltiplos remotes.

---

## ➕ Adicionar Remotes

### Básico

```bash
git remote add origin https://github.com/user/repo.git
```

### Buscar automaticamente após adicionar

```bash
git remote add -f upstream https://github.com/original/repo.git
```

### Rastrear apenas branches específicas

```bash
git remote add -t main -t develop origin <URL>
```

---

## 🔍 Listar e Inspecionar

### Listar

```bash
git remote
```

### Listar com URLs

```bash
git remote -v
```

### Mostrar detalhes completos

```bash
git remote show origin
```

Mostra:

* Branch padrão
* Branches rastreadas
* Branches locais fora de sincronia
* Status de fetch/push

---

## ✏️ Renomear e Remover

### Renomear

```bash
git remote rename origin upstream
```

Atualiza automaticamente:

* Branches remotos
* Configurações internas

### Remover

```bash
git remote remove staging
```

Remove:

* Configurações
* Branches remotos associados

---

## 🌿 Branch Padrão do Remote

### Detectar automaticamente

```bash
git remote set-head origin -a
```

### Definir explicitamente

```bash
git remote set-head origin main
```

### Remover referência

```bash
git remote set-head origin -d
```

Permite usar:

```bash
git fetch origin
```

em vez de:

```bash
git fetch origin/main
```

---

## 🔀 Gerenciar URLs

### Ver URL

```bash
git remote get-url origin
```

### Alterar URL

```bash
git remote set-url origin <nova-url>
```

### URLs diferentes para fetch e push

```bash
git remote set-url --push origin <push-url>
```

### Adicionar múltiplas URLs

```bash
git remote set-url --add origin <url-extra>
```

---

## 🧹 Limpeza (Prune)

### Limpar branches remotos deletados

```bash
git remote prune origin
```

### Simular limpeza

```bash
git remote prune --dry-run origin
```

> Essencial para manter o repositório **enxuto e confiável**.

---

## 🔄 Atualização em Massa

```bash
git remote update
```

### Com prune

```bash
git remote update --prune
```

Atualiza:

* Todos os remotes
* Grupos definidos em `remotes.<group>`

---

## 🧪 Casos de Uso Reais

### Trabalhando com fork

```bash
git remote add upstream <repo-original>
git fetch upstream
git merge upstream/main
```

### Espelhamento (mirror)

```bash
git remote add --mirror=fetch backup <URL>
```

### Clone manual controlado

```bash
git init
git remote add -f -t main origin <URL>
git merge origin/main
```

---

## ⚙️ Configuração Interna

Remotes são armazenados em:

* `remote.<name>.url`
* `remote.<name>.fetch`

Configuráveis via:

```bash
git config --list
```

---

## ⚠️ Boas Práticas

* Use `origin` apenas para o repositório principal.
* Use `upstream` em forks.
* Não misture fetch e push de lugares diferentes no mesmo remote.
* Prune regularmente.
* Nomeie remotes de forma semântica.

---

## ✅ Em resumo

`git remote` é o **controle de topologia distribuída do Git**.
Ele define como o teu repositório **conversa com o mundo externo** — com precisão, rastreabilidade e segurança.

Dominar `git remote` é deixar de ser apenas usuário de Git e passar a **arquitetar fluxos distribuídos**.
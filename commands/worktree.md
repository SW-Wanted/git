# 📘 Git Worktree — Guia de Referência

O comando `git worktree` é usado para **criar e gerenciar múltiplas árvores de trabalho (working trees)** associadas a um único repositório Git.  
Isso permite trabalhar em diferentes branches simultaneamente sem precisar clonar o repositório várias vezes.

---

## 🔑 Função Principal

* Criar múltiplos diretórios de trabalho vinculados ao mesmo repositório.
* Alternar entre branches em diferentes pastas sem conflito.
* Facilitar desenvolvimento paralelo (ex.: correção de bug em branch estável enquanto desenvolve feature em outro).
* Gerenciar e remover árvores de trabalho adicionais.

---

## 🧠 Conceito-Chave: Worktree = Várias Árvores de Trabalho

* Um repositório Git pode ter **uma árvore principal** e várias **árvores adicionais**.
* Cada worktree aponta para um branch diferente.
* Compartilham o mesmo `.git` central, mas têm diretórios separados.

👉 É como ter “clones leves” do mesmo repositório.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git worktree add ../branch-dev branch-dev
 ├── cria diretório ../branch-dev
 ├── associa ao branch branch-dev
 └── mantém .git compartilhado
```

---

## 📋 Operações Comuns

* `git worktree add ../feature-x feature-x` → cria nova árvore para branch `feature-x`.
* `git worktree list` → lista todas as árvores de trabalho ativas.
* `git worktree remove ../feature-x` → remove árvore de trabalho.
* `git worktree prune` → limpa árvores inválidas ou órfãs.
* `git worktree move ../old ../new` → renomeia/move árvore de trabalho.
* `git worktree lock` → bloqueia árvore para evitar remoção.
* `git worktree unlock` → desbloqueia árvore.

---

## 🌿 Exemplos Visuais

### Estrutura com múltiplas árvores

```
repo/
 ├── .git/
 ├── main/        (branch main)
 ├── feature-x/   (branch feature-x)
 └── hotfix/      (branch hotfix)
```

Cada diretório é uma árvore de trabalho vinculada ao mesmo repositório.

---

## 🔀 Opções Úteis

* `--detach` → cria worktree sem branch associado (HEAD destacado).
* `--force` → força criação mesmo se branch já estiver em uso.
* `--lock` → impede remoção automática.
* `--porcelain` → saída estável para scripts.

---

## 📊 Casos de Uso Reais

### Trabalhar em múltiplos branches ao mesmo tempo

```bash
git worktree add ../hotfix hotfix
```

### Revisar PR sem mexer na árvore principal

```bash
git worktree add ../review pr-123
```

### Limpar árvores antigas

```bash
git worktree prune
```

---

## ⚠️ Armadilhas Clássicas

* Criar worktree sem remover depois → acumula diretórios desnecessários.
* Usar `--force` sem cuidado → pode sobrescrever branch em uso.
* Confundir worktree com clone → worktree compartilha `.git`, clone é independente.

---

## 🧠 Regra de Ouro

> **Use `git worktree` para trabalhar em múltiplos branches sem precisar clonar o repositório.**

---

## ✅ Em resumo

`git worktree` é o comando para **gerenciar múltiplas árvores de trabalho** em um único repositório.  
Ele facilita desenvolvimento paralelo e revisão de código sem duplicar repositórios.

Quem entende `git worktree`:

* trabalha em vários branches com eficiência
* evita conflitos de checkout
* mantém repositório centralizado
* organiza melhor fluxos de desenvolvimento
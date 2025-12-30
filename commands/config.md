# 📘 Git Config — Guia de Referência

O comando `git config` é usado para **configurar o comportamento do Git** a nível **global**, **local** ou **do sistema**.
Ele define desde a tua identidade (nome e email) até opções avançadas como editor padrão, estratégia de merge, aliases e políticas de segurança.

---

## 🔑 Função Principal

* Define e altera configurações do Git.
* Controla o comportamento de comandos, merges e commits.
* Personaliza a experiência de uso (editor, cores, aliases).
* Gerencia credenciais e políticas de segurança.
* Diferencia configurações por repositório, utilizador ou sistema.

---

## 📋 Níveis de Configuração

O Git possui **três níveis hierárquicos** (do mais específico ao mais geral):

1. **Local** (`--local`)

   * Aplica-se apenas ao repositório atual.
   * Armazenado em `.git/config`.
2. **Global** (`--global`)

   * Aplica-se a todos os repositórios do utilizador.
   * Armazenado em `~/.gitconfig`.
3. **Sistema** (`--system`)

   * Aplica-se a todos os utilizadores do sistema.
   * Requer permissões de administrador.

> ⚠️ Prioridade: **local > global > system**

---

## ⚙️ Operações Comuns

* `git config --global user.name "Nome"`
* `git config --global user.email "email@exemplo.com"`
* `git config --list`
* `git config --global --list`
* `git config --local core.editor vim`
* `git config --unset user.email`
* `git config --get user.name`

---

## 🧠 Configurações Essenciais

### Identidade

```bash
git config --global user.name "Emanuel"
git config --global user.email "emanuel@email.com"
```

### Editor Padrão

```bash
git config --global core.editor "vim"
```

### Branch Padrão

```bash
git config --global init.defaultBranch main
```

### Cores no Terminal

```bash
git config --global color.ui auto
```

---

## ⚡ Aliases (Produtividade Máxima)

Aliases permitem criar **atalhos personalizados** para comandos Git.

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm "commit -m"
git config --global alias.lg "log --oneline --graph --all"
```

Uso:

```bash
git st
git co develop
git lg
```

---

## 🔐 Credenciais e Segurança

### Guardar Credenciais Temporariamente

```bash
git config --global credential.helper cache
```

### Guardar Credenciais Permanentemente

```bash
git config --global credential.helper store
```

### Configurar GPG para Commits Assinados

```bash
git config --global commit.gpgsign true
git config --global user.signingkey <GPG_KEY_ID>
```

---

## 🧩 Configurações Avançadas

* Estratégia de merge:

```bash
git config --global pull.rebase true
```

* Resolver conflitos automaticamente:

```bash
git config --global rerere.enabled true
```

* Respeitar permissões de ficheiros:

```bash
git config core.fileMode false
```

* Autocorreção de comandos:

```bash
git config --global help.autocorrect 1
```

---

## 📌 Exemplos Práticos

* Ver todas as configurações:

```bash
git config --list
```

* Ver apenas globais:

```bash
git config --global --list
```

* Alterar editor apenas num repositório:

```bash
git config --local core.editor nano
```

* Remover configuração:

```bash
git config --unset --global alias.co
```

---

## 🗂️ Ficheiros de Configuração

* `.git/config` → Configuração local
* `~/.gitconfig` → Configuração global
* `/etc/gitconfig` → Configuração do sistema

---

## ✅ Em resumo

`git config` é o **centro de comando do Git**.
Ele define **quem tu és**, **como trabalhas** e **como o Git reage** às tuas ações.
Dominar `git config` é deixar de ser apenas um utilizador de Git e passar a ser um **arquiteto do teu workflow**, com eficiência, segurança e identidade profissional.

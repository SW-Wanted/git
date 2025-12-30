# 📘 Git Commit — Guia de Referência

O comando `git commit` é responsável por **registar mudanças no repositório**, criando um novo *snapshot* do projeto.
Cada commit representa um **estado consistente do código**, ligado a um histórico imutável que sustenta colaboração, auditoria e evolução do software.

---

## 🔑 Função Principal

* Regista o conteúdo atual do **index (staging area)**.
* Cria um novo commit como filho direto do `HEAD`.
* Atualiza o branch atual para apontar para o novo commit.
* Associa mudanças a uma mensagem descritiva e metadados (autor, data, hash).

---

## 🧠 Conceito-Chave: Index (Staging Area)

Antes de um commit acontecer:

1. Alterações são feitas no *working tree*.
2. Arquivos são adicionados ao **index** com `git add`.
3. `git commit` grava exatamente o que está no index.

> Um commit **nunca grava automaticamente tudo** — grava apenas o que foi explicitamente preparado.

---

## 📋 Operações Comuns

* `git commit` → cria commit com editor interativo.
* `git commit -m "mensagem"` → cria commit direto.
* `git commit -a` → adiciona e comita arquivos rastreados.
* `git commit --amend` → altera o último commit.
* `git commit --dry-run` → simula o commit.
* `git commit -v` → mostra diff no editor.

---

## ✍️ Mensagem de Commit

Boas práticas:

```
Resumo curto (≤ 50 caracteres)

Descrição detalhada explicando:
- o que foi feito
- por que foi feito
- impactos relevantes
```

O **título** é usado por:

* `git log`
* `git format-patch`
* Pull Requests
* Ferramentas de revisão

---

## ⚙️ Formas de Criar um Commit

### Commit básico

```bash
git commit
```

### Commit direto

```bash
git commit -m "feat: adicionar autenticação"
```

### Commit automático (arquivos já rastreados)

```bash
git commit -a -m "fix: corrigir validação"
```

### Commit interativo

```bash
git commit -p
```

---

## 🔁 Alterar o Último Commit

```bash
git commit --amend
```

Usos comuns:

* Corrigir mensagem
* Incluir ficheiros esquecidos
* Ajustar pequenos erros

⚠️ **Nunca altere commits já publicados sem saber o impacto.**

---

## 🧹 Fixup, Squash e Autosquash

Criar commit de correção:

```bash
git commit --fixup <commit>
```

Criar commit de reescrita de mensagem:

```bash
git commit --fixup=reword:<commit>
```

Depois:

```bash
git rebase -i --autosquash
```

> Essencial para **histórico limpo e profissional**.

---

## 🛡️ Segurança e Assinaturas

### Commit assinado com GPG

```bash
git commit -S -m "chore: assinar commits"
```

Configuração global:

```bash
git config --global commit.gpgSign true
```

---

## 📌 Opções Importantes

* `--allow-empty` → permite commit vazio.
* `--no-verify` → ignora hooks.
* `--author="Nome <email>"` → sobrescreve autor.
* `--date="yesterday"` → sobrescreve data.
* `--cleanup=<mode>` → controla limpeza da mensagem.
* `--edit / --no-edit` → controla abertura do editor.

---

## 📊 Commit com Caminhos Específicos

```bash
git commit src/main.c
```

* Ignora o index.
* Commita apenas os arquivos indicados.
* O restante permanece staged.

---

## 🧪 Simulação

```bash
git commit --dry-run
```

Mostra:

* O que será commitado
* O que ficará de fora
* Arquivos não rastreados

---

## 🧩 Hooks Relacionados

`git commit` pode acionar:

* `pre-commit`
* `prepare-commit-msg`
* `commit-msg`
* `post-commit`
* `post-rewrite`

Essenciais para:

* lint
* testes automáticos
* validação de mensagens

---

## ⚙️ Configurações Relacionadas

* `commit.cleanup`
* `commit.gpgSign`
* `commit.status`
* `commit.template`
* `commit.verbose`
* `i18n.commitEncoding`

Controlam **formato, idioma, segurança e automação**.

---

## 📂 Ficheiros Importantes

* `.git/COMMIT_EDITMSG` → mensagem do commit em edição.
* `.git/config` → configurações locais.
* `~/.gitconfig` → configurações globais.

---

## 📌 Exemplos Práticos

### Fluxo clássico

```bash
git add .
git commit -m "feat: implementar login"
```

### Commit após resolver conflitos

```bash
git add arquivo_conflito.c
git commit
```

### Commit com template

```bash
git commit -t .gitmessage
```

---

## ⚠️ Boas Práticas

* Commits pequenos e focados.
* Uma ideia por commit.
* Mensagens claras e objetivas.
* Evitar commits quebrados.
* Usar `fixup` + `autosquash` para limpeza.

---

## ✅ Em resumo

`git commit` é o **ato fundamental de engenharia no Git**.
Cada commit é um contrato: ele documenta, versiona e sustenta decisões técnicas.
Dominar `git commit` é sair do nível “usuário de Git” e entrar no nível **engenheiro que controla o histórico**.

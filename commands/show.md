# 📘 Git Show — Guia de Referência

O comando `git show` é usado para **exibir informações sobre objetos Git** (commits, tags, trees e blobs).  
É muito utilizado para inspecionar commits, mostrando mensagem, autor e diff das alterações.

---

## 🔑 Função Principal

* Mostrar detalhes de commits (autor, data, mensagem).
* Exibir diffs introduzidos por um commit.
* Visualizar conteúdo de tags, trees e blobs.
* Verificar assinaturas GPG em commits.

---

## 🧠 Conceito-Chave: Show = Inspeção

* `git show` não altera nada.
* Ele apenas **exibe**:
  - Metadados do commit.
  - Diferenças introduzidas.
  - Conteúdo de objetos específicos.

👉 É o comando para **inspeção detalhada**.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git show <commit>
 ├── exibe mensagem do commit
 ├── mostra autor e data
 └── apresenta diff das alterações
```

---

## 📋 Operações Comuns

* `git show` → mostra último commit (HEAD).
* `git show <hash>` → mostra commit específico.
* `git show v1.0.0` → mostra tag e commit associado.
* `git show <branch>:<file>` → mostra conteúdo de arquivo em branch.
* `git show --oneline` → saída compacta.
* `git show --pretty=fuller` → saída detalhada.
* `git show --stat` → resumo de arquivos alterados.
* `git show --name-only` → apenas nomes de arquivos modificados.
* `git show --patch` → diffs completos (default).

---

## 🌿 Exemplos Visuais

### Exibir commit

```bash
git show 1a2b3c4
```

Saída:

```
commit 1a2b3c4
Author: Emanuel <emanuel@example.com>
Date:   Tue Dec 30 02:59 2025

    Corrige bug no login

diff --git a/app.js b/app.js
...
```

### Exibir conteúdo de arquivo em branch

```bash
git show main:README.md
```

---

## 🔀 Formatos de Saída

* `--pretty=oneline` → hash + mensagem.
* `--pretty=short` → autor + título.
* `--pretty=medium` → autor + data + mensagem.
* `--pretty=full` → autor + committer.
* `--pretty=fuller` → autor + committer + datas.
* `--pretty=email` → formato estilo patch.
* `--pretty=raw` → saída bruta.

---

## 🛡️ Modos de Segurança

### Verificar assinatura

```bash
git show --show-signature <commit>
```

Confere validade da assinatura GPG.

### Expandir tabs

```bash
git show --expand-tabs=4
```

Controla exibição de tabs em mensagens.

---

## 📊 Casos de Uso Reais

### Revisar último commit antes de push

```bash
git show
```

### Conferir alterações em arquivo específico

```bash
git show HEAD -- src/app.js
```

### Verificar tag de release

```bash
git show v2.0.0
```

---

## ⚠️ Armadilhas Clássicas

* Confundir `git show` com `git log` → `log` mostra histórico, `show` mostra detalhes de um commit.
* Usar sem opções em repositórios grandes → saída pode ser extensa.
* Não diferenciar formatos (`--pretty`) → pode perder informações importantes.

---

## 🧠 Regra de Ouro

> **Use `git show` para inspecionar commits e objetos específicos.  
> Use `git log` para navegar no histórico.**

---

## ✅ Em resumo

`git show` é o comando para **ver detalhes de commits e objetos Git**.  
Ele é essencial para revisão de alterações e inspeção de metadados.

Quem entende `git show`:

* revisa commits com precisão
* inspeciona tags e arquivos em versões passadas
* controla melhor o histórico
* trabalha com clareza em projetos colaborativos
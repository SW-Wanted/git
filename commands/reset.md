# 📘 Git Reset — Guia de Referência

O comando `git reset` é usado para **mover o HEAD para outro estado** e, opcionalmente, **alterar o índice (staging area) e a working tree**.
Ele atua diretamente sobre o **grafo de commits**, sendo fundamental para desfazer commits, reorganizar histórico e corrigir fluxos de trabalho.

> ⚠️ `git reset` **reescreve histórico**. Use com consciência.

---

## 🔑 Função Principal

* Move o `HEAD` para um commit específico.
* Controla o estado do **HEAD**, **índice** e **working tree**.
* Desfaz commits locais.
* Remove arquivos do staging sem perder alterações.
* Permite reestruturar commits (split, squash manual).

---

## 🧠 Modelo Mental (Essencial)

Git trabalha com **três camadas**:

```
[ Commit (HEAD) ] ← histórico
[ Index (Staging) ]
[ Working Tree ]
```

👉 `git reset` é o comando que **realinha essas três camadas**, dependendo do modo usado.

---

## 📋 Formas Principais de Uso

### Reset de commits (histórico)

```bash
git reset [--soft | --mixed | --hard | --merge | --keep] <commit>
```

### Reset apenas do índice (unstage)

```bash
git reset -- <arquivo>
git reset <commit> -- <arquivo>
```

### Reset interativo (por blocos)

```bash
git reset -p
```

---

## ⚙️ Modos de Reset (O Coração do Comando)

### 🔹 `--soft`

```bash
git reset --soft <commit>
```

* Move apenas o `HEAD`.
* **Index e working tree permanecem intactos**.
* Alterações ficam como *Changes to be committed*.

📌 Uso típico:

* Corrigir mensagem de commit.
* Reorganizar commits sem perder staging.

---

### 🔹 `--mixed` (padrão)

```bash
git reset <commit>
```

* Move o `HEAD`.
* Reseta o **index**.
* Mantém a working tree.

📌 Uso típico:

* Desfazer commit, mas manter código.
* Limpar staging area.

---

### 🔹 `--hard`

```bash
git reset --hard <commit>
```

* Move o `HEAD`.
* Reseta index e working tree.
* **Perde alterações locais em arquivos rastreados**.

⚠️ Perigoso. Irreversível sem reflog.

📌 Uso típico:

* Voltar completamente a um estado conhecido.
* Desfazer merge/pull problemático.

---

### 🔹 `--merge`

```bash
git reset --merge <commit>
```

* Usado para sair de um merge com conflito.
* Mantém alterações locais não adicionadas.
* Falha se houver inconsistências perigosas.

📌 Uso típico:

* Cancelar um merge mantendo trabalho local.

---

### 🔹 `--keep`

```bash
git reset --keep <commit>
```

* Remove commits.
* **Preserva alterações da working tree**.
* Aborta se houver conflito potencial.

📌 Uso típico:

* Mover commits errados para outro branch.

---

## 🧹 Reset de Arquivos (Unstage)

### Remover arquivo do staging

```bash
git reset -- arquivo.c
```

Equivalente moderno:

```bash
git restore --staged arquivo.c
```

👉 Working tree **não é afetada**.

---

## 🧩 Reset Interativo

```bash
git reset -p
```

* Remove blocos específicos do staging.
* O oposto de `git add -p`.

📌 Ideal para commits limpos e granulares.

---

## 🛠️ Casos de Uso Clássicos

### ❌ Commit errado (corrigir)

```bash
git reset --soft HEAD^
git commit -c ORIG_HEAD
```

---

### ❌ Commit não deveria estar no branch

```bash
git branch topic/wip
git reset --hard HEAD~3
git switch topic/wip
```

---

### ❌ Merge ou pull deu errado

```bash
git reset --hard ORIG_HEAD
```

Ou preservando alterações locais:

```bash
git reset --merge ORIG_HEAD
```

---

### 🔀 Dividir um commit em vários

```bash
git reset -N HEAD^
git add -p
git commit
```

---

## 🧠 ORIG_HEAD e Reflog

* Antes de qualquer reset de histórico, Git salva:

```text
.git/ORIG_HEAD
```

* Permite recuperação:

```bash
git reset --hard ORIG_HEAD
git reflog
```

👉 **Reset raramente é irreversível se fores consciente.**

---

## ⚠️ Armadilhas Comuns

* Usar `--hard` sem backup mental.
* Resetar commits já enviados para remoto.
* Confundir reset com revert.
* Não entender a diferença entre index e working tree.

---

## 🔄 Reset vs Restore vs Revert

| Comando | Reescreve histórico | Seguro em remoto |
| ------- | ------------------- | ---------------- |
| reset   | ✅ sim               | ❌ não            |
| restore | ❌ não               | ✅ sim            |
| revert  | ❌ não               | ✅ sim            |

---

## ✅ Em resumo

`git reset` é um **bisturi**, não um martelo.
Ele dá controle absoluto sobre o histórico local, staging e arquivos — mas exige **disciplina e entendimento profundo**.

Quem domina `git reset`:

* escreve histórico limpo
* corrige erros sem pânico
* entende Git como sistema de estados
* trabalha como engenheiro, não como usuário casual

# 📘 Git Restore — Guia de Referência

O comando `git restore` é usado para **restaurar arquivos da working tree e/ou do índice (staging area)** a partir de um estado conhecido (HEAD, index ou outro commit).
Ele foi introduzido para **separar responsabilidades** que antes ficavam concentradas no `git checkout`.

> 🎯 `git restore` **não mexe no histórico**. Ele atua apenas nos arquivos.

---

## 🔑 Função Principal

* Restaurar arquivos modificados ou apagados.
* Remover arquivos do staging (unstage).
* Recuperar arquivos a partir de commits específicos.
* Trabalhar de forma interativa (por blocos).
* Substituir usos perigosos/confusos de `git checkout`.

---

## 🧠 Modelo Mental (Essencial)

`git restore` atua **exclusivamente** nestas camadas:

```
[ Commit / Source ]
        ↓
[ Index (Staging) ]
        ↓
[ Working Tree ]
```

👉 Ele **copia conteúdo** de uma origem (`--source`) para um destino (`--staged`, `--worktree`).

---

## 📋 Uso Básico

### Restaurar arquivo na working tree

```bash
git restore arquivo.c
```

* Descarta alterações locais.
* Não afeta o histórico.
* Não afeta outros arquivos.

---

## ⚙️ Origens de Restauração (`--source`)

```bash
git restore --source=<commit> <arquivo>
```

Fontes comuns:

* `HEAD` (padrão)
* outro commit (`HEAD~2`)
* branch
* tag

📌 Se `--source` **não for usado**:

* com `--staged` → restaura a partir do `HEAD`
* sem `--staged` → restaura a partir do **index**

---

## 📦 Destinos de Restauração

### 🔹 Working Tree (padrão)

```bash
git restore arquivo.c
```

---

### 🔹 Index (unstage)

```bash
git restore --staged arquivo.c
```

Equivalente clássico:

```bash
git reset -- arquivo.c
```

---

### 🔹 Index + Working Tree

```bash
git restore --staged --worktree arquivo.c
```

Equivalente a:

```bash
git checkout -- arquivo.c
```

---

## 🧩 Modo Interativo

```bash
git restore -p
```

* Restaura **blocos específicos**.
* Ideal para desfazer alterações parcialmente.
* Mentalidade cirúrgica, não destrutiva.

---

## 🛠️ Casos de Uso Práticos

### ❌ Desfazer alterações locais

```bash
git restore main.c
```

---

### ❌ Recuperar arquivo apagado

```bash
git restore hello.c
```

---

### 🔄 Restaurar versão antiga de um arquivo

```bash
git restore --source=HEAD~2 Makefile
```

---

### 🔁 Unstage sem perder código

```bash
git restore --staged arquivo.c
```

---

### 🔀 Restaurar tudo no diretório

```bash
git restore .
```

Ou a partir da raiz:

```bash
git restore :/
```

---

## ⚔️ Conflitos (ours / theirs)

Durante conflitos de merge:

```bash
git restore --ours arquivo.c
git restore --theirs arquivo.c
```

Ou recriar o conflito:

```bash
git restore --merge arquivo.c
```

---

## 🧠 Restore vs Reset vs Revert

| Comando | Atua em arquivos | Reescreve histórico | Seguro em remoto |
| ------- | ---------------- | ------------------- | ---------------- |
| restore | ✅ sim            | ❌ não               | ✅ sim            |
| reset   | ⚠️ parcial       | ✅ sim               | ❌ não            |
| revert  | ❌ não            | ❌ não               | ✅ sim            |

📌 **Regra prática**

* Erro em arquivo → `restore`
* Erro em commit local → `reset`
* Erro em commit público → `revert`

---

## ⚠️ Observações Importantes

* `git restore` é marcado como **experimental**, mas já é padrão.
* Não confundir com rollback de commit.
* Arquivos restaurados **perdem alterações locais**.
* Funciona muito bem com `-p` para controle fino.

---

## 🧭 Filosofia do Git Moderno

Git agora segue a separação clara:

* `git switch` → mover entre branches
* `git restore` → restaurar arquivos
* `git checkout` → legado / casos avançados

👉 Isso reduz erros e aumenta legibilidade.

---

## ✅ Em resumo

`git restore` é o **comando do dia a dia**.

Ele:

* é seguro
* é explícito
* não mexe no histórico
* protege o fluxo colaborativo
* força clareza de intenção

Quem domina `git restore`:

* não perde trabalho por engano
* trabalha com confiança
* entende Git como sistema de estados
* escreve histórico limpo sem medo
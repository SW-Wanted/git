# 📘 Git Add — Guia de Referência

O comando `git add` é responsável por **mover conteúdo da working tree para o index (staging area)**.
Ele **define exatamente o que fará parte do próximo commit**.

> 🧠 Commit não lê a working tree.
> Commit lê **o index**.
> `git add` é quem decide o que entra lá.

---

## 🎯 Função Principal

* Preparar conteúdo para commit
* Controlar **o que** será versionado
* Permitir commits parciais e cirúrgicos
* Atualizar, adicionar ou remover ficheiros do index
* Servir como **filtro consciente** entre código local e histórico

---

## 🧠 Modelo Mental Essencial

```
[ Working Tree ] --(git add)--> [ Index ] --(git commit)--> [ Repository ]
```

* Working Tree → caos criativo
* Index → snapshot deliberado
* Commit → histórico imutável

👉 `git add` **não cria commits**
👉 Ele cria **intenção**

---

## 📋 Uso Básico

### Adicionar um ficheiro

```bash
git add main.c
```

### Adicionar vários ficheiros

```bash
git add file1.c file2.c
```

### Adicionar tudo

```bash
git add .
```

⚠️ Atenção: `.` depende do contexto do diretório atual.

---

## 🔍 Visualizar antes de adicionar

```bash
git status
```

Sempre pensa assim:

> “É **isto** que quero eternizar no histórico?”

---

## 🧩 Adição Parcial (Poder Real)

### 🔹 Modo interativo

```bash
git add -i
```

Permite:

* escolher ficheiros
* reverter staged
* adicionar não rastreados
* entrar em modo patch

---

### 🔹 Modo patch (nível Deus)

```bash
git add -p
```

* Adiciona **blocos específicos**
* Ideal para commits limpos
* Base de um histórico profissional

Opções principais:

```
y  → adicionar hunk
n  → ignorar
s  → dividir
e  → editar
```

---

## 🧠 Regra de Ouro

> **Um commit = uma ideia lógica**

`git add -p` é a ferramenta que torna isso possível.

---

## ⚙️ Modos Importantes

### 🔄 Atualizar apenas ficheiros já rastreados

```bash
git add -u
```

* Não adiciona ficheiros novos
* Atualiza modificações e remoções

---

### ➕ Tudo (add + modify + remove)

```bash
git add -A
```

* Sincroniza index com working tree
* Muito usado antes de commits finais

---

### 🚫 Ignorar remoções

```bash
git add --no-all
```

* Adiciona novos e modificados
* Ignora ficheiros apagados

---

## 🧪 Simulação (Dry Run)

```bash
git add -n .
```

Mostra **o que seria adicionado**, sem tocar no index.

---

## 🚧 Trabalhar com ficheiros ignorados

```bash
git add -f segredo.txt
```

⚠️ Use com extrema cautela
Normalmente indica falha no `.gitignore`

---

## 🧠 Intent-to-add (caso avançado)

```bash
git add -N novo.c
```

* Marca o ficheiro no index **sem conteúdo**
* Útil para:

  * `git diff`
  * commits com `-a`

---

## 🔁 Renormalização (CRLF / LF)

```bash
git add --renormalize .
```

Usado quando:

* mudas `core.autocrlf`
* corriges finais de linha
* trabalhas entre Windows ↔ Linux

---

## 🧠 `git add` vs outros comandos

| Comando          | Atua onde            | Função            |
| ---------------- | -------------------- | ----------------- |
| add              | working tree → index | preparar commit   |
| restore --staged | index                | desfazer staging  |
| reset            | index / HEAD         | reescrever estado |
| commit           | index → repo         | criar histórico   |

---

## 🧭 Fluxo Profissional Recomendado

```bash
git status
git diff
git add -p
git status
git commit
```

👉 Repetível, previsível, limpo.

---

## ⚠️ Erros Comuns

* Usar `git add .` sem olhar
* Misturar múltiplas ideias num commit
* Não usar `-p`
* Commitar código não testado
* Confiar no “depois eu arrumo”

---

## 🧠 Filosofia de Engenharia

`git add` não é um comando mecânico.
É um **ato de design do histórico**.

Quem domina `git add`:

* escreve commits claros
* facilita code review
* reduz bugs futuros
* constrói confiança em equipa
* entende Git como sistema de snapshots, não como “backup”

---

## ✅ Em resumo

* `git add` **define o commit**
* O index é um **buffer de intenção**
* `-p` é obrigatório para histórico sério
* Commit bom começa no `add`, não no `commit`
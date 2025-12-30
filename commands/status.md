# 📘 Git Status — Guia de Referência

O comando `git status` é usado para **mostrar o estado atual do diretório de trabalho e do índice**.  
Ele informa quais arquivos estão modificados, quais estão prontos para commit e quais não são rastreados.

---

## 🔑 Função Principal

* Mostrar diferenças entre **working tree**, **index** e **HEAD**.
* Indicar arquivos modificados, adicionados, deletados ou não rastreados.
* Exibir informações sobre branch atual e tracking remoto.
* Servir como guia antes de `git add` e `git commit`.

---

## 🧠 Conceito-Chave: Status = Diagnóstico

* `git status` não altera nada.
* Ele apenas **relata**:
  - O que será commitado.
  - O que pode ser adicionado.
  - O que está fora do controle do Git.

👉 É o comando de inspeção mais usado no fluxo diário.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git status
 ├── compara HEAD com index
 ├── compara index com working tree
 └── lista arquivos não rastreados
```

---

## 📋 Operações Comuns

* `git status` → saída longa e detalhada (default).
* `git status -s` → saída curta (short format).
* `git status -b` → inclui informações de branch.
* `git status --show-stash` → mostra número de entradas no stash.
* `git status -v` → mostra diffs dos arquivos staged.
* `git status -vv` → mostra diffs staged + não staged.
* `git status -uno` → não mostra arquivos não rastreados.
* `git status --ignored` → mostra arquivos ignorados.

---

## 🌿 Exemplos Visuais

### Saída longa

```
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   app.js

Changes not staged for commit:
  (use "git add <file>..." to update)
        modified:   index.html

Untracked files:
  (use "git add <file>..." to include)
        notes.txt
```

### Saída curta (`-s`)

```
M  app.js
 M index.html
?? notes.txt
```

---

## 🔀 Códigos de Status (short format)

* `M` → modificado
* `A` → adicionado
* `D` → deletado
* `R` → renomeado
* `C` → copiado
* `??` → não rastreado
* `!!` → ignorado
* `U` → conflito não resolvido

---

## 🛡️ Modos de Segurança

### Ignorar submódulos

```bash
git status --ignore-submodules=all
```

### Mostrar ignorados

```bash
git status --ignored=matching
```

---

## 📊 Casos de Uso Reais

### Antes de commit

```bash
git status
```

Verificar o que será incluído.

### Em projetos grandes

```bash
git status -uno
```

Evita listar milhares de arquivos não rastreados.

### Debug de conflitos

```bash
git status -s
```

Mostra rapidamente arquivos em conflito.

---

## ⚠️ Armadilhas Clássicas

* Confundir arquivos **não rastreados** com **ignorados**.
* Esquecer que `git status` pode ser lento em grandes repositórios sem cache.
* Não usar `-s` em scripts → saída longa é difícil de parsear.

---

## 🧠 Regra de Ouro

> **Sempre rode `git status` antes de commit ou push.**

---

## ✅ Em resumo

`git status` é o comando para **diagnosticar o estado do repositório**.  
Ele mostra o que está pronto, o que precisa ser adicionado e o que está fora do controle do Git.

Quem entende `git status`:

* evita commits incompletos
* resolve conflitos com clareza
* mantém controle sobre arquivos rastreados e não rastreados
* trabalha com segurança em qualquer fluxo Git
# 📘 Git Stash — Guia de Referência

O comando `git stash` é usado para **guardar temporariamente mudanças não commitadas** e retornar o repositório a um estado limpo.
Ele permite **interromper o trabalho com segurança**, mudar de contexto e retomar exatamente de onde parou — sem poluir o histórico.

---

## 🔑 Função Principal

* Guarda alterações do *working tree* e/ou do *index*.
* Reverte o diretório de trabalho para o estado do `HEAD`.
* Permite aplicar mudanças mais tarde, até sobre outro commit.
* Suporta stashes múltiplos, identificados via `stash@{n}`.
* Funciona como uma *fila de trabalho temporária*.

---

## 🧠 Conceito-Chave: O que é um Stash?

* Um stash é um **commit especial**.
* Contém:

  * Estado do *working tree*
  * Estado do *index*
* Não pertence a nenhum branch.
* Vive em `refs/stash` + reflog.

Visualmente:

```
       .---- W (working tree)
      /    /
-----H----I
```

---

## 📋 Operações Comuns

* `git stash` → guarda mudanças (alias de `git stash push`).
* `git stash list` → lista stashes.
* `git stash show` → mostra resumo.
* `git stash show -p` → mostra diff completo.
* `git stash apply` → reaplica stash.
* `git stash pop` → reaplica e remove stash.
* `git stash drop` → remove stash.
* `git stash clear` → remove todos.

---

## 📦 Criar um Stash

### Básico

```bash
git stash
```

### Com mensagem

```bash
git stash push -m "WIP: refatorar autenticação"
```

### Incluir arquivos não rastreados

```bash
git stash -u
```

### Incluir tudo (até ignorados)

```bash
git stash -a
```

---

## 🎯 Stash Seletivo

### Interativo (por hunks)

```bash
git stash push -p
```

### Apenas staged

```bash
git stash push --staged
```

### Manter index intacto

```bash
git stash push --keep-index
```

> Ideal para **commits parciais e testáveis**.

---

## 🔄 Aplicar um Stash

### Aplicar sem remover

```bash
git stash apply stash@{1}
```

### Aplicar e remover

```bash
git stash pop
```

### Restaurar também o index

```bash
git stash apply --index
```

⚠️ Pode gerar conflitos. Em caso de erro, o stash **não é removido**.

---

## 🌱 Criar Branch a partir de um Stash

```bash
git stash branch feature/recuperar stash@{0}
```

* Cria branch no commit original do stash.
* Aplica mudanças sem conflitos.
* Remove o stash se tudo correr bem.

> Estratégia profissional para stashes antigos.

---

## 📊 Inspeção

### Listar

```bash
git stash list
```

### Ver resumo

```bash
git stash show stash@{0}
```

### Ver patch completo

```bash
git stash show -p
```

### Ver apenas untracked

```bash
git stash show --only-untracked
```

---

## 🗑️ Remoção

### Remover um stash

```bash
git stash drop stash@{2}
```

### Limpar tudo

```bash
git stash clear
```

⚠️ **Irreversível** (exceto via `git fsck`).

---

## 🧪 Casos de Uso Reais

### Pull com working tree suja

```bash
git stash
git pull
git stash pop
```

### Interrupção urgente

```bash
git stash
git commit -a -m "Hotfix crítico"
git stash pop
```

### Commits bem isolados

```bash
git add -p
git stash --keep-index
git commit -m "Parte testada"
git stash pop
```

---

## ⚙️ Configurações Relacionadas

* `stash.showStat`
* `stash.showPatch`
* `stash.showIncludeUntracked`

Controlam como `git stash show` se comporta por padrão.

---

## ⚠️ Boas Práticas

* Não use stash como substituto de commit.
* Dê mensagens descritivas.
* Limpe stashes antigos regularmente.
* Use `stash branch` para recuperar stashes complexos.
* Evite `stash clear` sem backup.

---

## ✅ Em resumo

`git stash` é a **ferramenta de sobrevivência do engenheiro Git**.
Ele permite trocar de contexto sem risco, preservar trabalho inacabado e manter o histórico limpo.
Usado com disciplina, ele transforma caos em fluxo controlado.
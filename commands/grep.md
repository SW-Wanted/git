# 📘 Git Grep — Guia de Referência

O comando `git grep` é usado para **buscar padrões em arquivos rastreados pelo Git**.  
Ele permite localizar rapidamente trechos de código ou texto dentro do histórico e da árvore de trabalho.

---

## 🔑 Função Principal

* Procurar padrões em arquivos versionados.
* Suportar expressões regulares (básicas, estendidas, Perl).
* Mostrar nomes de arquivos, linhas e trechos correspondentes.
* Buscar em commits, index, working tree e submódulos.

---

## 🧠 Conceito-Chave: Grep no Git ≠ Grep do Sistema

* `grep` → busca em arquivos do sistema.
* `git grep` → busca em **arquivos rastreados pelo Git**, com suporte a histórico e pathspecs.

👉 É mais poderoso e integrado ao repositório.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git grep <pattern>
 ├── percorre arquivos rastreados
 ├── aplica regex ou string fixa
 └── mostra correspondências com contexto opcional
```

---

## 📋 Operações Comuns

* `git grep "main()"` → busca padrão em arquivos rastreados.
* `git grep -n "TODO"` → mostra número da linha.
* `git grep -l "error"` → lista apenas nomes de arquivos que contêm o padrão.
* `git grep -c "init"` → conta ocorrências por arquivo.
* `git grep -e "define" --and -e "MAX_PATH"` → combina múltiplos padrões.
* `git grep --recurse-submodules "pattern"` → busca também em submódulos.
* `git grep --cached "pattern"` → busca apenas no índice.
* `git grep --no-index "pattern"` → busca em diretório atual, ignorando Git.

---

## 🌿 Exemplos Visuais

### Buscar função em arquivos `.c` e `.h`

```bash
git grep 'time_t' -- '*.[ch]'
```

### Buscar macro específica

```bash
git grep -e '#define' --and \( -e MAX_PATH -e PATH_MAX \)
```

### Excluir diretório da busca

```bash
git grep solution -- :^Documentation
```

---

## 🔀 Opções Úteis

* `-i` → ignora maiúsculas/minúsculas.
* `-w` → busca apenas palavras inteiras.
* `-v` → inverte correspondência (linhas que **não** casam).
* `-A <n>` → mostra contexto após a linha.
* `-B <n>` → mostra contexto antes da linha.
* `-C <n>` → mostra contexto antes e depois.
* `-p` → mostra nome da função em que o match ocorreu.
* `--color` → destaca correspondências.

---

## 🛡️ Modos de Segurança

### Dry-run não existe aqui  
Mas você pode limitar a busca com **pathspecs**:

```bash
git grep "pattern" -- src/
```

---

## 📊 Casos de Uso Reais

### Encontrar todos os TODOs no código

```bash
git grep -n "TODO"
```

### Localizar função em arquivos específicos

```bash
git grep "connect" -- net/*
```

### Contar ocorrências de palavra

```bash
git grep -c "return"
```

---

## ⚠️ Armadilhas Clássicas

* Usar `grep` do sistema em vez de `git grep`.
* Esquecer que `git grep` só busca em arquivos rastreados (não pega untracked).
* Não usar `--no-index` quando quiser buscar fora do Git.

---

## 🧠 Regra de Ouro

> **Use `git grep` para buscas rápidas e integradas ao repositório.**

---

## ✅ Em resumo

`git grep` é o comando para **localizar padrões em arquivos versionados**.  
Ele é essencial para navegar em grandes bases de código e encontrar rapidamente funções, macros ou comentários.

Quem entende `git grep`:

* encontra código com precisão
* evita buscas manuais demoradas
* controla melhor o repositório
* trabalha com eficiência em projetos colaborativos
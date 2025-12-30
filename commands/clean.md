# 📘 Git Clean — Guia de Referência

O comando `git clean` é usado para **remover arquivos não rastreados** do diretório de trabalho, deixando o repositório em um estado mais limpo e próximo de um clone inicial.

---

## 🔑 Função Principal

* Apagar arquivos e diretórios não rastreados.
* Remover produtos de build, caches e arquivos temporários.
* Restaurar o diretório de trabalho a um estado “pristine”.

---

## 🧠 Conceito-Chave: Clean ≠ Reset

* `git reset` → mexe em commits e histórico.
* `git clean` → mexe apenas em **arquivos não rastreados**.

👉 `git clean` **não altera commits, apenas o diretório de trabalho**.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git clean -f
 ├── identifica arquivos não rastreados
 ├── aplica filtros (--exclude, --x, --X)
 └── remove arquivos/diretórios selecionados
```

---

## 📋 Operações Comuns

* `git clean -n` → mostra o que seria removido (dry-run).
* `git clean -f` → remove arquivos não rastreados.
* `git clean -fd` → remove arquivos **e diretórios** não rastreados.
* `git clean -fx` → remove inclusive arquivos ignorados (ex: build).
* `git clean -fX` → remove apenas arquivos ignorados.
* `git clean -i` → modo interativo (escolher o que apagar).

---

## 🌿 Exemplos Visuais

### Antes do clean

```
repo/
 ├── src/
 ├── build/   (não rastreado)
 ├── temp.log (não rastreado)
```

### Após `git clean -fd`

```
repo/
 ├── src/
```

---

## 🔀 Modo Interativo

```bash
git clean -i
```

Menu de opções:

```
1: clean
2: filter by pattern
3: select by numbers
4: ask each
5: quit
6: help
```

Permite excluir seletivamente arquivos/diretórios.

---

## 🛡️ Modos de Segurança

### Dry-run

```bash
git clean -n
```

Mostra o que seria removido sem apagar nada.

### Excluir por padrão

```bash
git clean -e "*.log"
```

Mantém arquivos `.log` mesmo se não rastreados.

---

## 📊 Casos de Uso Reais

### Limpar produtos de build

```bash
git clean -fx
```

### Resetar diretório para teste de build

```bash
git clean -fdx
```

### Remover apenas arquivos ignorados

```bash
git clean -fX
```

---

## ⚠️ Armadilhas Clássicas

* Usar `git clean -fdx` sem dry-run → pode apagar arquivos importantes.
* Confundir `git clean` com `git reset`.
* Esquecer de configurar `clean.requireForce` → impede execução sem `-f`.

---

## 🧠 Regra de Ouro

> **Sempre use `git clean -n` antes de apagar de verdade.**

---

## ✅ Em resumo

`git clean` é o comando para **limpar o diretório de trabalho**,
removendo arquivos não rastreados e garantindo um ambiente consistente.

Quem entende `git clean`:

* evita sujeira no repositório
* mantém builds reproduzíveis
* controla melhor o ambiente de desenvolvimento

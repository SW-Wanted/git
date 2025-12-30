# 📘 Git MV — Guia de Referência

O comando `git mv` é usado para **mover ou renomear arquivos, diretórios ou symlinks** dentro de um repositório Git.  
Ele atualiza automaticamente o índice para refletir a mudança, mas ainda é necessário fazer commit.

---

## 🔑 Função Principal

* Renomear arquivos versionados.
* Mover arquivos para novos diretórios.
* Atualizar o índice com a nova localização.
* Preparar mudanças para commit.

---

## 🧠 Conceito-Chave: MV ≠ Apenas `mv` do Sistema

* `mv` (do sistema) → apenas move arquivos no disco.
* `git mv` → move **e atualiza o índice**, preparando para commit.

👉 Use `git mv` para manter o histórico consistente.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git mv old.txt new.txt
 ├── move arquivo no diretório de trabalho
 ├── atualiza índice (staging area)
 └── pronto para commit
```

---

## 📋 Operações Comuns

* `git mv old.txt new.txt` → renomeia arquivo.
* `git mv file1 file2 dir/` → move múltiplos arquivos para diretório.
* `git mv -f old.txt new.txt` → força renomeação mesmo se destino existir.
* `git mv -n old.txt new.txt` → mostra o que seria feito (dry-run).
* `git mv -k file1 file2 dir/` → ignora erros e move apenas arquivos válidos.
* `git mv -v old.txt new.txt` → saída detalhada (verbose).

---

## 🌿 Exemplos Visuais

### Antes do `git mv`

```
repo/
 ├── src/
 └── old.txt
```

### Após `git mv old.txt src/new.txt`

```
repo/
 └── src/
      └── new.txt
```

E o índice já reflete a mudança.

---

## 🔀 Submódulos

* `git mv` também atualiza submódulos clonados com gitfile.
* Ajusta automaticamente `.gitmodules` e `core.worktree`.
* Pode deixar diretórios órfãos em mudanças de superprojeto → use `git submodule update`.

---

## 🛡️ Modos de Segurança

### Dry-run

```bash
git mv -n file1 file2
```

Mostra o que seria feito sem executar.

### Forçar

```bash
git mv -f file1 file2
```

Sobrescreve destino existente.

---

## 📊 Casos de Uso Reais

### Renomear arquivo

```bash
git mv README.txt README.md
git commit -m "Renomeia README para Markdown"
```

### Reorganizar diretório

```bash
git mv src/* lib/
git commit -m "Move código de src para lib"
```

### Corrigir nome de submódulo

```bash
git mv old-sub new-sub
git commit -m "Renomeia submódulo"
```

---

## ⚠️ Armadilhas Clássicas

* Usar `mv` em vez de `git mv` → índice não atualizado.
* Esquecer de fazer commit após mover.
* Forçar sobrescrita sem revisar → perda de arquivos.
* Problemas com submódulos se não atualizar corretamente.

---

## 🧠 Regra de Ouro

> **Sempre use `git mv` para renomear ou mover arquivos versionados.**

---

## ✅ Em resumo

`git mv` é o comando para **mover ou renomear arquivos com controle de versão**.  
Ele garante que o índice seja atualizado e que o histórico reflita corretamente a mudança.

Quem entende `git mv`:

* mantém histórico consistente
* evita erros de staging
* organiza melhor o repositório
* trabalha com clareza em projetos colaborativos
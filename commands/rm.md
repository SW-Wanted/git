# 📘 Git RM — Guia de Referência

O comando `git rm` é usado para **remover arquivos do índice (staging area) e do diretório de trabalho**.  
Ele prepara a exclusão de arquivos para o próximo commit, garantindo que o histórico reflita a remoção.

---

## 🔑 Função Principal

* Remover arquivos rastreados do repositório.
* Atualizar o índice e o diretório de trabalho.
* Opcionalmente, remover apenas do índice (`--cached`).
* Preparar exclusões para o próximo commit.

---

## 🧠 Conceito-Chave: RM ≠ Apenas Deletar Arquivos

* `rm` (do sistema) → apaga arquivos do disco, mas Git ainda os vê como **removidos não rastreados**.
* `git rm` → remove arquivos do **índice e do working tree**, registrando a exclusão para commit.

👉 `git rm` garante que a remoção seja parte do histórico.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git rm file.txt
 ├── remove do índice
 ├── remove do diretório de trabalho
 └── marca exclusão para o próximo commit
```

---

## 📋 Operações Comuns

* `git rm file.txt` → remove arquivo do índice e do diretório.
* `git rm -r dir/` → remove diretório e subdiretórios.
* `git rm --cached file.txt` → remove apenas do índice, mantém arquivo no disco.
* `git rm -f file.txt` → força remoção mesmo com alterações não commitadas.
* `git rm -n file.txt` → mostra o que seria removido (dry-run).
* `git rm -q file.txt` → remove silenciosamente (sem output).

---

## 🌿 Exemplos Visuais

### Antes do `git rm`

```
repo/
 ├── src/
 ├── notes.txt (rastreadado)
```

### Após `git rm notes.txt`

```
repo/
 ├── src/
```

E o próximo commit registrará a exclusão de `notes.txt`.

---

## 🔀 Diferença entre `rm` e `git rm`

### Usando `rm` (sistema)

```bash
rm notes.txt
git status
```

Resultado: `notes.txt` aparece como **deleted**, mas precisa ser adicionado com `git add -u`.

### Usando `git rm`

```bash
git rm notes.txt
git commit -m "Remove notes.txt"
```

Resultado: exclusão já preparada para commit.

---

## 🛡️ Modos de Segurança

### Dry-run

```bash
git rm -n *.log
```

Mostra quais arquivos seriam removidos.

### Apenas índice

```bash
git rm --cached config.json
```

Mantém arquivo no disco, mas remove do Git.

---

## 📦 Submódulos

* `git rm` remove submódulos baseados em **gitfile**.
* Atualiza `.gitmodules` automaticamente.
* Para apenas remover checkout local sem commit → use `git submodule deinit`.

---

## 📊 Casos de Uso Reais

### Remover arquivo sensível do Git

```bash
git rm --cached secrets.env
echo "secrets.env" >> .gitignore
git commit -m "Stop tracking secrets.env"
```

### Limpar diretório inteiro

```bash
git rm -r old_docs/
```

### Forçar remoção de arquivo modificado

```bash
git rm -f temp.txt
```

---

## ⚠️ Armadilhas Clássicas

* Usar `rm` em vez de `git rm` → exclusão não registrada.
* Esquecer `--cached` ao remover arquivos que devem permanecer no disco.
* Forçar remoção sem revisar → pode apagar alterações não commitadas.
* Submódulos antigos podem deixar diretórios órfãos.

---

## 🧠 Regra de Ouro

> **Use `git rm` sempre que quiser que a exclusão faça parte do histórico.**

---

## ✅ Em resumo

`git rm` é o comando para **remover arquivos rastreados de forma controlada**, garantindo que a exclusão seja registrada no próximo commit.

Quem entende `git rm`:

* mantém histórico consistente
* evita arquivos sensíveis no repositório
* controla melhor o índice e o working tree
* trabalha com clareza em projetos colaborativos
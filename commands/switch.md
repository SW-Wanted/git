# 📘 Git Switch — Guia de Referência

O comando `git switch` é usado para **mudar de branch** de forma simples e segura.  
Ele atualiza o diretório de trabalho e o índice para refletir o branch escolhido.

---

## 🔑 Função Principal

* Alternar entre branches existentes.
* Criar novos branches e mudar para eles.
* Entrar em modo **detached HEAD** para inspecionar commits.
* Trabalhar com branches remotos de forma automática.

---

## 🧠 Conceito-Chave: Switch ≠ Checkout

* `git checkout` → comando antigo, faz muitas coisas (mudar branch, restaurar arquivos).
* `git switch` → comando novo, focado apenas em **mudar branches**.

👉 Mais simples e menos propenso a erros.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git switch mybranch
 ├── atualiza HEAD para mybranch
 ├── atualiza índice e working tree
 └── novos commits serão adicionados em mybranch
```

---

## 📋 Operações Comuns

* `git switch master` → muda para branch `master`.
* `git switch -` → volta para o branch anterior.
* `git switch -c feature` → cria e muda para branch `feature`.
* `git switch -C feature` → recria branch `feature` a partir de outro ponto.
* `git switch --detach HEAD~3` → inspeciona commit sem branch (detached HEAD).
* `git switch --orphan docs` → cria branch órfão (sem histórico).

---

## 🌿 Exemplos Visuais

### Alternando branches

```
A---B---C master
     \
      D---E topic
```

```bash
git switch topic
```

👉 HEAD passa a apontar para `topic`.

---

## 🔀 Lidando com mudanças locais

* Se houver alterações não commitadas, `git switch` pode falhar.
* Opções disponíveis:
  - `--discard-changes` → descarta alterações locais.
  - `--merge` → tenta mesclar alterações locais com o novo branch.
  - `--conflict=diff3` → controla estilo de conflitos.

---

## 🛡️ Modos de Segurança

### Dry-run não existe aqui  
Mas você pode verificar antes com:

```bash
git status
```

### Forçar mudança

```bash
git switch -f branch
```

Alias para `--discard-changes`.

---

## 📦 Integração com Remotos

* `git switch mybranch` → se não existir localmente, cria a partir de `origin/mybranch`.
* `--guess` → tenta automaticamente encontrar branch remoto correspondente.
* `--no-guess` → desativa esse comportamento.

---

## 📊 Casos de Uso Reais

### Criar branch de correção

```bash
git switch -c fix HEAD~3
```

### Inspecionar commit antigo

```bash
git switch --detach HEAD~5
```

### Criar branch órfão para documentação

```bash
git switch --orphan docs
```

---

## ⚠️ Armadilhas Clássicas

* Confundir `git switch` com `git restore`.
* Esquecer que `--detach` cria HEAD sem branch.
* Usar `-C` sem cuidado → pode sobrescrever branch existente.
* Alterações locais podem ser perdidas com `--discard-changes`.

---

## 🧠 Regra de Ouro

> **Use `git switch` para mudar de branch. Use `git restore` para restaurar arquivos.**

---

## ✅ Em resumo

`git switch` é o comando moderno para **alternar branches**.  
Ele simplifica o fluxo, evita confusões com `git checkout` e oferece opções seguras para lidar com alterações locais.

Quem entende `git switch`:

* alterna branches com confiança
* cria novos branches de forma clara
* inspeciona commits sem bagunçar histórico
* trabalha com repositórios remotos de forma prática

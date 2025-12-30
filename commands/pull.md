# 📘 Git Pull — Guia de Referência

O comando `git pull` é responsável por **sincronizar o branch atual com outro repositório ou branch**, integrando alterações remotas ao histórico local.

Tecnicamente, `git pull` **NÃO é um comando primitivo**:
ele é uma **composição** de dois comandos fundamentais:

```
git pull = git fetch + (git merge | git rebase)
```

---

## 🔑 Função Principal

* Buscar atualizações de um repositório remoto.
* Integrar essas atualizações ao branch atual.
* Resolver divergências via **merge** ou **rebase**.
* Manter o branch local alinhado com o upstream.

---

## 🧠 Conceito-Chave: Pull ≠ Apenas “Atualizar”

Quando você executa `git pull`, você está:

1. **Importando histórico externo**
2. **Alterando o histórico local**
3. **Possivelmente criando commits de merge**
4. **Ou reescrevendo commits (rebase)**

Ou seja:
👉 `git pull` **mexe no grafo de commits**.

---

## 🔍 O que acontece internamente?

Fluxo padrão:

```text
git pull
 ├── git fetch <remote>
 └── git merge  OR  git rebase
```

Se houver:

* **Fast-forward** → apenas move o ponteiro
* **Divergência** → merge ou rebase é necessário

---

## 📋 Operações Comuns

* `git pull` → usa remote e branch configurados.
* `git pull origin main` → pull explícito.
* `git pull --rebase` → integra via rebase.
* `git pull --ff-only` → só fast-forward.
* `git pull --no-rebase` → força merge.

---

## 🌿 Fast-Forward vs Divergência

### Fast-forward (limpo)

```
A---B---C  (origin/main)
     \
      B---C (local)
```

Resultado: apenas move o `HEAD`.

### Histórico divergente

```
A---B---C  origin/main
     \
      D---E local
```

➡️ Precisa decidir: **merge ou rebase**.

---

## 🔀 Merge vs Rebase

### Merge (default tradicional)

```bash
git pull --no-rebase
```

* Cria commit de merge.
* Preserva histórico real.
* Ideal para branches compartilhados.

### Rebase

```bash
git pull --rebase
```

* Reescreve commits locais.
* Histórico linear.
* Ideal para branches pessoais.

⚠️ **Nunca rebase commits já publicados.**

---

## 🧪 Configuração Estratégica

Definir comportamento padrão:

```bash
git config --global pull.rebase true
```

Ou por branch:

```bash
git config branch.main.rebase false
```

---

## 🛡️ Modos de Segurança

### Apenas fast-forward

```bash
git pull --ff-only
```

Falha se houver divergência → **segurança máxima**.

### Autostash

```bash
git pull --autostash
```

* Cria stash temporário
* Faz pull
* Reaplica mudanças locais

⚠️ Pode gerar conflitos ao final.

---

## 📦 Submódulos

```bash
git pull --recurse-submodules
```

* Atualiza commits de submódulos
* Rebase ou merge conforme estratégia

---

## 🧹 Limpeza durante pull

```bash
git pull --prune
```

Remove referências remotas obsoletas antes do fetch.

---

## 📊 Casos de Uso Reais

### Fluxo seguro profissional

```bash
git fetch
git status
git merge origin/main
```

### Pull rápido (branch pessoal)

```bash
git pull --rebase
```

### CI / produção

```bash
git pull --ff-only
```

### Working tree suja

```bash
git pull --autostash
```

---

## ⚠️ Armadilhas Clássicas

* `git pull` sem entender merge vs rebase
* Rebase em branch compartilhado
* Pull com working tree suja
* Histórico poluído com merges desnecessários

---

## 🧠 Regra de Ouro

> **Nunca use `git pull` no automático sem saber qual estratégia está ativa.**

Profissionais usam:

* `git fetch` + ação explícita
  ou
* `git pull` **com flags conscientes**

---

## ✅ Em resumo

`git pull` é um **atalho poderoso**, mas perigoso quando usado sem intenção.
Dominar esse comando significa **entender o grafo de commits**, não apenas atualizar código.

Quem entende `git pull`:

* controla histórico
* evita conflitos
* trabalha bem em equipa
* pensa em Git como sistema distribuído

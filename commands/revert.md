# 📘 Git Revert — Guia de Referência

O comando `git revert` é usado para **desfazer commits de forma segura**, criando **novos commits que anulam alterações anteriores**, **sem reescrever o histórico**.
É o comando **correto e recomendado** quando o histórico já foi compartilhado com outras pessoas.

---

## 🔑 Função Principal

* Reverte alterações introduzidas por commits anteriores.
* Cria **novos commits inversos**, preservando o histórico.
* É **seguro para branches públicos/remotos**.
* Permite reverter commits simples ou merges.
* Mantém rastreabilidade e auditabilidade.

---

## 🧠 Modelo Mental (Essencial)

Enquanto `git reset` **volta no tempo**, `git revert` **anda para frente corrigindo o passado**.

```
A --- B --- C --- D   (histórico)
              |
              ↓
A --- B --- C --- D --- D'
```

👉 `D'` é um **novo commit** que desfaz o efeito de `D`.

---

## 📋 Uso Básico

```bash
git revert <commit>
```

* O working tree deve estar **limpo**.
* Git cria automaticamente um commit de reversão.

---

## ⚙️ Opções Importantes

### 🔹 `--edit` / `--no-edit`

```bash
git revert --edit <commit>
git revert --no-edit <commit>
```

* Controla edição da mensagem de commit.
* Boa prática: **explicar o motivo da reversão**.

---

### 🔹 `-n` / `--no-commit`

```bash
git revert -n <commit>
```

* Aplica a reversão no index e working tree.
* **Não cria commit automaticamente**.
* Ideal para:

  * Reverter vários commits de uma vez.
  * Ajustar manualmente antes de commitar.

---

### 🔹 `-m <parent>` (Reverter Merge)

```bash
git revert -m 1 <merge-commit>
```

* Necessário para commits de merge.
* Define qual parent é o **mainline**.
* Reverter um merge **não é trivial** — altera futuros merges.

📌 Use com extremo cuidado.

---

### 🔹 `-s` / `--signoff`

```bash
git revert -s <commit>
```

* Adiciona `Signed-off-by`.
* Muito usado em projetos open-source e ambientes corporativos.

---

### 🔹 `-S` / `--gpg-sign`

```bash
git revert -S <commit>
```

* Assina criptograficamente o commit de reversão.

---

## 🔁 Revert em Sequência (Sequencer)

Durante conflitos ou múltiplos reverts:

```bash
git revert --continue
git revert --skip
git revert --abort
git revert --quit
```

📌 Mesma lógica do `git cherry-pick`.

---

## 🛠️ Casos de Uso Reais

### ❌ Reverter último commit

```bash
git revert HEAD
```

---

### ❌ Reverter commit específico

```bash
git revert a1b2c3d
```

---

### 🔁 Reverter intervalo de commits (sem commit imediato)

```bash
git revert -n master~5..master~2
git commit
```

---

### ⚠️ Reverter merge problemático

```bash
git revert -m 1 <merge-commit>
```

👉 Apenas se souberes **exatamente** o impacto.

---

## 🧠 Revert vs Reset vs Restore

| Comando | Reescreve histórico | Seguro em remoto | Cria commit |
| ------- | ------------------- | ---------------- | ----------- |
| revert  | ❌ não               | ✅ sim            | ✅ sim       |
| reset   | ✅ sim               | ❌ não            | ❌ não       |
| restore | ❌ não               | ✅ sim            | ❌ não       |

📌 **Regra de ouro**

> Se o commit já foi enviado → **use `git revert`**

---

## 📝 Boas Práticas

* Sempre explique **por que** o commit foi revertido.
* Evite “revert do revert” com mensagens confusas.
* Prefira `revert` em branches compartilhados.
* Teste após a reversão — revert não garante correção lógica.
* Para bugs críticos em produção: `revert` > `reset`.

---

## ⚠️ Armadilhas Comuns

* Reverter merge sem entender o parent.
* Criar cadeias longas de `Revert "Revert ..."` no log.
* Confundir revert com rollback automático de estado.

---

## ✅ Em resumo

`git revert` é o **comando da maturidade** em Git.

Ele preserva:

* histórico
* colaboração
* rastreabilidade
* confiança no repositório

Quem domina `git revert`:

* trabalha bem em equipa
* resolve problemas em produção
* entende Git como sistema distribuído
* pensa em impacto futuro, não só no presente

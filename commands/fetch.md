# 📘 Git Fetch — Guia de Referência

O comando `git fetch` é responsável por **baixar objetos e referências de outro repositório**, mantendo seu repositório local atualizado com o remoto **sem alterar o histórico do seu branch atual**.

Ele é fundamental para **trabalhar de forma segura com repositórios remotos**, pois permite analisar mudanças antes de integrá-las com `merge` ou `rebase`.

---

## 🔑 Função Principal

* Baixar commits, branches e tags de repositórios remotos.
* Atualizar referências de rastreamento remoto (`remote-tracking branches`).
* Preparar o histórico local para integração sem modificar branches locais diretamente.
* Servir como base para `git pull`.

---

## 🧠 Conceito-Chave: Fetch ≠ Pull

Quando você executa `git fetch`, você está **apenas sincronizando seu repositório local com o remoto**, sem:

* Alterar o branch atual.
* Criar commits de merge ou rebase.
* Modificar o histórico local.

Ou seja:
👉 `git fetch` é **uma operação segura e não destrutiva**.

---

## 🔍 O que acontece internamente?

Fluxo padrão:

```text
git fetch <remote>
 └── Baixa objetos e atualiza refs em .git/FETCH_HEAD
````

Se houver branches divergentes:

* Seus branches locais permanecem intactos.
* Você decide quando e como integrar (merge/rebase).

O arquivo `.git/FETCH_HEAD` registra **quais refs foram atualizadas**, permitindo inspeção posterior com `git log FETCH_HEAD`.

---

## 📋 Operações Comuns

* `git fetch` → fetch do remoto padrão (`origin`).
* `git fetch origin` → fetch explícito do `origin`.
* `git fetch --all` → fetch de todos os remotos.
* `git fetch --prune` → remove branches remotas deletadas localmente.
* `git fetch --tags` → busca todas as tags do remoto.
* `git fetch <remote> <branch>` → fetch específico de branch.

---

## 🌿 Fetch vs Pull

| Comando     | O que faz                      | Impacto no branch local |
| ----------- | ------------------------------ | ----------------------- |
| `git fetch` | Baixa histórico do remoto      | Nenhum                  |
| `git pull`  | Baixa + integra (merge/rebase) | Pode alterar histórico  |

⚡ Dica: sempre faça `git fetch` antes de um `merge` ou `rebase` para evitar surpresas.

---

## 🔀 Estratégias de Integração Pós-Fetch

Após um fetch, você pode:

### Merge

```bash
git merge origin/main
```

* Integra mudanças do remoto.
* Mantém histórico divergente.

### Rebase

```bash
git rebase origin/main
```

* Reescreve commits locais.
* Histórico linear.

---

## 🧹 Limpeza com Fetch

* `--prune` → remove referências remotas deletadas.
* `--prune-tags` → remove tags locais que não existem no remoto.
* `--no-tags` → não baixa tags automaticamente.

---

## 🧩 Opções Avançadas

* `--depth=<n>` → fetch superficial, limitado a `n` commits.
* `--shallow-since=<date>` → limita fetch a commits após a data.
* `--recurse-submodules` → busca submódulos modificados.
* `--jobs=<n>` → paraleliza fetch de múltiplos remotos/submódulos.
* `--dry-run` → simula fetch sem alterar nada.
* `--update-head-ok` → permite atualizar o HEAD do branch atual (usado internamente pelo pull).

---

## 📊 Casos de Uso Reais

### Sincronização segura

```bash
git fetch
git log ..origin/main
```

### Atualizando todos os remotos

```bash
git fetch --all --prune
```

### Atualizando submódulos

```bash
git fetch --recurse-submodules
```

### Trabalhando com shallow repositories

```bash
git fetch --depth=10
git fetch --deepen=5
git fetch --unshallow
```

---

## ⚠️ Armadilhas Clássicas

* Acreditar que `fetch` altera o branch atual.
* Ignorar `--prune` → acumulação de referências obsoletas.
* Confundir fetch superficial (`--depth`) com histórico completo.

---

## ✅ Em resumo

`git fetch` é **o comando mais seguro para sincronizar seu repositório com remotos**.
Ele permite que você:

* Veja o que mudou antes de integrar.
* Mantenha seu histórico local intacto.
* Trabalhe de forma colaborativa sem surpresas.

> Profissionais de Git usam: `git fetch` regularmente e só integram após inspeção consciente.

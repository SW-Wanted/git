# 📘 Git Merge — Guia de Referência

O comando `git merge` é usado para **combinar histórias de desenvolvimento de diferentes branches**. Ele é uma ferramenta essencial para integrar alterações locais e remotas, e também é a base do `git pull`.

Tecnicamente, `git merge` **não cria magia**, ele apenas:

`git merge <branch>` = pega alterações desde o ponto de divergência e integra no branch atual


---

## 🔑 Função Principal

* Integrar mudanças de outro branch no branch atual.
* Manter histórico de commits consistente.
* Resolver divergências automaticamente ou manualmente.
* Permitir estratégias de merge personalizadas (merge commit, fast-forward, squash).

---

## 🧠 Conceito-Chave: Merge ≠ Apenas “Juntar Código”

Quando você executa `git merge`, você está:

1. Pegando commits de outro branch.
2. Incorporando-os no seu branch atual.
3. Criando **um novo commit de merge** (dependendo da estratégia).
4. Possivelmente enfrentando conflitos a resolver.

Ou seja:
👉 `git merge` **modifica o grafo de commits**.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git merge <branch>
 ├── identifica ponto de divergência (merge base)
 ├── compara diferenças
 └── aplica alterações no branch atual
      ├─ sucesso automático → fast-forward ou merge commit
      └─ conflito → resolução manual necessária
````

Se houver:

* **Fast-forward** → apenas move o ponteiro
* **Divergência** → merge commit ou rebase necessário

---

## 📋 Operações Comuns

* `git merge <branch>` → merge padrão.
* `git merge --no-ff <branch>` → força commit de merge mesmo se fast-forward.
* `git merge --ff-only <branch>` → só permite fast-forward.
* `git merge --squash <branch>` → aplica alterações sem criar merge commit.
* `git merge --abort` → cancela merge em conflito.
* `git merge --continue` → continua merge interrompido.

---

## 🌿 Fast-Forward vs Histórico Divergente

### Fast-forward (simples)

```
A---B---C  (origin/main)
     \
      D local
```

Resultado: apenas move o `HEAD`.

### Histórico divergente

```
A---B---C origin/main
     \
      D---E local
```

➡️ Necessário merge commit ou rebase.

---

## 🔀 Estratégias de Merge

### Merge padrão (commit)

```bash
git merge <branch>
```

* Cria commit de merge.
* Preserva histórico real.
* Ideal para branches compartilhados.

### Fast-forward

```bash
git merge --ff-only <branch>
```

* Só avança ponteiro se possível.
* Histórico linear.
* Seguro para CI/produção.

### Squash

```bash
git merge --squash <branch>
git commit
```

* Junta alterações em **um único commit**.
* Não preserva histórico detalhado.
* Útil para integração limpa antes de merge final.

---

## ⚡ Resolução de Conflitos

Durante conflitos, Git usa **três versões**:

```text
<<<<<<< HEAD
versão local
||||||| base
versão base
=======
versão remota
>>>>>>> branch
```

### Passos para resolver

1. Editar arquivos manualmente.
2. `git add <arquivo>` para marcar resolvido.
3. `git merge --continue` para finalizar.

Ferramentas de merge gráfico:

* `git mergetool` → usa GUI configurada (Meld, KDiff3, VSCode, etc.)
* `git diff` → ver diferenças detalhadas
* `git log --merge -p` → histórico de alterações conflitantes

---

## 🧪 Configurações Úteis

* `merge.ff` → controla fast-forward por padrão (`true`, `false`, `only`).
* `merge.tool` → define ferramenta de merge (`meld`, `vimdiff`, `vscode`).
* `merge.autostash` → stasha mudanças sujas antes do merge.

---

## 📊 Casos de Uso Reais

### Fluxo seguro profissional

```bash
git fetch
git status
git merge origin/main
```

### Merge rápido (branch pessoal)

```bash
git merge --ff-only origin/main
```

### Squash antes de integrar feature

```bash
git merge --squash feature-branch
git commit -m "Integra feature"
```

### Conflitos em working tree suja

```bash
git merge --autostash <branch>
```

---

## ⚠️ Armadilhas Clássicas

* Merge sem entender fast-forward vs commit.
* Merge em branch compartilhado sem coordenação.
* Merge com working tree suja.
* Squash inadvertido que destrói histórico detalhado.

---

## 🧠 Regra de Ouro

> **Sempre escolha a estratégia consciente antes de dar merge.**

Profissionais preferem:

* `git fetch` + merge explícito
* Merge com flags claras (`--no-ff`, `--squash`, `--ff-only`)

---

## ✅ Em resumo

`git merge` é **o coração da integração de branches**.
Dominar este comando significa **controlar o grafo de commits**, resolver conflitos com segurança e manter o fluxo de trabalho limpo e linear.

Quem domina `git merge`:

* evita conflitos inesperados
* mantém histórico organizado
* trabalha bem em equipe
* pensa Git como um sistema distribuído
# 📘 Git Rebase — Guia de Referência

O comando `git rebase` é usado para **reaplicar commits em cima de outro base tip**, reescrevendo o histórico para manter uma linha de commits mais limpa e linear.

Tecnicamente, `git rebase` **não mescla diretamente**:
ele **move commits** para uma nova base, recriando-os.

---

## 🔑 Função Principal

* Reaplicar commits de um branch sobre outro.
* Manter histórico linear e organizado.
* Remover ou editar commits durante o processo.
* Substituir merges por uma sequência de commits reescritos.

---

## 🧠 Conceito-Chave: Rebase = Reescrever Histórico

Quando você executa `git rebase`, você está:

1. **Resetando o branch atual** para a nova base.
2. **Reaplicando commits** um por um.
3. **Possivelmente pulando commits duplicados**.
4. **Resolvendo conflitos manualmente, se necessário**.

👉 `git rebase` **recria commits e altera o grafo**.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git rebase <upstream>
 ├── salva commits locais temporariamente
 ├── reseta HEAD para <upstream>
 └── reaplica commits um a um
```

Se houver:

* **Commits duplicados** → são ignorados.
* **Conflitos** → você resolve e continua.

---

## 📋 Operações Comuns

* `git rebase master` → rebase branch atual sobre `master`.
* `git rebase master topic` → troca para `topic` e rebase sobre `master`.
* `git rebase --onto master next topic` → muda base de `topic` de `next` para `master`.
* `git rebase --interactive` → editar, reordenar, squash ou remover commits.
* `git rebase --continue` → continuar após resolver conflitos.
* `git rebase --abort` → cancelar e voltar ao estado inicial.
* `git rebase --skip` → pular commit problemático.

---

## 🌿 Exemplo Visual

### Antes do rebase

```
A---B---C topic
     /
D---E---F master
```

### Após `git rebase master`

```
A'--B'--C' topic
     /
D---E---F master
```

---

## 🔀 Rebase vs Merge

### Merge

```bash
git merge master
```

* Cria commit de merge.
* Preserva histórico divergente.

### Rebase

```bash
git rebase master
```

* Reescreve commits locais.
* Histórico linear.
* Mais fácil de ler, mas altera hashes.

⚠️ **Nunca rebase commits já publicados em branches compartilhados.**

---

## 🧪 Configuração Estratégica

Definir comportamento padrão para pull com rebase:

```bash
git config --global pull.rebase true
```

Ou por branch:

```bash
git config branch.topic.rebase true
```

---

## 🛡️ Modos de Segurança

### Abortando rebase

```bash
git rebase --abort
```

Volta ao estado inicial.

### Pulando commit problemático

```bash
git rebase --skip
```

Ignora commit atual.

### Continuando após conflito

```bash
git rebase --continue
```

Após resolver conflitos e `git add`.

---

## ✨ Rebase Interativo

```bash
git rebase -i HEAD~5
```

Permite:

* Reordenar commits.
* Squash (juntar commits).
* Reword (editar mensagens).
* Drop (remover commits).

---

## 📊 Casos de Uso Reais

### Limpar histórico antes de PR

```bash
git rebase -i origin/main
```

### Mudar base de branch

```bash
git rebase --onto master next topic
```

### Remover commits problemáticos

```bash
git rebase --onto topicA~5 topicA~3 topicA
```

---

## ⚠️ Armadilhas Clássicas

* Rebase em branch compartilhado → quebra histórico.
* Conflitos não resolvidos corretamente.
* Perder commits ao usar `--skip` sem atenção.
* Alterar hashes de commits já revisados.

---

## 🧠 Regra de Ouro

> **Use `git rebase` para manter histórico limpo, mas nunca em branches compartilhados.**

---

## ✅ Em resumo

`git rebase` é uma ferramenta poderosa para **reescrever histórico** e manter um grafo linear.
Dominar esse comando significa **controlar commits com precisão** e evitar poluição no histórico.

Quem entende `git rebase`:

* mantém histórico limpo
* evita merges desnecessários
* facilita revisão de código
* trabalha com clareza em projetos colaborativos

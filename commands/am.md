# 📘 Git Am — Guia de Referência

O comando `git am` é usado para **aplicar uma série de patches vindos de uma mailbox** diretamente em um branch.  
Ele é o inverso de `git format-patch`: enquanto `format-patch` gera patches a partir de commits, `git am` pega esses patches e os transforma novamente em commits.

---

## 🔑 Função Principal

* Ler mensagens de e-mail contendo patches.
* Extrair autor, data, mensagem e diffs.
* Criar commits correspondentes no branch atual.
* Automatizar integração de contribuições enviadas por e-mail.

---

## 🧠 Conceito-Chave: Am = Apply Mailbox

* `git am` divide mensagens em:
  - **Metadados** (autor, data, assunto).
  - **Mensagem de commit**.
  - **Patch** (diff).
* Aplica cada patch como um commit novo.

👉 É essencial em fluxos de contribuição via e-mail.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git am patches.mbox
 ├── lê mensagens da mailbox
 ├── extrai autor, data e assunto
 ├── aplica diffs como commits
 └── continua até aplicar todos os patches
```

---

## 📋 Operações Comuns

* `git am series.mbox` → aplica patches de um arquivo mbox.
* `git am --signoff series.mbox` → adiciona trailer "Signed-off-by".
* `git am --3way series.mbox` → usa merge 3-way se patch não aplicar limpo.
* `git am --skip` → pula patch problemático.
* `git am --continue` → continua após resolver conflito manualmente.
* `git am --abort` → cancela operação e restaura branch.
* `git am --show-current-patch` → mostra patch que causou conflito.

---

## 🌿 Exemplos Visuais

### Aplicar patches recebidos por e-mail

```bash
git am patches.mbox
```

### Resolver conflito e continuar

```bash
# edite arquivos e resolva conflito
git add .
git am --continue
```

### Pular patch problemático

```bash
git am --skip
```

---

## 🔀 Opções Úteis

* `--signoff` → adiciona "Signed-off-by".
* `--3way` → tenta merge 3-way em caso de conflito.
* `--ignore-whitespace` → ignora diferenças de espaço.
* `--patch-format=<format>` → força formato (mbox, stgit, hg).
* `--message-id` → adiciona cabeçalho Message-ID ao commit.
* `--gpg-sign` → assina commits com GPG.

---

## 📊 Casos de Uso Reais

### Integrar contribuições enviadas por e-mail

```bash
git am contrib-patches.mbox
```

### Usar merge 3-way para aplicar patch difícil

```bash
git am --3way fix-bug.mbox
```

### Cancelar operação

```bash
git am --abort
```

---

## ⚠️ Armadilhas Clássicas

* Aplicar patches no branch errado → sempre confira com `git status`.
* Esquecer de usar `--signoff` em projetos que exigem DCO.
* Não resolver conflitos corretamente antes de `--continue`.
* Misturar patches de formatos diferentes sem especificar `--patch-format`.

---

## 🧠 Regra de Ouro

> **Use `git am` para transformar patches recebidos em commits reais.  
> Combine com `git format-patch` para fluxos de contribuição via e-mail.**

---

## ✅ Em resumo

`git am` é o comando para **aplicar patches de mailbox como commits**.  
Ele é fundamental em projetos que usam fluxo de contribuição por e-mail.

Quem entende `git am`:

* integra patches com precisão
* resolve conflitos com segurança
* mantém histórico limpo e confiável
* colabora em projetos distribuídos com eficiência
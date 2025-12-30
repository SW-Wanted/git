# 📘 Git Cherry-Pick — Guia de Referência

O comando `git cherry-pick` é usado para **aplicar as mudanças introduzidas por commits existentes** em outro branch.  
Ele cria novos commits com o mesmo conteúdo, permitindo trazer correções ou features específicas sem precisar mesclar todo o histórico.

---

## 🔑 Função Principal

* Copiar mudanças de commits específicos para o branch atual.
* Criar novos commits com base em commits já existentes.
* Facilitar backports (aplicar correções de branches novos em versões antigas).
* Selecionar mudanças pontuais sem fazer merge completo.

---

## 🧠 Conceito-Chave: Cherry-Pick = Escolher a Dedo

* `git merge` → junta históricos inteiros.
* `git cherry-pick` → aplica **apenas commits escolhidos**.
* Útil para trazer correções específicas sem trazer todo o branch.

👉 É como “colher cerejas” do histórico: você pega só o que precisa.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git cherry-pick <commit>
 ├── aplica mudanças do commit
 ├── cria novo commit no branch atual
 └── mantém autor e mensagem (editável)
```

---

## 📋 Operações Comuns

* `git cherry-pick <hash>` → aplica commit específico.
* `git cherry-pick master~2` → aplica o penúltimo commit da branch master.
* `git cherry-pick A B C` → aplica múltiplos commits em sequência.
* `git cherry-pick -n <hash>` → aplica mudanças sem criar commit (útil para agrupar).
* `git cherry-pick --edit <hash>` → permite editar mensagem de commit.
* `git cherry-pick --signoff <hash>` → adiciona trailer "Signed-off-by".
* `git cherry-pick --ff ..next` → fast-forward se possível.
* `git cherry-pick --abort` → cancela operação.
* `git cherry-pick --continue` → continua após resolver conflitos.
* `git cherry-pick --skip` → pula commit problemático.

---

## 🌿 Exemplos Visuais

### Aplicar commit específico

```bash
git cherry-pick 1a2b3c4
```

### Aplicar múltiplos commits

```bash
git cherry-pick master~4 master~2
```

### Resolver conflito e continuar

```bash
# edite arquivos e resolva conflito
git add .
git cherry-pick --continue
```

---

## 🔀 Opções Úteis

* `-n` / `--no-commit` → aplica mudanças sem criar commit.
* `-x` → adiciona linha “(cherry picked from commit …)” na mensagem.
* `-m <parent>` → necessário para cherry-pick de merges (define qual pai usar).
* `--allow-empty` → permite commits vazios.
* `--allow-empty-message` → permite commits sem mensagem.
* `--empty=drop|keep|stop` → controla commits redundantes.
* `--strategy=<strategy>` → define estratégia de merge.
* `-X<option>` → passa opções específicas para estratégia.

---

## 📊 Casos de Uso Reais

### Backport de correção

```bash
git checkout release-1.0
git cherry-pick fix-commit-hash
```

### Agrupar múltiplos commits em um só

```bash
git cherry-pick -n commit1 commit2 commit3
git commit -m "Agrupa correções"
```

### Cancelar cherry-pick com conflito

```bash
git cherry-pick --abort
```

---

## ⚠️ Armadilhas Clássicas

* Cherry-pick de merges sem `-m` → erro.
* Esquecer de resolver conflitos antes de `--continue`.
* Usar cherry-pick em excesso → histórico pode ficar confuso.
* Não usar `-x` em backports → difícil rastrear origem do commit.

---

## 🧠 Regra de Ouro

> **Use `git cherry-pick` para trazer commits específicos.  
> Use `git merge` ou `git rebase` para fluxos completos.**

---

## ✅ Em resumo

`git cherry-pick` é o comando para **aplicar commits escolhidos em outro branch**.  
Ele é essencial para backports, correções pontuais e seleção de mudanças específicas.

Quem entende `git cherry-pick`:

* aplica commits com precisão
* resolve conflitos com segurança
* mantém histórico rastreável
* trabalha com eficiência em fluxos complexos
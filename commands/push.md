# 📘 Git Push — Guia de Referência

O comando `git push` é usado para **enviar commits locais para um repositório remoto**, atualizando referências (branches, tags) e compartilhando seu trabalho com outros.

---

## 🔑 Função Principal

* Atualizar branches remotos com commits locais.
* Criar novos branches ou tags no remoto.
* Deletar referências remotas.
* Sincronizar histórico entre local e remoto.

---

## 🧠 Conceito-Chave: Push = Publicar Histórico

Quando você executa `git push`, você está:

1. **Selecionando um repositório remoto** (ex: `origin`).
2. **Definindo quais refs enviar** (branch/tag).
3. **Transmitindo objetos necessários** (commits, blobs, trees).
4. **Atualizando ponteiros remotos**.

👉 `git push` **torna seus commits visíveis para outros**.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git push origin main
 ├── verifica commits locais vs remotos
 ├── envia objetos faltantes
 └── atualiza refs no servidor
```

Se houver:

* **Fast-forward** → remoto avança sem perder histórico.
* **Non-fast-forward** → rejeição, a menos que force (`--force`).

---

## 📋 Operações Comuns

* `git push` → envia branch atual para remoto configurado.
* `git push origin main` → envia explicitamente `main` para `origin`.
* `git push -u origin main` → define upstream (tracking branch).
* `git push --tags` → envia todas as tags.
* `git push --delete origin branch` → remove branch remoto.
* `git push --all` → envia todos os branches locais.
* `git push --mirror` → espelha todas as refs (branches + tags).

---

## 🌿 Fast-Forward vs Non-Fast-Forward

### Fast-forward (permitido)

```
A---B---C local
     \
      A---B remote
```

Resultado: remoto avança para incluir `C`.

### Non-fast-forward (rejeitado por padrão)

```
A---B---C local
     \
      A---D remote
```

➡️ Push rejeitado para evitar perda de histórico.

---

## 🔀 Forçar Push

### Force simples

```bash
git push --force origin main
```

* Substitui histórico remoto.
* ⚠️ Pode apagar commits de outros.

### Force seguro (lease)

```bash
git push --force-with-lease origin main
```

* Só força se remoto não mudou desde seu último fetch.
* Mais seguro em colaboração.

---

## 🧪 Configuração Estratégica

Definir comportamento padrão:

```bash
git config --global push.default simple
```

Modos disponíveis:

* `simple` → branch atual para upstream (default).
* `current` → branch atual para remoto com mesmo nome.
* `upstream` → branch atual para seu upstream configurado.
* `matching` → todos os branches com mesmo nome.
* `nothing` → não envia nada sem refspec explícito.

---

## 🛡️ Modos de Segurança

### Dry-run

```bash
git push --dry-run
```

Simula push sem enviar nada.

### Atomic

```bash
git push --atomic origin main dev
```

Ou tudo é atualizado, ou nada.

### Signed Push

```bash
git push --signed
```

Assina push com GPG.

---

## 📦 Submódulos

```bash
git push --recurse-submodules=on-demand
```

* Garante que commits de submódulos também sejam enviados.

---

## 📊 Casos de Uso Reais

### Publicar branch novo

```bash
git push -u origin feature/login
```

### Enviar todas as tags

```bash
git push --tags
```

### Remover branch remoto

```bash
git push --delete origin old-feature
```

### Espelhar repositório

```bash
git push --mirror
```

---

## ⚠️ Armadilhas Clássicas

* Usar `--force` sem cuidado → perda de histórico.
* Push em branch errado por falta de upstream configurado.
* Esquecer de enviar tags importantes.
* Push automático sem verificar conflitos.

---

## 🧠 Regra de Ouro

> **Sempre saiba o que está sendo enviado antes de usar `git push`.**

Profissionais usam:

* `git push --dry-run` para verificar.
* `--force-with-lease` em vez de `--force`.
* Configurações explícitas para evitar surpresas.

---

## ✅ Em resumo

`git push` é o comando que **publica seu trabalho**.
Dominar suas opções significa **controlar o que vai para o remoto** e evitar perdas de histórico.

Quem entende `git push`:

* compartilha código com segurança
* evita sobrescrever trabalho alheio
* mantém branches e tags organizados
* trabalha de forma colaborativa e responsável
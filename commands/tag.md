# 📘 Git Tag — Guia de Referência

O comando `git tag` é usado para **criar, listar, deletar ou verificar tags** em um repositório Git.  
Tags são marcadores que apontam para commits específicos, geralmente usados para marcar versões de release.

---

## 🔑 Função Principal

* Criar tags **leves** (apenas um nome para um commit).
* Criar tags **anotadas** (com mensagem, autor, data e assinatura opcional).
* Listar tags existentes.
* Deletar tags.
* Verificar assinaturas GPG em tags.

---

## 🧠 Conceito-Chave: Tipos de Tags

* **Lightweight tag** → apenas um ponteiro para um commit.
* **Annotated tag** → contém metadados (autor, data, mensagem, assinatura GPG).
  - Usada para releases oficiais.
  - Reconhecida por comandos como `git describe`.

👉 Use **annotated tags** para versões públicas e **lightweight tags** para uso interno.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git tag v1.0.0
 ├── cria referência em refs/tags/v1.0.0
 └── aponta para commit atual (HEAD)
```

---

## 📋 Operações Comuns

* `git tag v1.0.0` → cria tag leve no commit atual.
* `git tag -a v1.0.0 -m "Release 1.0.0"` → cria tag anotada com mensagem.
* `git tag -s v1.0.0 -m "Release 1.0.0"` → cria tag assinada com GPG.
* `git tag -l` → lista todas as tags.
* `git tag -l "v-*"` → lista tags que começam com `v-`.
* `git tag -d v1.0.0` → deleta tag local.
* `git tag -v v1.0.0` → verifica assinatura GPG da tag.

---

## 🌿 Exemplos Visuais

### Criando tag anotada

```bash
git tag -a v2.0.0 -m "Versão 2.0 estável"
```

Resultado: tag `v2.0.0` com mensagem e metadados.

### Listando tags

```bash
git tag --sort=version:refname
```

Ordena tags por versão semântica.

---

## 🔀 Re-tagging (Corrigir tags)

* Se **não publicou** a tag → recrie com `-f`.
* Se **já publicou** → crie nova tag (`v1.0.1`) ou avise publicamente que retaggeou.

⚠️ Alterar tags já publicadas pode causar inconsistência entre colaboradores.

---

## 🛡️ Modos de Segurança

### Verificar assinatura

```bash
git tag -v v1.0.0
```

Confirma autenticidade da tag.

### Forçar recriação

```bash
git tag -f v1.0.0 HEAD~2
```

Reaponta tag para commit anterior.

---

## 📊 Casos de Uso Reais

### Marcar release oficial

```bash
git tag -a v3.0.0 -m "Release 3.0.0"
git push origin v3.0.0
```

### Criar tag leve para teste interno

```bash
git tag temp-build
```

### Deletar tag remota

```bash
git push origin --delete v2.0.0
```

---

## ⚠️ Armadilhas Clássicas

* Alterar tags já publicadas sem aviso.
* Usar lightweight tags para releases → ignoradas por `git describe`.
* Esquecer de assinar tags em projetos que exigem verificação GPG.

---

## 🧠 Regra de Ouro

> **Use tags anotadas para releases. Lightweight tags são apenas marcadores temporários.**

---

## ✅ Em resumo

`git tag` é o comando para **marcar commits importantes**.  
Ele organiza versões, facilita releases e garante autenticidade com assinaturas GPG.

Quem entende `git tag`:

* controla versões com clareza
* evita confusões em releases
* garante confiança no histórico
* trabalha de forma profissional em projetos colaborativos
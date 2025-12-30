# 📘 Git Clone — Guia de Referência

O comando `git clone` é usado para **criar uma cópia de um repositório existente** em um novo diretório.  
Ele baixa todos os objetos, referências e configurações necessárias para começar a trabalhar localmente.

---

## 🔑 Função Principal

* Copiar um repositório remoto ou local.
* Configurar automaticamente o `origin` como remoto padrão.
* Criar branches locais e remotos.
* Preparar ambiente para desenvolvimento colaborativo.

---

## 🧠 Conceito-Chave: Clone = Novo Repositório

* `git clone` cria um **novo diretório** com histórico completo (ou parcial, se filtrado).
* Configura `origin` para apontar para o repositório original.
* Permite começar a trabalhar imediatamente no branch padrão.

👉 É o primeiro passo em qualquer fluxo Git colaborativo.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git clone <repo> <dir>
 ├── cria diretório <dir>
 ├── copia objetos e refs
 ├── configura remoto origin
 └── faz checkout do branch inicial
```

---

## 📋 Operações Comuns

* `git clone https://github.com/user/repo.git` → clona repositório remoto.
* `git clone /path/to/repo` → clona repositório local.
* `git clone -b dev https://github.com/user/repo.git` → clona e muda para branch `dev`.
* `git clone --bare repo.git` → cria clone bare (sem working tree).
* `git clone --mirror repo.git` → espelha todos os refs (branches, tags, remotes).
* `git clone --depth=1 https://github.com/user/repo.git` → clone raso (shallow), apenas último commit.
* `git clone --filter=blob:none https://github.com/user/repo.git` → clone parcial, sem blobs.

---

## 🌿 Exemplos Visuais

### Clone normal

```
repo.git (remoto)
   |
   └── clone → diretório local com histórico completo
```

### Clone raso (`--depth=1`)

```
repo.git (remoto)
   |
   └── clone → apenas último commit
```

---

## 🔀 Opções Úteis

* `-o <name>` → define nome do remoto (default: origin).
* `--separate-git-dir=<dir>` → separa `.git` em outro diretório.
* `--sparse` → ativa sparse-checkout.
* `--recurse-submodules` → clona também submódulos.
* `--shallow-since=<date>` → clone raso a partir de data.
* `--shallow-exclude=<ref>` → exclui commits de referência.

---

## 📊 Casos de Uso Reais

### Clonar repositório para desenvolvimento

```bash
git clone https://github.com/org/project.git
```

### Criar clone bare para servidor central

```bash
git clone --bare project.git /srv/git/project.git
```

### Criar clone raso para economizar espaço

```bash
git clone --depth=1 https://github.com/org/project.git
```

### Clonar com submódulos

```bash
git clone --recurse-submodules https://github.com/org/project.git
```

---

## ⚠️ Armadilhas Clássicas

* Usar clone raso e depois precisar de histórico completo.
* Confundir `--bare` com clone normal → bare não tem working tree.
* Esquecer de clonar submódulos → projeto incompleto.
* Alterar remoto sem configurar corretamente `origin`.

---

## 🧠 Regra de Ouro

> **Use `git clone` para começar a trabalhar em um repositório.  
> Escolha opções conforme necessidade (bare, mirror, shallow, sparse).**

---

## ✅ Em resumo

`git clone` é o comando para **copiar repositórios** e iniciar colaboração.  
Ele configura ambiente local com histórico, refs e remoto padrão.

Quem entende `git clone`:

* escolhe o tipo de clone adequado
* evita problemas com histórico incompleto
* organiza melhor ambientes de trabalho
* trabalha com eficiência em projetos distribuídos
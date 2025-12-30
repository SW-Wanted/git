# 📘 Git Init — Guia de Referência

O comando `git init` é usado para **criar um novo repositório Git** ou **re-inicializar um existente**.  
Ele configura a estrutura básica necessária para começar a versionar arquivos.

---

## 🔑 Função Principal

* Criar um novo repositório vazio.
* Re-inicializar um repositório existente sem sobrescrever dados.
* Configurar branch inicial e diretórios internos.
* Preparar ambiente para controle de versão.

---

## 🧠 Conceito-Chave: Init = Ponto de Partida

* `git init` cria a pasta `.git` com subdiretórios e arquivos de configuração.
* Define branch inicial (por padrão `master`, mas pode ser alterado).
* Permite começar a rastrear arquivos com `git add` e `git commit`.

👉 É o primeiro passo para transformar qualquer pasta em um repositório Git.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git init
 ├── cria diretório .git
 ├── adiciona subdiretórios (objects, refs, hooks, etc.)
 ├── define branch inicial
 └── prepara ambiente para commits
```

---

## 📋 Operações Comuns

* `git init` → cria repositório vazio no diretório atual.
* `git init myproject` → cria repositório em novo diretório `myproject`.
* `git init --bare` → cria repositório bare (sem working tree).
* `git init --initial-branch=main` → define branch inicial como `main`.
* `git init --template=/usr/share/git-core/templates` → usa diretório de templates.
* `git init --separate-git-dir=/path/to/repo.git` → separa `.git` em outro local.
* `git init --shared=group` → cria repositório compartilhado entre usuários do mesmo grupo.

---

## 🌿 Exemplos Visuais

### Repositório vazio

```
myproject/
 └── .git/
      ├── objects/
      ├── refs/
      ├── HEAD
      └── config
```

---

## 🔀 Opções Úteis

* `--bare` → repositório sem working tree (usado em servidores).
* `--initial-branch=<name>` → define nome do branch inicial.
* `--object-format=sha256` → usa SHA-256 em vez de SHA-1.
* `--ref-format=reftable` → usa formato experimental de refs.
* `--shared` → configura permissões para uso colaborativo.

---

## 📊 Casos de Uso Reais

### Criar repositório local

```bash
mkdir projeto
cd projeto
git init
```

### Criar repositório bare para servidor

```bash
git init --bare /srv/git/projeto.git
```

### Definir branch inicial como `main`

```bash
git init --initial-branch=main
```

---

## ⚠️ Armadilhas Clássicas

* Confundir `git init` com `git clone` → `init` cria repositório vazio, `clone` copia existente.
* Esquecer de configurar branch inicial → pode gerar divergências (`master` vs `main`).
* Usar `--bare` sem necessidade → não terá working tree para editar arquivos.
* Não configurar permissões em repositórios compartilhados.

---

## 🧠 Regra de Ouro

> **Use `git init` para começar um repositório do zero.  
> Use `git clone` para copiar um já existente.**

---

## ✅ Em resumo

`git init` é o comando para **inicializar repositórios Git**.  
Ele cria a estrutura interna e define o branch inicial, permitindo começar a versionar arquivos.

Quem entende `git init`:

* sabe quando criar repositórios locais ou bare
* evita confusões entre init e clone
* configura corretamente branches e permissões
* trabalha com clareza em projetos colaborativos
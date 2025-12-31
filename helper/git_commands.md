# 📘 Git Comandos

Os comandos do git podem ser agrupados em:
- **[🔑 Main Porcelain Commands](#-main-porcelain-commands)**
- **[🛠 Ancillary Commands / Manipulators](#-ancillary-commands--manipulators)**
- **[🔍 Ancillary Commands / Interrogators](#-ancillary-commands--interrogators)**
- **[🌐 Interacting with Others](#-interacting-with-others)**
- **[⚙️ Low-level Commands](#️-low-level-commands)**
- **[🔧 Low-level Syncing & Helpers](#-low-level-syncing--helpers)**
- **[📂 Interfaces e Arquivos](#-interfaces-e-arquivos)**
- **[👨‍💻 Interfaces para Desenvolvedores](#-interfaces-para-desenvolvedores)**
- **[🔗 Comandos Externos](#-comandos-externos)**
---

## 🔑 Main Porcelain Commands
Comandos de alto nível usados no dia a dia:

- [git add](./../commands/add.md) → adiciona conteúdo de arquivos ao índice (staging).
- [git commit](./../commands/commit.md) → registra mudanças no repositório.
- [git branch](./../commands/branch.md) → lista, cria ou exclui branches.
- [git checkout](./../commands/checkout.md) → alterna branches ou restaura arquivos da árvore de trabalho.
- [git switch](./../commands/switch.md) → alterna branches (alternativa moderna ao checkout).
- [git merge](./../commands/merge.md) → une históricos de desenvolvimento.
- [git rebase](./../commands/rebase.md) → reaplica commits sobre outro ponto base.
- [git clone](./../commands/clone.md) → clona um repositório em um novo diretório.
- [git pull](./../commands/pull.md) → busca e integra alterações de outro repositório.
- [git push](./../commands/push.md) → envia commits para um repositório remoto.
- [git status](./../commands/status.md) → mostra o estado da árvore de trabalho.
- [git log](./../commands/log.md) → exibe histórico de commits.
- [git diff](./../commands/diff.md) → mostra diferenças entre commits ou entre commit e árvore de trabalho.
- [git tag](./../commands/tag.md) → cria, lista ou exclui tags.
- [git stash](./../commands/stash.md) → guarda temporariamente mudanças não commitadas.
- [git restore](./../commands/restore.md) → restaura arquivos da árvore de trabalho.
- [git reset](./../commands/reset.md) → redefine o HEAD para um estado específico.
- [git revert](./../commands/revert.md) → desfaz commits existentes criando commits inversos.
- [git cherry-pick](./../commands/cherry_pick.md) → aplica mudanças introduzidas por commits existentes.
- [git mv](./../commands/mv.md) / [git rm](./../commands/rm.md) → mover/renomear ou remover arquivos do índice e da árvore de trabalho.
- `git archive` → cria um arquivo compactado de uma árvore nomeada.
- [git bisect](./../commands/bisect.md) → busca binária para encontrar commit que introduziu bug.
- `git gc` → otimiza e limpa arquivos desnecessários.
- [git fetch](./../commands/fetch.md) → baixa objetos e refs de outro repositório.
- `git format-patch` → prepara patches para submissão por e-mail.

---

## 🛠 Ancillary Commands / Manipulators
Ferramentas auxiliares para manipulação:

- [git config](./../commands/config.md) → define opções globais ou do repositório.
- `git filter-branch` → reescreve branches.
- `git mergetool` → executa ferramentas de resolução de conflitos.
- [git remote](./../commands/remote.md) → gerencia repositórios remotos.
- `git reflog` → gerencia histórico de referências.
- `git repack` → compacta objetos.
- `git replace` → cria/gerencia refs para substituir objetos.

---

## 🔍 Ancillary Commands / Interrogators
Comandos para inspecionar e diagnosticar:

- `git blame` → mostra quem modificou cada linha de um arquivo.
- `git annotate` → anota linhas com informações de commit.
- `git bugreport` → coleta informações para reportar bug.
- `git difftool` → mostra diferenças usando ferramentas externas.
- `git fsck` → verifica integridade do banco de objetos.
- `git show-branch` → mostra branches e seus commits.
- `git verify-commit` / `git verify-tag` → verifica assinaturas GPG.
- `git version` → mostra versão do Git.

---

## 🌐 Interacting with Others
Integração com outros sistemas:

- `git request-pull` → gera resumo de mudanças pendentes.
- `git send-email` → envia patches como e-mails.
- `git svn` → integração bidirecional com Subversion.
- `git p4` → integração com Perforce.
- `git archimport`, `git cvsimport`, `git cvsexportcommit`, `git cvsserver` → integração com CVS/Arch.

---

## ⚙️ Low-level Commands
Comandos de baixo nível para manipulação interna:

- `git apply` → aplica patches.
- `git commit-tree` → cria objeto de commit.
- `git hash-object` → calcula ID de objeto e opcionalmente cria objeto.
- `git read-tree` → lê informações de árvore para o índice.
- `git write-tree` → cria objeto de árvore a partir do índice.
- `git cat-file` → mostra conteúdo/detalhes de objetos.
- `git ls-tree` → lista conteúdo de um objeto árvore.
- `git rev-list` → lista commits em ordem cronológica inversa.
- `git rev-parse` → interpreta parâmetros de revisão.
- `git update-index` → registra conteúdo de arquivos no índice.
- `git update-ref` → atualiza refs com segurança.

---

## 🔧 Low-level Syncing & Helpers
- `git daemon` → servidor simples para repositórios Git.
- `git http-backend` → implementação de servidor Git via HTTP.
- `git send-pack` → envia objetos via protocolo Git.
- `git fetch-pack` → recebe objetos faltantes de outro repositório.
- `git update-server-info` → atualiza informações auxiliares para servidores simples.
- `git credential-*` → gerencia credenciais (cache, store).
- `git hook` → executa hooks do Git.
- `git patch-id` → calcula ID único para um patch.

---

## 📂 Interfaces e Arquivos
- `attributes` → define atributos por caminho.
- `ignore` → especifica arquivos não rastreados a ignorar.
- `hooks` → scripts de automação em eventos Git.
- `mailmap` → mapeia nomes/emails de autores.
- `repository-layout` → estrutura de diretório do repositório.
- `revisions` → especifica revisões e intervalos.

---

## 👨‍💻 Interfaces para Desenvolvedores
- `format-bundle`, `format-pack`, `format-index` → formatos de arquivos internos.
- `protocol-*` → especificações de protocolos Git (v0, v1, v2, HTTP, pack).
- `format-commit-graph` → formato de commit-graph.
- `format-signature` → formatos de assinatura criptográfica.

---

## 🔗 Comandos Externos
- `git lfs` → suporte a arquivos grandes.
- `git flow` → suporte a fluxo de trabalho Git Flow.
- `credential-manager` → gerenciador de credenciais para Windows.
- `update-git-for-windows` → atualizador para Git no Windows.
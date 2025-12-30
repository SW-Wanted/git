# 📘 Git Checkout — Guia de Referência

O comando `git checkout` é usado para **alternar branches** ou **restaurar arquivos da árvore de trabalho**. Ele também pode ser utilizado para criar novos branches, trabalhar em commits específicos (detached HEAD) e resolver conflitos.

---

## 🔑 Função Principal
- Atualiza arquivos da árvore de trabalho para corresponder ao índice ou a um commit específico.
- Altera o `HEAD` para apontar para outro branch ou commit.
- Permite criar novos branches e alternar para eles.
- Pode restaurar arquivos individuais a partir do índice ou de commits.

---

## 📋 Operações Comuns
- `git checkout <branch>` → alterna para um branch existente.
- `git checkout -b <novo-branch>` → cria e alterna para um novo branch.
- `git checkout -B <branch>` → cria ou redefine branch e alterna para ele.
- `git checkout <commit>` → alterna para um commit específico (detached HEAD).
- `git checkout -- <arquivo>` → restaura arquivo do índice.
- `git checkout <commit> -- <arquivo>` → restaura arquivo de um commit específico.
- `git checkout -p` → modo interativo para descartar/selecionar alterações.

---

## ⚙️ Opções Importantes
- `-f` / `--force` → força troca de branch mesmo com alterações locais.
- `--ours` / `--theirs` → restaura versão de merge (lado nosso ou deles).
- `-m` / `--merge` → tenta mesclar alterações locais ao trocar de branch.
- `--detach` → alterna para commit sem associar a um branch (detached HEAD).
- `--orphan <novo-branch>` → cria branch sem histórico (novo repositório).
- `--guess` / `--no-guess` → controla adivinhação de branch remoto.
- `--conflict=<style>` → define estilo de conflitos (merge, diff3, zdiff3).
- `--overlay` / `--no-overlay` → controla se arquivos extras são removidos.
- `--recurse-submodules` → atualiza submódulos ao trocar de branch.
- `--pathspec-from-file=<arquivo>` → lê lista de arquivos de um arquivo externo.

---

## 🛠️ Conceito de Detached HEAD
- O `HEAD` normalmente aponta para um branch.
- Em detached HEAD, `HEAD` aponta diretamente para um commit.
- Commits criados nesse estado não ficam ligados a nenhum branch.
- É possível criar branch ou tag para preservar esses commits.

---

## 📌 Exemplos Práticos
- Alternar para branch `develop`:  
  `git checkout develop`
- Criar e alternar para branch `feature/login`:  
  `git checkout -b feature/login`
- Restaurar arquivo `hello.c` do índice:  
  `git checkout -- hello.c`
- Alternar para commit específico:  
  `git checkout 1a2b3c4`
- Resolver conflitos escolhendo versão "ours":  
  `git checkout --ours <arquivo>`

---

## ✅ Em resumo
`git checkout` é um comando versátil para **gerenciar branches e restaurar arquivos**.  
Ele permite criar branches, alternar para commits específicos, lidar com merges e conflitos, e até iniciar históricos independentes com `--orphan`. É fundamental para navegação e manipulação de versões dentro de um repositório Git.

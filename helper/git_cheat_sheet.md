# 📘 Git Cheat Sheet

## 1. Inicialização e Configuração

```bash
# Configurar usuário
git config --global user.name "Seu Nome"
git config --global user.email "email@exemplo.com"

# Inicializar repositório
git init

# Clonar repositório existente
git clone <url_do_repositorio>

# Status do repositório
git status
```

## 2. Trabalhando com Arquivos

```bash
# Adicionar arquivos ao staging
git add arquivo.txt
git add .  # todos os arquivos

# Remover arquivos do staging
git reset arquivo.txt

# Remover arquivos do Git mas manter localmente
git rm --cached arquivo.txt
```

## 3. Commits

```bash
# Criar commit
 git commit -m "Mensagem do commit"

# Editar o último commit (amend)
git commit --amend

# Editar a mensagem do ultimo commit
git commit --amend -m "New message"

# Criar commit direto adicionando arquivos (só para rastreados)
git commit -am "Mensagem"

# Remover o último commit (sem perder as alterações)
git reset --soft HEAD~1

# Remover o último commit e tirar os ficheiros do stage
git reset --mixed HEAD~1

# Remover o último commit e todas as alterações (⚠️ cuidado)
git reset --hard HEAD~1

# Desfazer um commit específico sem mexer no histórico
# - Se o commit já foi publicado (por exemplo, está no GitHub), o ideal é reverter:
git revert <hash_do_commit>

```

## 4. Branches

```bash
# Listar branches
git branch

# Criar branch
git branch nome_da_branch

# Mudar de branch
git checkout nome_da_branch
# ou
git switch nome_da_branch

# Criar e mudar de branch ao mesmo tempo
git checkout -b nova_branch
# ou
git switch -c nova_branch

# Deletar branch
git branch -d branch_name
git branch -D branch_name  # forçar deletar
```

## 5. Pull, Push e Remote

```bash
# Adicionar remoto
git remote add origin <url_do_repositorio>

# Ver remotos
git remote -v

# Enviar alterações (push)
git push origin main

# Puxar alterações (pull)
git pull
git pull origin main
git pull --rebase origin main   # rebasing
```

## 6. Merge e Rebase

```bash
# Merge
git merge nome_da_branch

# Rebase
git rebase main
```

## 7. Manutenção de Commits e Histórico

```bash
# Voltar ao commit anterior mantendo alterações
git reset --soft HEAD~1

# Voltar ao commit anterior descartando alterações
git reset --hard HEAD~1

# Reverter um commit específico (gera commit novo)
git revert <hash_commit>

# Rebase interativo (editar, unir ou reordenar commits)
git rebase -i HEAD~N
# pick -> mantém o commit
# squash -> junta ao anterior
# edit -> edita o commit

# Mostrar histórico de commits
git log
git log --oneline --graph --decorate --all
```

## 8. Stash (guardar alterações temporariamente)

```bash
git stash           # guarda alterações não commitadas
git stash list      # lista stashes
git stash pop       # aplica e remove stash
git stash apply     # aplica sem remover stash
```

## 9. Tags

```bash
# Criar tag
git tag v1.0
git tag -a v1.0 -m "Release 1.0"

# Enviar tags
git push origin v1.0
git push origin --tags
```

## 10. Outros Comandos Úteis

```bash
git diff                  # diferenças entre arquivos modificados e staging
git diff --staged         # diferenças entre staging e último commit
git show <hash_commit>    # mostrar alterações de um commit
git blame arquivo.txt     # mostra linha por linha quem modificou
git clean -f              # remove arquivos não rastreados
git fetch                 # baixa alterações do remoto sem aplicar
git remote prune origin   # remove branches remotas deletadas
```
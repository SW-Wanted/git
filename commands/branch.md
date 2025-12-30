# Branch
`git branch` é o comando central para gerenciar branches no Git — listar, criar, renomear, copiar, excluir e configurar tracking com remotos. Ele oferece opções poderosas para filtrar branches, controlar upstream e personalizar comportamento.

## 🔑 Função Principal
O comando `git branch` serve para:

- Listar branches existentes (locais e remotos).
- Criar novos branches a partir do `HEAD` ou de um commit específico.
- Renomear ou copiar branches.
- Deletar branches locais ou remotos.
- Configurar tracking/upstream entre branches locais e remotos.
- Editar descrições de branches.

## 📋 Operações Comuns
- `git branch` → lista branches locais.
- `git branch -r` → lista branches remotos.
- `git branch -a` → lista todos (locais + remotos).
- `git branch <nome>` → cria um novo branch.
  - Exemplo: `git branch feature/login`
- `git branch <nome> <commit|tag>` → cria branch a partir de commit/tag.
  - Exemplo: `git branch hotfix/ssl v1.2.3`
- `git branch -d <nome>` → deleta branch (se já foi mesclado).
- `git branch -D <nome>` → força a exclusão.
- `git branch -m <antigo> <novo>` → renomeia branch (falha se o destino existir).
- `git branch -M <antigo> <novo>` → renomeia branch forçando, mesmo se o destino existir.
- `git branch -c <antigo> <novo>` → copia branch.
- `git branch -C <antigo> <novo>` → copia branch forçando, mesmo se o destino existir.
- `git branch --set-upstream-to=<remoto>/<branch>` → define branch remoto como upstream.
  - Exemplo: `git branch --set-upstream-to=origin/main`
- `git branch --set-upstream-to=<remoto>/<branch> <local>` → define upstream para branch específico.
  - Exemplo: `git branch --set-upstream-to=origin/dev dev`
- `git branch --unset-upstream` → remove configuração de upstream.
- `git branch --show-current` → mostra branch atual.
- `git branch --edit-description` → abre editor para editar descrição do branch.

## ⚙️ Opções Importantes
- `git branch --merged [<commit>]` → lista branches já mesclados em relação ao commit (padrão: HEAD).
  - Exemplo: `git branch --merged main`
- `git branch --no-merged [<commit>]` → lista branches não mesclados.
  - Exemplo: `git branch --no-merged main`
- `git branch --contains <commit>` → lista branches que contêm determinado commit.
- `git branch --no-contains <commit>` → lista branches que não contêm determinado commit.
- `git branch --track <novo> <remoto>/<branch>` → cria branch com tracking automático.
- `git branch --no-track <novo> <remoto>/<branch>` → cria branch sem tracking.
- `git branch -f <nome> [<start-point>]` → força criação/renomeação/exclusão mesmo em casos restritos.
- `git branch --color=always` → força saída colorida.
- `git branch --color=never` → desativa cores.
- `git branch -v` → mostra SHA e mensagem do último commit.
- `git branch -vv` → mostra SHA, upstream e worktree.

## 🛠️ Configurações Relacionadas
- `git config --global branch.autoSetupMerge true`  
  → controla se novos branches criados a partir de remotos terão tracking automático.
- `git config --global branch.autoSetupRebase always`  
  → define se `git pull` deve usar rebase em vez de merge.
- `git config --global branch.sort -committerdate`  
  → ordena branches na listagem (ex.: por data do último commit).
- `git config branch.<nome>.remote <remoto>`  
  → configura remoto para branch específico.
- `git config branch.<nome>.merge refs/heads/<branch-remoto>`  
  → define branch remoto que será usado como upstream.
- `git config branch.<nome>.description "texto"`  
  → adiciona descrição editável ao branch.

## 📌 Exemplos Práticos
- Criar branch a partir de uma tag e configurar tracking:  
  `git branch --track release/1.2 origin/release/1.2`
- Renomear branch atual de forma segura:  
  `git branch -m feature/login feature/auth`
- Forçar renomeação quando o destino já existe:  
  `git branch -M feature/auth feature/signup`
- Listar branches não mesclados em relação ao main:  
  `git branch --no-merged main -vv`
- Apagar com segurança branches já mesclados:  
  `git branch --merged main | grep -v "\*" | xargs -n 1 git branch -d`

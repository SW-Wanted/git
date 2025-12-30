## 🔹 Iniciar um repositório
- `git init` → cria um novo repositório vazio.
- `git clone` → copia um repositório existente.

---

## 🔹 Trabalhar nas mudanças
- `git add` → adiciona arquivos ao índice.
- `git commit` → registra mudanças no histórico.
- `git status` → mostra o estado da árvore de trabalho.
- `git restore` → desfaz alterações em arquivos.
- `git rm` → remove arquivos do índice e do diretório.
- `git mv` → move ou renomeia arquivos.
- `git clean` → remove arquivos não rastreados.
- `git stash` → guarda mudanças temporariamente.

---

## 🔹 Explorar histórico e estado
- `git log` → mostra histórico de commits.
- `git diff` → compara mudanças.
- `git show` → inspeciona commits ou objetos.
- `git grep` → busca padrões no código.
- `git bisect` → encontra o commit que introduziu um bug.
- `git shortlog` → resumo do log por autor.
- `git whatchanged` → mostra diferenças introduzidas por cada commit.
- `git describe` → dá nome legível a objetos.

---

## 🔹 Gerenciar branches e versões
- `git branch` → lista, cria ou remove branches.
- `git switch` → troca de branch facilmente.
- `git checkout` → alterna branch ou restaura arquivos.
- `git merge` → une branches.
- `git rebase` → reaplica commits em outra base.
- `git reset` → redefine HEAD para outro estado.
- `git revert` → desfaz commits específicos.
- `git tag` → marca pontos importantes no histórico.
- `git worktree` → gerencia múltiplas árvores de trabalho.
- `git cherry-pick` → aplica commits escolhidos em outro branch.
- `git range-diff` → compara dois conjuntos de commits.

---

## 🔹 Colaborar com outros
- `git fetch` → baixa objetos e refs de outro repositório.
- `git pull` → traz e integra mudanças do remoto.
- `git push` → envia commits para o remoto.
- `git remote` → gerencia conexões com repositórios externos.
- `git submodule` → gerencia submódulos.
- `git bundle` → exporta objetos e refs em arquivo.
- `git request-pull` → gera resumo de mudanças para upstream.
- `git send-email` → envia patches por e-mail.
- `git am` → aplica patches recebidos por e-mail.
- `git format-patch` → gera patches para envio.

---

## 🔹 Manutenção e otimização
- `git gc` → otimiza repositório.
- `git maintenance` → tarefas de manutenção.
- `git reflog` → histórico de referências.
- `git fsck` → verifica integridade dos objetos.
- `git prune` → remove objetos inalcançáveis.
- `git repack` → empacota objetos.
- `git notes` → adiciona anotações a objetos.

---

## 🔹 Ferramentas gráficas e auxiliares
- `gitk` → navegador gráfico de repositório.
- `git gui` → interface gráfica portátil.
- `git citool` → alternativa gráfica ao commit.
- `git mergetool` → resolve conflitos com ferramentas visuais.
- `git difftool` → compara mudanças com ferramentas externas.

---

## 🔹 Avançados e especializados
- `git backfill` → baixa blobs faltantes em clones parciais.
- `git scalar` → gerencia repositórios grandes.
- `git survey` → mede dimensões de escala (experimental).
- `git blame` → mostra quem modificou cada linha.
- `git annotate` → anota linhas com informações de commit.
- `git replay` → reaplica commits em nova base (experimental).

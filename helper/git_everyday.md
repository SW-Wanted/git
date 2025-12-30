# 📘 Git Everyday

Para fins de descrição de um pequeno conjunto de comandos úteis para o uso diário do Git, os utilizadores podem ser amplamente agrupados em quatro categorias.

- Os comandos de [Desenvolvedor Individual (Autónomo)](#-desenvolvedor-individual-autônomo) são essenciais para qualquer pessoa que faça commits, mesmo para quem trabalha sozinho.

- Se você trabalha com outras pessoas, também precisará dos comandos listados na secção [Desenvolvedor Individual (Participante)](#-desenvolvedor-individual-participante).

- As pessoas que exercem o papel de [Integrador](#-integrador) precisam aprender alguns comandos adicionais além dos anteriores.

- Os comandos de [Administração de Repositório](#️-administração-de-repositório) destinam-se a administradores de sistemas responsáveis pela manutenção e gestão de repositórios Git.

## 👨‍💻 Desenvolvedor Individual (Autônomo)

Um **desenvolvedor individual autónomo** não troca patches com outras pessoas e trabalha sozinho num único repositório, utilizando os seguintes comandos:

- `git init` → cria um novo repositório.
- `git add` → adiciona arquivos ao índice.
- `git commit` → registra mudanças.
- `git status` → mostra o estado da árvore de trabalho.
- `git log` → inspeciona histórico de commits.
- `git diff` → compara mudanças.
- `git switch` / `git branch` → alterna ou cria branches.
- `git restore` → desfaz alterações.
- `git merge` → une branches locais.
- `git tag` → marca pontos importantes no histórico.


## 🤝 Desenvolvedor Individual (Participante)

Um **desenvolvedor que atua como participante** num projeto em grupo precisa aprender a comunicar-se com outros e usa estes comandos, além dos necessários para um **[desenvolvedor autónomo](#-desenvolvedor-individual-autônomo)**:

- `git clone` → copia repositório existente.
- `git pull` / `git fetch` → traz mudanças do remoto.
- `git push` → envia suas contribuições.
- `git format-patch` → prepara patches para envio.
- `git send-email` → envia patches por e-mail.
- `git request-pull` → gera resumo para upstream.

---

## 🧑‍🔧 Integrador

Uma pessoa relativamente central que atua como **integrador** num projeto em grupo recebe alterações feitas por outros, revê, responde a `git request-pull` ou pull requests no GitHub, integra e publica o resultado para uso dos demais, utilizando estes comandos além dos necessários aos **[participantes](#-desenvolvedor-individual-participante)**.

- `git am` → aplica patches recebidos.
- `git revert` → desfaz commits problemáticos.
- `git rebase` → reaplica commits em outra base.
- `git cherry-pick` → aplica commits específicos.
- `git push` → publica branches e tags.
- `git show` → inspeciona commits detalhadamente.
- `git bisect` → encontra o commit que introduziu um bug.

---

## 🛠️ Administração de Repositório

Um **administrador de repositório** usa as seguintes ferramentas para configurar e manter o acesso de desenvolvedores:

- `git daemon` → servidor simples para acesso.
- `git shell` → shell restrito para usuários.
- `git http-backend` → suporte a Git via HTTP.
- `git gc` → otimiza repositório.
- `git config` → ajusta opções globais e locais.
- `git worktree` → gerencia múltiplas árvores de trabalho.
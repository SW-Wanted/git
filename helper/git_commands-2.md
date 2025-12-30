# 📘 Guia Completo do Git

Este README reúne os principais **comandos** e **guias conceituais** do Git, organizados para servir como referência prática e teórica. Ele cobre desde operações básicas até conceitos avançados e fluxos de trabalho recomendados.

---

## 🔑 Comandos Principais (Porcelain)
Estes são os comandos de alto nível usados no dia a dia:

- `git add` → adiciona arquivos ao índice (staging).
- `git commit` → registra mudanças no repositório.
- `git branch` → lista, cria ou exclui branches.
- `git checkout` / `git switch` → alterna branches ou restaura arquivos.
- `git merge` → une históricos de desenvolvimento.
- `git rebase` → reaplica commits sobre outro ponto base.
- `git clone` → clona um repositório.
- `git pull` → busca e integra alterações de outro repositório.
- `git push` → envia commits para remoto.
- `git status` → mostra estado da árvore de trabalho.
- `git log` → exibe histórico de commits.
- `git diff` → mostra diferenças entre commits ou entre commit e árvore.
- `git tag` → cria, lista ou exclui tags.
- `git stash` → guarda temporariamente mudanças não commitadas.
- `git reset` / `git revert` → redefinir HEAD ou desfazer commits.
- `git cherry-pick` → aplica mudanças de commits específicos.
- `git mv` / `git rm` → mover/renomear ou remover arquivos.

---

## 🛠 Comandos Auxiliares (Ancillary)
Ferramentas para manipulação e inspeção:

- `git config` → configura opções globais ou locais.
- `git remote` → gerencia repositórios remotos.
- `git reflog` → histórico de referências.
- `git repack` / `git prune` → otimização e limpeza.
- `git mergetool` → resolução de conflitos com ferramentas externas.
- `git blame` / `git annotate` → mostra quem modificou cada linha.
- `git fsck` → verifica integridade do repositório.
- `git show-branch` → exibe branches e commits.
- `git verify-commit` / `git verify-tag` → verifica assinaturas GPG.

---

## 🌐 Interação com Outros Sistemas
Integração com outros SCMs e envio de patches:

- `git request-pull` → gera resumo de mudanças pendentes.
- `git send-email` → envia patches por e-mail.
- `git svn` → integração bidirecional com Subversion.
- `git p4` → integração com Perforce.
- `git cvsimport`, `git cvsexportcommit`, `git cvsserver` → integração com CVS.
- `git archimport` → integração com GNU Arch.

---

## ⚙️ Comandos de Baixo Nível
Operações internas e avançadas:

- `git apply` → aplica patches.
- `git commit-tree` → cria objeto de commit.
- `git hash-object` → calcula ID de objeto.
- `git read-tree` / `git write-tree` → manipula objetos árvore.
- `git cat-file` → mostra conteúdo de objetos.
- `git ls-tree` → lista conteúdo de árvore.
- `git rev-list` / `git rev-parse` → manipula revisões.
- `git update-index` / `git update-ref` → atualiza índice e referências.

---

## 📂 Interfaces e Arquivos
Definições e convenções:

- `attributes` → atributos por caminho.
- `ignore` → arquivos a ignorar.
- `hooks` → scripts de automação.
- `mailmap` → mapeamento de nomes/emails.
- `repository-layout` → estrutura de diretório.
- `revisions` → especificação de revisões e intervalos.

---

## 👨‍💻 Interfaces para Desenvolvedores
Formatos e protocolos internos:

- `format-bundle`, `format-pack`, `format-index` → formatos de arquivos.
- `protocol-*` → especificações de protocolos Git (v0, v1, v2, HTTP).
- `format-commit-graph` → formato de commit-graph.
- `format-signature` → formatos de assinatura criptográfica.

---

## 📘 Guias Conceituais (git help -g)
Documentação conceitual para aprofundar o entendimento:

- **`core-tutorial`** → tutorial do núcleo do Git para desenvolvedores.
- **`credentials`** → fornecimento de usuários e senhas ao Git.
- **`cvs-migration`** → Git para usuários de CVS.
- **`diffcore`** → ajustes na saída de diffs.
- **`everyday`** → conjunto mínimo de comandos úteis para o dia a dia.
- **`faq`** → perguntas frequentes sobre Git.
- **`glossary`** → glossário de termos do Git.
- **`namespaces`** → namespaces no Git.
- **`remote-helpers`** → programas auxiliares para interação com remotos.
- **`submodules`** → uso de submódulos (repositórios dentro de outros).
- **`tutorial`** → introdução ao Git.
- **`tutorial-2`** → introdução ao Git (parte dois).
- **`workflows`** → visão geral de fluxos de trabalho recomendados.

---

## ✅ Conclusão
Este README organiza o Git em duas dimensões:
- **Comandos** → Porcelain (alto nível), Ancillary (auxiliares), Low-level (internos).
- **Guias Conceituais** → Tutoriais, glossário, workflows e integrações.

📌 Use este guia como referência rápida para dominar tanto a prática quanto a teoria do Git.
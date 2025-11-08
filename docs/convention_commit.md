# 🧭 Guia de Convenção de Commits (COMMIT_CONVENTION.md)

## 🧠 Objetivo

Este documento define o padrão de mensagens de commit utilizado neste repositório. O objetivo é manter um histórico limpo, expressivo e automatizável (para gerar changelogs, releases e facilitar revisões de código).

Cada commit deve indicar **o tipo de alteração**, **o contexto (scope)** e **um resumo conciso**.

> **Formato padrão:**
>
> ```
> EMOJI tipo(scope): resumo curto
>
> [linha em branco]
> [descrição detalhada opcional]
>
> [Footer opcional: Fixes #id, Refs #id, Co-authored-by: nome]
> ```

---

## 📋 Tipos e Emojis

| Emoji |       Tipo        | Descrição           | Quando usar                                  | Exemplo                                      |
| :---: | :---------------: | :------------------ | :------------------------------------------- | :------------------------------------------- |
|  ✨   |     **feat**      | Nova funcionalidade | Quando adicionas um novo recurso ou função   | `✨ feat(auth): add password reset endpoint` |
|  🐛   |      **fix**      | Correção de bug     | Corrige comportamentos incorretos            | `🐛 fix(parser): handle negative numbers`    |
|  📝   |     **docs**      | Documentação        | README, wikis, docstrings                    | `📝 docs: update API reference`              |
|  🎨   |     **style**     | Estilo / Formatação | Espaços, indentação, lint                    | `🎨 style: reformat code to norminette`      |
|  ♻️   |   **refactor**    | Refatoração         | Melhorias internas sem alterar comportamento | `♻️ refactor(db): simplify query logic`      |
|  ✅   |     **test**      | Testes              | Cria ou modifica testes                      | `✅ test(api): add auth integration tests`   |
|  🔧   |     **chore**     | Tarefas gerais      | Atualiza dependências, configs, scripts      | `🔧 chore: update Makefile`                  |
|  ⚡️  |     **perf**      | Performance         | Otimização de desempenho                     | `⚡️ perf(cache): reduce lookup latency`     |
|  📦   |     **build**     | Sistema de build    | Makefile, CMake, npm build                   | `📦 build: update CMakeLists`                |
|  ⚙️   |      **ci**       | Integração Contínua | Workflows, pipelines, actions                | `⚙️ ci: add GitHub Actions pipeline`         |
|  🔥   |    **remove**     | Remoção de código   | Elimina arquivos ou trechos obsoletos        | `🔥 remove: drop legacy payment module`      |
|  🚑   |    **hotfix**     | Correção urgente    | Patch crítico em produção                    | `🚑 hotfix(auth): fix token expiry bug`      |
|  ♿️  | **accessibility** | Acessibilidade      | Melhorias de UX/A11y                         | `♿️ accessibility: add aria labels`         |
|  🔐   |   **security**    | Segurança           | Patches ou medidas de proteção               | `🔐 security: sanitize user input`           |
|  🧹   |     **clean**     | Limpeza             | Remoção de warnings, logs ou TODOs           | `🧹 clean: remove debug statements`          |
|  🐳   |    **docker**     | Docker / containers | Dockerfile, compose, imagens                 | `🐳 docker: add production compose file`     |
|  🚚   |     **move**      | Movimentação        | Renomeia ou move ficheiros                   | `🚚 move: relocate utils to /lib`            |
|  🗃️   |      **db**       | Banco de dados      | Migrations, seeds, esquemas                  | `🗃️ db: add create_users_table migration`    |
|  🌐   |     **i18n**      | Internacionalização | Tradução, locale, suporte multilíngue        | `🌐 i18n: add pt-PT translations`            |
|  🧪   |  **experiment**   | Protótipos / POCs   | Testes ou ideias experimentais               | `🧪 experiment: try new parsing strategy`    |
|  📈   |   **analytics**   | Telemetria / logs   | Trackers, métricas, analytics                | `📈 analytics: add usage tracking`           |
|  🛠️   |    **config**     | Configurações       | Ajustes em configurações gerais              | `🛠️ config: tune nginx timeouts`             |
|  🧱   |    **release**    | Publicação / tag    | Releases, version bumps                      | `🧱 release: v1.4.0`                         |
|  ↩️   |    **revert**     | Reversão de commit  | Reverte alteração anterior                   | `↩️ revert: revert "feat: add auth"`         |
|  🔄   |     **sync**      | Sincronização       | Merge, upstream, mirrors                     | `🔄 sync: merge branch develop`              |

---

## 🧩 Estrutura da Mensagem

### 1️⃣ Linha de cabeçalho (obrigatória)

- Formato: `EMOJI tipo(scope): resumo`
- **Limite:** 72 caracteres no máximo.
- O resumo deve ser **imperativo** e **conciso** ("add", "fix", "remove", "update").

### 2️⃣ Corpo (opcional)

Explica **porquê** a mudança foi feita e **o impacto** no sistema.

### 3️⃣ Rodapé (opcional)

Incluir referências a issues, PRs ou co-autores.

```
Fixes #42
Refs #101
Co-authored-by: Emanuel <emanuel@example.com>
```

---

## 💡 Exemplos Práticos

```
✨ feat(trie): add insert and search methods

Implements the core Trie functionality with support for
insertion and lookup of lowercase words.

Refs #12
```

```
🐛 fix(memory): prevent leak in ft_split

Freed temporary buffer when handling malformed input
to prevent heap growth.

Closes #34
```

```
🔧 chore: update .gitignore and Makefile
```

```
✅ test(gnl): add test for EOF edge case
```

---

## 🧰 Boas Práticas

- Usa **um commit por alteração lógica**.
- Evita commits genéricos como "update code".
- Mantém o histórico **legível e semântico**.
- Usa `feat`, `fix` e `perf` para gerar changelogs automáticos.

---

# 🔖 Palavras-chave de Issues nos Commits

Essas palavras são interpretadas automaticamente pelas plataformas (como GitHub) para ligar ou fechar issues quando fazes o push do commit ou merge da branch.

## 🧩 1. Referenciar (sem fechar)

Essas palavras apenas criam um link para a issue.
Útil quando o trabalho ainda está em andamento.
| Palavra-chave | Ação | Exemplo |
| ------------- | -------------------------------------- | ---------------- |
| `Refs` | Apenas referencia a issue | `Refs #12` |
| `References` | Apenas referencia | `References #12` |
| `See` | Apenas referencia | `See #12` |
| `Related to` | Apenas referencia | `Related to #12` |
| `Part of` | Indica que o commit faz parte da issue | `Part of #12` |

### Exemplo

```markdown
✨ feat(trie): add insert and search methods

Implements the core Trie functionality with support for
insertion and lookup of lowercase words.

Refs #12
```

A issue **#12** vai mostrar que este commit está **relacionado**, mas não será fechada.

## 🧩 2. Fechar automaticamente a issue

Essas palavras fecham a issue automaticamente quando o commit chega à branch principal (geralmente main ou master).

| Palavra-chave | Efeito        | Exemplo        |
| ------------- | ------------- | -------------- |
| `Fixes`       | Fecha a issue | `Fixes #12`    |
| `Closes`      | Fecha a issue | `Closes #12`   |
| `Resolves`    | Fecha a issue | `Resolves #12` |
| `Fixed`       | Fecha a issue | `Fixed #12`    |
| `Closed`      | Fecha a issue | `Closed #12`   |
| `Resolved`    | Fecha a issue | `Resolved #12` |

### Exemplo

```markdown
🐛 fix(trie): correct word lookup logic

Fixes a bug where the search method failed
for words with a shared prefix.

Fixes #12
```

Assim que fizeres o push e o merge, a issue **#12** será **fechada automaticamente**.

## 🧩 3. Combinar múltiplas issues

Podes fechar ou referenciar várias issues no mesmo commit.

### Exemplo

```markdown
✨ feat(hashmap): implement collision handling

Introduces chaining technique to handle key collisions
in the hash map implementation.

Fixes #10, Fixes #11, Refs #12
```

- As issues **#10** e **#11** serão **fechadas automaticamente**.
- A issue **#12** será apenas **referenciada**.

## 🧩 4. Quando usar

- Usa `Refs` quando o commit faz parte do **progresso** (por exemplo, etapa intermediária).
- Usa `Fixes` / `Closes` / `Resolves` quando o commit **finaliza o trabalho** e a issue pode ser fecha

## 🚀 Automatização Recomendada

### 🔍 Hook Git `commit-msg`

Adiciona o seguinte script em `.git/hooks/commit-msg` e torna-o executável com `chmod +x .git/hooks/commit-msg`:

```bash
#!/bin/bash

commit_msg_file=$1
commit_msg=$(head -n1 "$commit_msg_file")

regex='^([[:space:]]*[[:graph:]]+)\s(feat|fix|docs|style|refactor|test|chore|perf|build|ci|remove|hotfix|accessibility|security|clean|docker|move|db|i18n|experiment|analytics|config|release|revert|sync)(\(.+\))?: .{1,72}$'

if ! [[ $commit_msg =~ $regex ]]; then
  echo "\n❌ Mensagem de commit inválida.\n"
  echo "➡️ Formato esperado: EMOJI tipo(scope): resumo curto"
  echo "Exemplo: ✨ feat(api): add authentication endpoint\n"
  exit 1
fi

exit 0
```

Este hook impede commits fora do padrão definido.

---

## 📚 Referências

- [Conventional Commits](https://www.conventionalcommits.org/)
- [Gitmoji](https://gitmoji.dev)
- [Keep a Changelog](https://keepachangelog.com)

---

> _Mantém os commits significativos. Cada commit é uma história — escreve-a como se outros fossem depender dela._

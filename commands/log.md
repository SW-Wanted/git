# 📘 Git Log — Guia de Referência

O comando `git log` mostra o histórico de commits em um repositório. Ele é altamente configurável, permitindo limitar, ordenar e formatar a saída conforme a necessidade.

---

## 🔑 Função Principal
- Exibe commits em ordem cronológica inversa.
- Permite definir intervalos de revisões (`commit1..commit2`, `commit1...commit2`).
- Pode mostrar apenas commits que afetam determinados arquivos ou caminhos.
- Suporta filtros por autor, datas, mensagens e merges.

---

## 📋 Operações Comuns
- `git log` → lista histórico completo.
- `git log <branch>` → histórico de um branch específico.
- `git log <commit1>..<commit2>` → commits entre dois pontos.
- `git log -- <path>` → histórico de um arquivo ou diretório.
- `git log --oneline` → histórico compacto (hash abreviado + mensagem).
- `git log --graph` → exibe gráfico ASCII da árvore de commits.
- `git log --decorate` → mostra refs (branches, tags) associadas a commits.

---

## ⚙️ Opções Importantes
- **Limitação de commits:**
  - `--since=<data>` / `--until=<data>` → filtra por datas.
  - `--author=<padrão>` / `--committer=<padrão>` → filtra por autor/committer.
  - `--grep=<padrão>` → filtra por mensagens de commit.
  - `--merges` / `--no-merges` → inclui ou exclui merges.
  - `--max-count=<n>` → limita número de commits.

- **Ordenação:**
  - `--date-order` → ordena por data de commit.
  - `--author-date-order` → ordena por data do autor.
  - `--topo-order` → evita misturar commits de linhas paralelas.
  - `--reverse` → inverte ordem.

- **Formatação:**
  - `--pretty=<formato>` → define formato (oneline, short, medium, full, email, raw).
  - `--abbrev-commit` → mostra hash abreviado.
  - `--stat` → resumo de alterações por arquivo.
  - `-p` / `--patch` → mostra diffs completos.
  - `--name-only` / `--name-status` → lista arquivos alterados.

---

## 🛠️ Configurações Relacionadas
- `log.decorate` → controla exibição de refs.
- `log.abbrevCommit` → define tamanho do hash abreviado.
- `log.date` → formato padrão de datas.
- `log.diffMerges` → formato de diffs em merges.

---

## 📌 Exemplos Práticos
- Histórico compacto com gráfico e refs:  
  `git log --oneline --graph --decorate`
- Commits de um autor específico no último mês:  
  `git log --author="Emanuel" --since="1 month ago"`
- Histórico de um arquivo com diffs:  
  `git log -p -- <arquivo>`
- Commits não mesclados em relação ao main:  
  `git log main --no-merges`
- **Histórico dos 5 últimos commits com personalização da saída:**
  
  `git log -n 5 --pretty=format:"%h - %an, %ar : %s"`
  
### 🔑 Explicação dos parâmetros do último exemplo
- `-n 5` → limita a saída aos 5 commits mais recentes.
- `--pretty=format:"..."` → define o formato de saída.
  - `%h` → hash abreviado do commit.
  - `%an` → nome do autor.
  - `%ar` → data relativa (ex.: "2 days ago").
  - `%s` → mensagem do commit.

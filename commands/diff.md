# 📘 Git Diff — Guia de Referência

O comando `git diff` mostra diferenças entre commits, entre o índice (staging) e a árvore de trabalho, ou entre dois arquivos/objetos. É uma ferramenta essencial para inspecionar alterações antes de confirmar ou integrar mudanças.

---

## 🔑 Função Principal
- Comparar **working tree** com o índice.
- Comparar **índice** com um commit.
- Comparar **dois commits** arbitrários.
- Comparar **blobs** (conteúdos brutos de objetos).
- Comparar **dois arquivos** no disco (`--no-index`).
- Visualizar diferenças em merges ou conflitos (`AUTO_MERGE`).

---

## 📋 Operações Comuns
- `git diff` → mostra mudanças não staged.
- `git diff --cached` → mostra mudanças staged em relação ao último commit.
- `git diff HEAD` → mostra mudanças desde o último commit.
- `git diff <commit>` → compara working tree com commit específico.
- `git diff <commit1> <commit2>` → compara dois commits.
- `git diff <branch1> <branch2>` → compara branches.
- `git diff --no-index file1 file2` → compara arquivos fora do controle do Git.

---

## ⚙️ Opções Importantes
- `-p` / `--patch` → gera patch detalhado.
- `--stat` → resumo de alterações por arquivo.
- `--shortstat` → resumo compacto (arquivos modificados, linhas adicionadas/removidas).
- `--name-only` → lista apenas nomes de arquivos alterados.
- `--name-status` → lista nomes e status (A, M, D, R).
- `--color` / `--no-color` → controla cores na saída.
- `--word-diff` → mostra diferenças por palavra.
- `--diff-algorithm=<alg>` → define algoritmo (myers, minimal, patience, histogram).
- `--ignore-space-change`, `--ignore-all-space` → ignora diferenças de espaço.
- `--check` → alerta sobre erros de whitespace.
- `--submodule` → controla como mostrar diffs em submódulos.
- `--relative` → mostra caminhos relativos ao diretório atual.
- `--exit-code` → retorna código de saída (0 se não há diferenças, 1 se há).
- `--quiet` → suprime saída, útil em scripts.

---

## 🛠️ Formatos de Saída
- **Raw output** → mostra modos, hashes e status de arquivos.
- **Patch format** → saída tradicional de diffs com contexto.
- **Combined diff** → usado em merges, mostra diferenças em múltiplos pais.
- **Numstat** → saída numérica (linhas adicionadas/removidas).
- **Dirstat** → distribuição de mudanças por diretório.

---

## 📌 Exemplos Práticos
- Mostrar mudanças não staged:  
  `git diff`
- Mostrar mudanças staged:  
  `git diff --cached`
- Comparar último commit com penúltimo:  
  `git diff HEAD^ HEAD`
- Comparar branches:  
  `git diff topic master`
- Mostrar apenas nomes de arquivos alterados:  
  `git diff --name-only`
- Mostrar resumo estatístico:  
  `git diff --stat`

---

## ✅ Em resumo
`git diff` é a ferramenta central para **inspecionar diferenças** no Git.  
Ele suporta múltiplos modos de comparação (working tree, índice, commits, blobs, arquivos externos) e oferece opções poderosas de filtragem, formatação e análise. É indispensável para revisão de código e auditoria de mudanças.

# 🧭 Convenções e Boas Práticas para Criação de Issues

As *issues* são a base da organização e comunicação num projeto.  
Elas permitem registar bugs, propor funcionalidades e documentar tarefas de forma rastreável e colaborativa.

---

## 📌 1. Tipos de Issues

| Tipo | Emoji | Prefixo | Quando usar |
|------|--------|----------|-------------|
| 🐛 **Bug Report** | 🐛 | `bug:` | Quando algo não funciona como esperado |
| ✨ **Feature Request** | ✨ | `feat:` | Quando queres adicionar algo novo |
| 🧹 **Refactor** | ♻️ | `refactor:` | Quando queres melhorar código existente |
| 🧠 **Documentation** | 📝 | `docs:` | Quando há necessidade de atualizar documentação |
| ⚙️ **Chore / Task** | 🔧 | `chore:` | Para tarefas de manutenção, configs, dependências |
| 🚀 **Performance** | ⚡ | `perf:` | Quando queres melhorar desempenho |
| 🧪 **Testing** | ✅ | `test:` | Para criar ou atualizar testes |
| 🗂️ **Project Management** | 🗂️ | `pm:` | Planeamento e organização de milestones e tarefas |

---

## 🧩 2. Estrutura Padrão de uma Issue

### 🏷️ Título
[emoji] tipo: descrição breve

**Exemplos:**
🐛 bug: erro ao calcular imposto
✨ feat: adicionar menu principal interativo
🧠 docs: atualizar instruções de compilação

---

### 🧾 Corpo

Usa o seguinte modelo base para descrever a issue:

```markdown
## 🧩 Descrição
(Explica claramente o problema, funcionalidade ou tarefa.)

## 🧠 Contexto
(Como o problema foi identificado, ou por que é necessário implementar a melhoria.)

## 🧪 Passos para Reproduzir (para bugs)
1. Passo 1...
2. Passo 2...
3. Resultado esperado...
4. Resultado obtido...

## 🚀 Solução Proposta
(Descreve brevemente como resolver — se já houver uma ideia.)

## ✅ Critérios de Aceitação
- [ ] O código foi testado e validado
- [ ] Documentação atualizada
- [ ] Commit segue as convenções (`COMMIT_CONVENTION.md`)
```

## 🧱 3. Labels Recomendadas

| Label              | Cor sugerida  | Significado                    |
| ------------------ | ------------- | ------------------------------ |
| `bug`              | 🔴 Vermelho   | Erros e falhas                 |
| `enhancement`      | 🟢 Verde      | Nova funcionalidade            |
| `documentation`    | 🟣 Roxo       | Alterações de documentação     |
| `refactor`         | 🟡 Amarelo    | Melhoria de código             |
| `test`             | 🔵 Azul       | Questões relacionadas a testes |
| `help wanted`      | 🟠 Laranja    | Requer assistência             |
| `good first issue` | 🩵 Azul claro | Boa para iniciantes            |

## 🧠 4. Boas Práticas

✅ Sê específico e direto no título.
✅ Adiciona labels adequadas para facilitar filtros.
✅ Usa checklists (- [ ]) para marcar progresso.
✅ Liga issues a commits com Fixes #n ou Closes #n.
✅ Evita duplicar issues já abertas.
✅ Menciona pessoas relevantes com @nome.

## 🧩 5. Exemplo Completo
```markdown
✨ feat: adicionar cálculo automático de média de alunos

## 🧩 Descrição
Implementar uma função que calcule automaticamente a média final dos alunos, com base nas notas de provas e trabalhos.

## 🧠 Contexto
Atualmente o cálculo é feito manualmente em cada exercício, o que gera duplicação de código.

## 🚀 Solução Proposta
Criar a classe `CalculadoraMedia` em `exercicio3/` e integrá-la ao menu principal (`Main.java`).

## ✅ Critérios de Aceitação
- [ ] Código compilando sem erros
- [ ] Média calculada corretamente
- [ ] Teste criado em `testes/Exercicio3Test.java`
```
Labels: `enhancement`, `ready-for-dev`

---

# ⚙️ **Parte 2 — Template de Issue no GitHub**

Agora, vamos automatizar.  
O GitHub permite definir *templates de issue* no repositório, para que qualquer colaborador veja o formato automaticamente ao criar uma nova issue.

## 📁 Estrutura do diretório

Cria dentro do teu repositório:
```bash
.github/
└── ISSUE_TEMPLATE/
├── bug_report.yml
├── feature_request.yml
└── refactor_request.yml
```

---

## 🐛 `bug_report.yml`

```yaml
name: "🐛 Bug Report"
description: Reportar um erro encontrado no projeto
title: "🐛 bug: [descrição curta]"
labels: ["bug"]
body:
  - type: textarea
    attributes:
      label: 🧩 Descrição
      description: Descreve o erro de forma clara.
    validations:
      required: true
  - type: textarea
    attributes:
      label: 🧪 Passos para Reproduzir
      description: Lista os passos para reproduzir o bug.
  - type: textarea
    attributes:
      label: 🧠 Resultado Esperado
  - type: textarea
    attributes:
      label: ⚠️ Resultado Obtido
  - type: textarea
    attributes:
      label: 🚀 Solução Proposta
  - type: checkboxes
    attributes:
      label: ✅ Critérios de Aceitação
      options:
        - label: O código foi testado e validado
        - label: Commit segue convenções (`COMMIT_CONVENTION.md`)
```
✨ feature_request.yml
```yaml
name: "✨ Feature Request"
description: Propor uma nova funcionalidade ou melhoria
title: "✨ feat: [descrição curta]"
labels: ["enhancement"]
body:
  - type: textarea
    attributes:
      label: 🧩 Descrição
      description: Explica claramente a nova funcionalidade.
    validations:
      required: true
  - type: textarea
    attributes:
      label: 🧠 Contexto
      description: Justifica a necessidade da melhoria.
  - type: textarea
    attributes:
      label: 🚀 Solução Proposta
  - type: checkboxes
    attributes:
      label: ✅ Critérios de Aceitação
      options:
        - label: Código funcional e testado
        - label: Documentação atualizada
        - label: Commit segue convenções (`COMMIT_CONVENTION.md`)
```
♻️ refactor_request.yml
```yaml
name: "♻️ Refactor Suggestion"
description: Sugerir melhorias de código sem alterar a funcionalidade
title: "♻️ refactor: [descrição curta]"
labels: ["refactor"]
body:
  - type: textarea
    attributes:
      label: 🧩 Descrição
      description: O que deve ser refatorado?
    validations:
      required: true
  - type: textarea
    attributes:
      label: 🧠 Justificação
      description: Por que essa refatoração é necessária?
  - type: textarea
    attributes:
      label: 🚀 Solução Proposta
  - type: checkboxes
    attributes:
      label: ✅ Critérios de Aceitação
      options:
        - label: Código mais limpo e legível
        - label: Testes intactos e funcionando
```
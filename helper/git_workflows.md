# 📘 Git Workflows

O comando `git workflows` não é um comando executável, mas sim um **documento de boas práticas** que descreve fluxos de trabalho recomendados com Git.  
Ele mostra como organizar branches, integrar contribuições e manter um histórico bem fixe.

---

## 🔑 Função Principal

* Definir regras para organizar commits e branches.
* Explicar como usar merges, cherry-picks e rebases de forma saudável.
* Mostrar como gerenciar releases e manutenção.
* Orientar colaboração em projetos distribuídos.

---

## 🧠 Workflow = Fluxo de Trabalho

* Git não impõe um único fluxo de trabalho.
* O documento recomenda práticas usadas no próprio desenvolvimento do Git.
* O objetivo é **histórico limpo, colaboração eficiente e releases controlados**.

---

## 📋 Regras Fundamentais

### 1. **Separe mudanças**
- Faça commits pequenos e lógicos.
- Cada commit deve ser independente e funcional.
- Use `git rebase -i` para ajustar commits antes de publicar.

### 2. **Gerencie branches**
- Use `git merge` para integrar conjuntos completos de mudanças.
- Use `git cherry-pick` apenas quando for necessário aplicar commits específicos.
- Mantenha branches de integração bem definidas:
  - `maint` → correções críticas para a versão estável.
  - `main` → linha principal de desenvolvimento.
  - `next` → integração antecipada para testes e validação.
  - `seen` → branch temporária para mudanças experimentais ou ainda instáveis.


### 3. **Merging upwards**
- Sempre aplique correções no branch mais antigo que precisa delas.
- Depois, faça merges **para cima** (de `maint` → `main` → `next`).
- Se precisar aplicar correção de cima para baixo, use `git cherry-pick`.

### 4. **Topic branches**
- Crie branches separados para cada feature ou bugfix.
- Mantenha-os independentes até serem integrados.
- Evite misturar mudanças diferentes no mesmo branch.

### 5. **Throw-away integration**
- Para testar interação de vários tópicos, use branches descartáveis.
- Exemplo: `seen` é usado para testes temporários.
- Nunca baseie trabalho em branches descartáveis.

### 6. **Gerenciamento de releases**
- Releases de features vêm de `main`.
- Releases de manutenção vêm de `maint`.
- Use tags para marcar versões:
  ```bash
  git tag -s -m "Git X.Y.Z" vX.Y.Z main
  ```
- Crie branches de manutenção para versões antigas se necessário.

---

## 🔀 Workflows Distribuídos

### Merge workflow
- Usado por mantenedores.
- Propaga histórico completo (incluindo merges).
- Ferramentas principais:
  - `git push` → publica branches.
  - `git fetch` → traz branches remotos.
  - `git pull` → fetch + merge.

### Patch workflow
- Usado por contribuidores.
- Envia patches por e-mail.
- Ferramentas principais:
  - `git format-patch` → gera patches.
  - `git send-email` → envia patches.
  - `git am` → aplica patches recebidos.

---

## 📊 Casos de Uso Reais

### Publicar branch para revisão
```bash
git push origin feature-x
```

### Enviar patches por e-mail
```bash
git format-patch -M upstream..topic
git send-email --to=maintainer@example.com *.patch
```

### Importar patches recebidos
```bash
git am < patch.mbox
```

---

## ⚠️ Armadilhas Clássicas

* Fazer commits grandes e confusos → dificulta revisão.
* Misturar várias features em um único branch.
* Rebasear branches já publicados → quebra histórico compartilhado.
* Usar `git pull` sem entender que ele faz merge automático.

---

## 🧠 Dica

> **Organize seu trabalho em commits pequenos, use branches de tópicos e integre de forma controlada.**
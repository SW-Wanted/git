# 📘 Git Bisect — Guia de Referência

O comando `git bisect` é usado para **encontrar o commit que introduziu um bug** utilizando busca binária no histórico do repositório.

---

## 🔑 Função Principal

* Localizar commits problemáticos de forma eficiente.
* Usar busca binária para reduzir o número de testes.
* Marcar commits como **bons** ou **ruins**.
* Automatizar testes com scripts.

---

## 🧠 Conceito-Chave: Bisect = Debug no Histórico

* Você informa ao Git um commit **bom** (sem bug) e um commit **ruim** (com bug).
* O Git escolhe um commit intermediário.
* Você testa e marca como **bom** ou **ruim**.
* O processo continua até encontrar o commit exato que introduziu o problema.

👉 É como um “detetive” que divide o histórico em metades até achar o culpado.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git bisect start
git bisect bad        # commit com bug
git bisect good v1.0  # commit sem bug
 ├── Git escolhe commit intermediário
 ├── você testa e marca como good/bad
 └── repete até achar o primeiro commit ruim
```

---

## 📋 Operações Comuns

* `git bisect start` → inicia sessão de bisect.
* `git bisect bad` → marca commit atual como ruim.
* `git bisect good <commit>` → marca commit como bom.
* `git bisect reset` → encerra bisect e volta ao estado inicial.
* `git bisect skip` → pula commit não testável.
* `git bisect visualize` → mostra commits candidatos.
* `git bisect run <script>` → automatiza testes com script.

---

## 🌿 Exemplos Visuais

### Histórico inicial

```
A---B---C topic
     \
      D---E---F---G master
```

### Após `git bisect master`

```
A'--B'--C' topic
     \
      D---E---F---G master
```

---

## 🔀 Casos de Uso

### Encontrar commit que quebrou build

```bash
git bisect start
git bisect bad HEAD
git bisect good v2.6.13-rc2
```

### Automatizar testes

```bash
git bisect run make test
```

### Pular commits problemáticos

```bash
git bisect skip v2.5..v2.6
```

---

## 🛡️ Modos de Segurança

* `git bisect reset` → volta ao estado inicial.
* `git bisect skip` → evita commits não testáveis.
* `git bisect log` → mostra histórico de decisões.

---

## 📊 Casos de Uso Reais

* Localizar regressões em grandes projetos.
* Descobrir commits que introduziram falhas de performance.
* Identificar mudanças que quebraram compatibilidade.

---

## ⚠️ Armadilhas Clássicas

* Marcar commits incorretamente → resultado errado.
* Esquecer de resetar após terminar.
* Não automatizar testes → processo manual pode ser demorado.

---

## 🧠 Regra de Ouro

> **Use `git bisect` para encontrar regressões com precisão.  
> Combine com scripts para automatizar testes.**

---

## ✅ Em resumo

`git bisect` é o comando para **caçar commits problemáticos**.  
Ele reduz drasticamente o esforço de debug em grandes históricos.

Quem entende `git bisect`:

* encontra bugs com eficiência
* automatiza testes de regressão
* mantém qualidade em projetos grandes
* trabalha com clareza e precisão no histórico
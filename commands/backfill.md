# 📘 Git Backfill — Guia de Referência

O comando `git backfill` é usado para **baixar blobs faltantes em clones parciais**.  
Ele otimiza operações em repositórios clonados com filtros (como `--filter=blob:none`), permitindo recuperar objetos em lote em vez de múltiplas requisições individuais.

---

## 🔑 Função Principal

* Baixar blobs ausentes em clones parciais.
* Agrupar blobs relacionados para melhor compressão.
* Evitar lentidão em operações como `git blame` ou `git diff`.
* Integrar com sparse-checkout para baixar apenas o necessário.

---

## 🧠 Conceito-Chave: Backfill = Completar Objetos

* Clones parciais (`git clone --filter=blob:none`) não trazem blobs inicialmente.
* Operações que precisam de conteúdo (checkout, merge, blame) podem ficar lentas.
* `git backfill` permite **preencher blobs faltantes em lote**, otimizando performance.

👉 É como “completar lacunas” do repositório local.

---

## 🔍 O que acontece internamente?

Fluxo típico:

```text
git backfill
 ├── identifica blobs faltantes
 ├── agrupa por caminho
 ├── solicita blobs em lote ao servidor
 └── aplica delta-compression para otimizar transferência
```

---

## 📋 Operações Comuns

* `git backfill` → baixa todos os blobs alcançáveis a partir do HEAD.
* `git backfill --batch-size=5000` → define tamanho mínimo de lote.
* `git backfill --sparse` → baixa apenas blobs dentro do sparse-checkout.
* `git backfill --no-sparse` → ignora sparse-checkout e baixa todos os blobs.

---

## 🌿 Exemplos Visuais

### Clone parcial inicial

```
A---B---C commits
 \ 
  trees (sem blobs)
```

### Após `git backfill`

```
A---B---C commits
 \ 
  trees + blobs baixados em lote
```

---

## 🔀 Opções Úteis

* `--batch-size=<n>` → tamanho mínimo de lote (default: 16.000).
* `--sparse` → respeita sparse-checkout.
* `--no-sparse` → baixa todos os blobs, mesmo fora do sparse-checkout.

---

## 📊 Casos de Uso Reais

### Melhorar performance de blame/diff

```bash
git backfill
```

### Baixar apenas arquivos ativos no sparse-checkout

```bash
git backfill --sparse
```

### Controlar tamanho de lote

```bash
git backfill --batch-size=8000
```

---

## ⚠️ Armadilhas Clássicas

* Usar clone parcial sem backfill → operações ficam lentas.
* Baixar blobs desnecessários → aumenta consumo de rede e disco.
* Ignorar sparse-checkout → pode trazer arquivos irrelevantes.

---

## 🧠 Regra de Ouro

> **Use `git backfill` para completar blobs faltantes em clones parciais e otimizar operações.**

---

## ✅ Em resumo

`git backfill` é o comando para **preencher blobs ausentes em clones parciais**.  
Ele garante que operações como `checkout`, `merge` e `blame` sejam rápidas e eficientes.

Quem entende `git backfill`:

* evita lentidão em clones filtrados
* controla melhor o que baixar
* otimiza uso de rede e disco
* trabalha com eficiência em grandes repositórios

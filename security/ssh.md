# 🔐 SSH — Guia de Referência

O **SSH (Secure Shell)** é um protocolo criptográfico usado para **comunicação segura** entre máquinas numa rede insegura.
No contexto do GitHub, o SSH permite **autenticação forte baseada em chaves**, eliminando o uso de senha.

> 🔒 Desde 2021, o GitHub **aboliu autenticação por usuário + senha** para operações Git.

---

## 🎯 Objetivo do SSH no GitHub

* Autenticar o utilizador **sem senha**
* Garantir **segurança criptográfica**
* Facilitar automação (CI/CD, scripts, bots)
* Eliminar prompts repetitivos de autenticação
* Identificar **quais computadores** podem agir em teu nome

---

## 🧠 Modelo Mental

```
[ Teu computador ] --(chave privada)--> [ GitHub ]
                           ↑
                     nunca sai daqui
```

* 🔑 **Chave privada** → fica no teu computador
* 🔓 **Chave pública** → é cadastrada no GitHub
* GitHub **nunca recebe** a chave privada

---

## 🗝️ Tipos de Chaves SSH

### 🔹 Ed25519 (Recomendado)

* Mais seguro
* Mais rápido
* Chave menor
* Padrão moderno

### 🔹 RSA (Compatibilidade)

* Mais antigo
* Usado apenas se Ed25519 não for suportado

---

## 1️⃣ Gerar uma chave SSH

### 🔐 Opção recomendada (Ed25519)

```bash
ssh-keygen -t ed25519 -C "your_github_email@example.com"
```

### 🔐 Alternativa (RSA 4096 bits)

```bash
ssh-keygen -t rsa -b 4096 -C "your_github_email@example.com"
```

Durante o processo:

* Pressiona **Enter** para aceitar o caminho padrão
* Opcionalmente define uma **passphrase** (recomendado)

---

## 📁 Onde a chave é armazenada?

### Linux / macOS

```text
~/.ssh/
├── id_ed25519       # chave privada (NUNCA compartilhe)
└── id_ed25519.pub   # chave pública
```

### Windows

```text
C:\Users\SEU_USUARIO\.ssh\
```

⚠️ **Nunca envie ou publique a chave privada**

---

## 2️⃣ Cadastrar a chave no GitHub

1. Acesse:
   👉 [https://github.com/settings/ssh/new](https://github.com/settings/ssh/new)
2. Em **Title**, dê um nome identificável
   Ex: `Laptop Ubuntu`, `PC Casa`, `WSL`
3. Em **Key**, cole o conteúdo do ficheiro:

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
4. Clique em **Add SSH key**

---

## 3️⃣ Testar a conexão SSH

```bash
ssh -T git@github.com
```

Resposta esperada:

```text
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

✅ SSH configurado com sucesso.

---

## 🔄 Usar SSH em repositórios Git

### Clonar via SSH

```bash
git clone git@github.com:USERNAME/REPOSITORIO.git
```

### Ver URL atual

```bash
git remote -v
```

### Alterar HTTPS → SSH

```bash
git remote set-url origin git@github.com:USERNAME/REPOSITORIO.git
```

---

## 🧠 SSH vs HTTPS (GitHub)

| Critério     | SSH       | HTTPS         |
| ------------ | --------- | ------------- |
| Segurança    | ⭐⭐⭐⭐⭐     | ⭐⭐⭐⭐          |
| Senha        | ❌         | ❌ (token)     |
| Automação    | Excelente | Limitada      |
| CI/CD        | Ideal     | Menos prático |
| Profissional | ✅         | ⚠️            |

👉 **SSH é o padrão profissional**

---

## 🔐 SSH Agent

Evita digitar a passphrase repetidamente.

### Linux / macOS

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

### Windows (PowerShell)

```powershell
Start-Service ssh-agent
ssh-add $env:USERPROFILE\.ssh\id_ed25519
```

---

## ⚠️ Boas Práticas de Segurança

* ✔️ Uma chave por máquina
* ✔️ Use passphrase
* ❌ Nunca reutilize chave privada
* ❌ Nunca comite `.ssh/`
* ❌ Nunca envie chave privada por email/chat

---

## 🧭 Relação com Git

SSH **não é Git**, mas:

* é o **canal seguro** do Git
* é a **identidade criptográfica** do programador
* é a base de workflows modernos

Sem SSH:

* Git funciona
* Mas **não escala profissionalmente**

---

## ✅ Em resumo

* SSH substitui senhas no GitHub
* Autenticação é feita por chaves criptográficas
* Chave privada nunca sai da máquina
* SSH é essencial para workflows sérios
* Todo engenheiro deve dominar isso cedo
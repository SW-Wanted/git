# 🔏 GPG — Guia de Referência

**GPG (GNU Privacy Guard)** é um sistema de **criptografia assimétrica** usado para **assinar e verificar a autoria de commits e tags** no Git.

No GitHub, GPG garante que:

> *“Este commit foi realmente criado por quem diz ter criado.”*

---

## 🎯 Objetivo do GPG no Git

* Assinar commits e tags
* Provar **autenticidade** e **integridade**
* Evitar spoofing de identidade
* Tornar histórico **criptograficamente confiável**
* Ativar o selo **Verified** no GitHub

---

## 🧠 Modelo Mental

```
[ Commit ]
   │
   ├── conteúdo
   ├── metadata
   └── assinatura GPG  ← chave privada
```

* 🔑 **Chave privada** → assina localmente
* 🔓 **Chave pública** → publicada no GitHub
* GitHub **verifica**, mas **não assina**

---

## 🔐 GPG ≠ SSH

| Aspecto                | GPG                  | SSH               |
| ---------------------- | -------------------- | ----------------- |
| Finalidade             | Assinar commits/tags | Autenticar acesso |
| Prova identidade       | ✅                    | ❌                 |
| Segurança do histórico | ✅                    | ❌                 |
| Canal de transporte    | ❌                    | ✅                 |
| GitHub “Verified”      | ✅                    | ❌                 |

👉 **SSH autentica ações**
👉 **GPG autentica autoria**

---

## 1️⃣ Instalar GPG

### Linux (Ubuntu)

```bash
sudo apt install gnupg
```

### macOS

```bash
brew install gnupg
```

### Windows

* Instalar **Gpg4win**
* Inclui Kleopatra + gpg-agent

---

## 2️⃣ Gerar chave GPG

```bash
gpg --full-generate-key
```

Escolhas recomendadas:

* Tipo: `(1) RSA and RSA`
* Tamanho: `4096`
* Validade: `0` (ou 1–2 anos)
* Nome: teu nome real
* Email: **o mesmo do GitHub**
* Passphrase: **obrigatória**

---

## 3️⃣ Listar chaves e obter o Key ID

```bash
gpg --list-secret-keys --keyid-format=long
```

Exemplo:

```text
sec   rsa4096/ABCDEF1234567890
```

👉 **Key ID**: `ABCDEF1234567890`

---

## 4️⃣ Exportar chave pública

```bash
gpg --armor --export ABCDEF1234567890
```

Copia **todo o bloco**:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
...
-----END PGP PUBLIC KEY BLOCK-----
```

---

## 5️⃣ Cadastrar chave no GitHub

1. Acesse
   👉 [https://github.com/settings/gpg/new](https://github.com/settings/gpg/new)
2. Cole a chave pública
3. Confirme

---

## 6️⃣ Configurar Git para usar GPG

### Definir chave padrão

```bash
git config --global user.signingkey ABCDEF1234567890
```

### Assinar commits por padrão

```bash
git config --global commit.gpgSign true
```

### Assinar tags

```bash
git config --global tag.gpgSign true
```

---

## 7️⃣ Criar commit assinado

```bash
git commit -S -m "feat: implement login"
```

Ou automaticamente (se global ativo).

---

## 8️⃣ Verificar assinatura

```bash
git log --show-signature
```

No GitHub:

* Commit aparece como **Verified ✅**

---

## 🔁 GPG Agent (evitar digitar senha sempre)

### Linux / macOS

```bash
export GPG_TTY=$(tty)
```

Adicionar ao `.bashrc` / `.zshrc`

### Windows

* Gpg4win já inclui agente gráfico

---

## ⚠️ Problemas Comuns

### Commit não aparece como Verified

* Email do commit ≠ email da chave
* Chave não cadastrada no GitHub
* Commit antigo (não retroativo)

### Erro: `gpg failed to sign the data`

```bash
gpgconf --kill gpg-agent
```

---

## 🧠 GPG vs Assinatura SSH (GitHub)

GitHub permite **assinatura via SSH**, mas:

| Critério        | GPG       | SSH         |
| --------------- | --------- | ----------- |
| Portabilidade   | Alta      | Média       |
| Ecossistema     | Universal | GitHub-only |
| Padrão clássico | ✅         | ❌           |
| Transparência   | Melhor    | Boa         |

👉 **GPG ainda é o padrão de ouro**

---

## 🧭 Boas Práticas

* ✔️ Uma chave por identidade
* ✔️ Backup seguro da chave privada
* ✔️ Rotacionar chaves periodicamente
* ❌ Nunca perder a chave privada
* ❌ Nunca publicar a privada

---

## ✅ Em resumo

* GPG garante autoria real
* Commits assinados elevam o nível profissional
* GitHub mostra confiança pública
* SSH ≠ GPG (ambos são complementares)
* Histórico confiável é engenharia, não estética
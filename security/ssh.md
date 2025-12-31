# Configurar chave SSH para o Github

SSH é um protocolo para comunicação de dados com segurança.

O Github aboliu a autenticação somente com usuário e senha.

A ideia básica é cadastrar previamente quais computadores podem acessar o Github em seu nome. Outros computadores não conseguem acessar.

Para isto você deve:

## 1. Gerar uma chave SSH no seu computador
Isto cria uma nova chave SSH, usando o nome de e-mail fornecido como uma etiqueta.
```bash
ssh-keygen -t ed25519 -C "your_github_email@example.com"
```
ou
```bash
ssh-keygen -t rsa -b 4096 -C "your_github_email@example.com"
```
> Será gerado duas chaves, uma privada `id_ed25519` e outra pública `id_ed25519.pub`

Esta chave geralmente é salva em `C:\Users\YOUR_USERNAME\.ssh`
## 2. Cadastrar essa chave no seu Github
1. Clique em [Add new SSH Key](https://github.com/settings/ssh/new)
2. Cole no campo **Key** o conteúdo da chave pública `id_ed25519.pub`
# 📜 Licenças de Software

Licenciar um projeto é uma **decisão técnica, jurídica e estratégica**.  
Uma licença define **o que outras pessoas podem ou não fazer** com o seu código-fonte.

Sem uma licença explícita, aplicam-se automaticamente as leis padrão de **copyright**,
o que significa que **ninguém tem permissão legal** para usar, modificar ou redistribuir o código.

> 📌 Se o objetivo é código aberto (*open source*), **licenciar não é opcional — é obrigatório**.

---

## 🧠 O que é uma licença de software?

Uma licença de software é um **contrato legal** entre o autor e os utilizadores do código,
definindo:

- Direitos de uso
- Permissões de modificação
- Possibilidade de redistribuição
- Requisitos legais (atribuição, copyleft, etc.)
- Limitações de responsabilidade

---

## 🌍 Open Source e GitHub

Repositórios públicos no GitHub são frequentemente usados para compartilhar software open source.

⚠️ **Importante**:  
Publicar código em um repositório público **não o torna automaticamente open source**.

Sem licença:
- ❌ Outros não podem copiar
- ❌ Não podem modificar
- ❌ Não podem redistribuir
- ❌ Não podem usar legalmente

Com licença:
- ✔️ Regras claras
- ✔️ Segurança jurídica
- ✔️ Adoção facilitada
- ✔️ Reconhecimento automático pelo GitHub

---

## 🗂️ Onde colocar a licença?

Boas práticas recomendadas:

1. 📄 Arquivo `LICENSE` ou `LICENSE.md` na **raiz do repositório**
2. 📘 Referência à licença no `README.md`
3. 📁 (Opcional) Licenças organizadas em uma pasta dedicada

Este repositório adota a seguinte estrutura:

```text
licenses/
├── mit.md
├── apache-2.0.md
├── gpl-3.0.md
└── ...
````

---

## 🧭 Escolhendo a licença certa

O GitHub mantém o site **choosealicense.com**, que ajuda a escolher a licença adequada
com base em perguntas simples como:

* Quero permitir uso comercial?
* Quero obrigar que modificações também sejam open source?
* Quero o mínimo de restrições possíveis?

### Guia rápido:

| Objetivo                       | Licença recomendada |
| ------------------------------ | ------------------- |
| Máxima liberdade               | MIT                 |
| Proteção forte (copyleft)      | GPL                 |
| Copyleft fraco                 | LGPL                |
| Licença permissiva corporativa | Apache 2.0          |
| Domínio público                | Unlicense / CC0     |

---

## 🧩 Famílias de licenças (principais)

### 🔓 Licenças permissivas

Permitem quase tudo, com poucas obrigações.

* MIT
* BSD (2-Clause, 3-Clause)
* Apache 2.0
* ISC
* Zlib

### 🔒 Licenças copyleft

Exigem que trabalhos derivados mantenham a mesma licença.

* GPL v2 / v3
* AGPL
* LGPL (copyleft fraco)

### 🎨 Conteúdo não-código

Usadas para documentação, textos, imagens e fontes.

* Creative Commons (CC-BY, CC-BY-SA, CC0)
* SIL Open Font License (OFL)

---

## 🔍 Identificação automática de licenças

O GitHub utiliza a ferramenta **Licensee** para detectar licenças automaticamente.

Para garantir que a licença seja reconhecida:

* Use o **texto oficial** da licença
* Evite modificações no arquivo LICENSE
* Use licenças reconhecidas pelo **Choose a License**

Se houver múltiplas licenças ou exceções, documente no README.

---

## 🔗 Referências de licenças neste repositório

Licenças documentadas:

* 📄 [MIT License](../licenses/mit.md)

> Outras licenças serão adicionadas progressivamente.

---

## ⚠️ Isenção de responsabilidade

Este material tem **fins educacionais**.
Não substitui aconselhamento jurídico profissional.

Se o projeto envolver:

* Uso comercial
* Patentes
* Distribuição corporativa
* Jurisdições específicas

➡️ Consulte um advogado especializado em software.

---

## 📚 Leitura adicional

* [https://choosealicense.com](https://choosealicense.com)
* GitHub Open Source Guides
* The Legal Side of Open Source
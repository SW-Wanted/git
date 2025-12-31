# 📜 Licenças de Software

Uma licença open source **protege quem contribui e quem usa**.  
Projetos sem licença são, na prática, **código fechado por padrão**.

> Empresas e desenvolvedores experientes **não usam projetos sem licença**.

---

## 🧠 Por que escolher uma licença?

Sem uma licença explícita:

- ❌ Ninguém pode usar seu código legalmente
- ❌ Não pode modificar
- ❌ Não pode redistribuir
- ❌ Não pode colaborar com segurança jurídica

Com uma licença:

- ✔️ Direitos e deveres claros
- ✔️ Proteção legal
- ✔️ Adoção comunitária
- ✔️ Reconhecimento automático pelo GitHub

---

## 🧭 Como escolher uma licença open source

A escolha depende **do seu contexto**.

### ❓ Qual situação melhor descreve o seu projeto?

---

## 🤝 Preciso trabalhar em uma comunidade

Se você contribui ou depende de um projeto existente:

➡️ **Use a licença da comunidade**

Isso não é apenas conveniência — muitas vezes é **obrigatório**.

### Exemplos de preferências comunitárias

| Comunidade / Ecossistema | Licença preferida |
|-------------------------|------------------|
| Apache Foundation | [Apache License 2.0](./../licenses/apache-2.0.md) |
| CNCF (Cloud Native) | [Apache License 2.0](./../licenses/apache-2.0.md) |
| GNU | GNU GPLv3 |
| npm | [MIT](./../licenses/apache-2.0.md) ou ISC |
| OpenBSD | ISC |
| Rust crates | [MIT](./../licenses/mit.md) **ou** [Apache 2.0](./../licenses/apache-2.0.md) |
| WordPress plugins | GPLv2 ou posterior |
| Joomla extensions | GPLv2 (PHP) |

📌 **Regra de ouro**:  
> Se o projeto base tem licença, **herde-a**.

Se uma dependência **não tiver licença**, peça educadamente aos mantenedores que adicionem uma.

---

## ⚡ Quero algo simples e permissivo

### 👉 Licença MIT

A **MIT License** é curta, direta e extremamente popular.

Ela permite:
- Uso comercial
- Modificação
- Distribuição
- Código fechado derivado

Exige apenas:
- Preservar o aviso de copyright
- Preservar o texto da licença

Usada por:
- Babel
- .NET
- Rails

💡 Ideal para:
- Bibliotecas
- Ferramentas
- Projetos educacionais
- Máxima adoção

---

## 🔁 Eu me importo em compartilhar melhorias

### 👉 GNU GPLv3

A **GPLv3** garante que:
- O código continue livre
- Modificações **também sejam open source**
- Direitos de patentes sejam concedidos

Ela **proíbe**:
- Distribuição de versões fechadas

Usada por:
- Ansible
- Bash
- GIMP

📌 Característica central:
> *Copyleft forte*: quem redistribui **deve** compartilhar o código-fonte.

📄 Licença completa:
➡️ (a adicionar em `licenses/gpl-3.0.md`)

💡 Ideal para:
- Software livre ideológico
- Ferramentas fundamentais
- Projetos comunitários de longo prazo

---

## ❓ E se nenhuma dessas funcionar?

---

## 📂 Meu projeto não é software

Licenças open source **não se limitam a código**.

### 📊 Dados, mídia, datasets
- CC0-1.0
- CC-BY-4.0
- CC-BY-SA-4.0

⚠️ Creative Commons **não é recomendada para software**.

### 📘 Documentação
- Pode usar a **mesma licença do software**
- Ou uma licença Creative Commons

### 🔤 Fontes
- SIL Open Font License 1.1 (OFL)

### 🔧 Hardware
- CERN-OHL-P (permissiva)
- CERN-OHL-W (copyleft fraco)
- CERN-OHL-S (copyleft forte)

📌 Projetos mistos podem usar **múltiplas licenças**, desde que isso esteja **claramente documentado**.

---

## 🧩 Quero mais opções

Licenças open source formam um **espectro**, do mais restritivo ao mais permissivo:

```
AGPL → GPL → LGPL → MPL → Apache → MIT → BSD → Unlicense
```

Algumas licenças importantes:

- GNU AGPLv3 (copyleft máximo, rede = distribuição)
- GNU GPLv3
- GNU LGPLv3
- Mozilla Public License 2.0
- Apache License 2.0
- MIT License
- Boost Software License
- Unlicense (domínio público)

📁 Todas devem ser documentadas individualmente em: `licenses/`

---

## 🚫 Não quero escolher uma licença

Então acontece o seguinte:

- Seu código fica sob **copyright exclusivo**
- Outros **não podem usar legalmente**
- Colaborações ficam juridicamente frágeis

Mesmo no GitHub:
- Outros podem **ver e fazer fork**
- Mas **não podem usar, modificar ou redistribuir**

📌 Se isso for intencional:
- Declare explicitamente no README
- Considere um acordo de contribuidor (CLA)

Se a ideia for **abrir mão totalmente do copyright**:
- Use **Unlicense** ou **CC0**

---

## 🗂️ Onde colocar a licença no repositório

Boas práticas:

1. 📄 `LICENSE` ou `LICENSE.md` na raiz
2. 📘 Referência no `README.md`
3. 📁 Pasta `licenses/` para textos organizados

---

## ⚠️ Aviso legal

Este guia é **educacional**.
Não substitui aconselhamento jurídico.

Para projetos com:

* Uso comercial
* Patentes
* Contratos
* Distribuição internacional

➡️ Consulte um advogado especializado.

---

## 📚 Referências

* [https://choosealicense.com](https://choosealicense.com)
* GitHub Open Source Guides
* GNU Licenses — [https://www.gnu.org/licenses/](https://www.gnu.org/licenses/)

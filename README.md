## 🗳️ Diagnóstico de Reciclagem — Largo do Arouche

### 📍 Descrição

Este projeto faz parte do **Programa de Extensão UFMS Digital**, dentro do **Projeto Integrador I – Curso de Ciência de Dados**.
Seu objetivo é **coletar dados sobre a separação e destinação de resíduos sólidos** na região do **Largo do Arouche**, em São Paulo (SP), abrangendo **condomínios, comércios e catadores locais**.

As informações coletadas serão utilizadas para:

* Mapear práticas de separação e coleta seletiva;
* Quantificar volumes e tipos de resíduos gerados;
* Identificar gargalos logísticos e educacionais;
* Apoiar a criação de **rotas otimizadas de coleta** e **ações comunitárias sustentáveis**.

---

## ⚙️ Estrutura do projeto

| Arquivo              | Função                                                                          |
| -------------------- | ------------------------------------------------------------------------------- |
| `index.html`         | Contém o formulário principal (interface para entrevistas e coleta de dados).   |
| `style.css`          | Define o estilo visual e a responsividade do formulário.                        |
| `Google Apps Script` | Recebe os dados enviados e grava automaticamente em uma planilha Google Sheets. |

---

## 🧩 Campos do formulário

O formulário coleta as seguintes informações:

1. **Endereço (número)**
2. **Tipo de local** (Comercial, Residencial, Misto)
3. **Separação de resíduos** (Sim, Às vezes, Não)
4. **Responsável pela separação**
5. **Tipos de resíduos separados** (checkbox múltiplo)
6. **Destino dos resíduos**
7. **Controle de volume gerado**
8. **Volume estimado (kg/semana)**
9. **Capacitação sobre separação correta**
10. **Nível de informação da comunidade**
11. **Conhecimento das políticas da prefeitura**
12. **Iniciativas comunitárias conhecidas**
13. **Maior dificuldade na separação**
14. **Observações adicionais**

Cada envio cria **uma nova linha** na planilha Google Sheets.

---

## ☁️ Integração com Google Sheets

O sistema utiliza um **endpoint público do Google Apps Script** para armazenar os dados.

### Exemplo do script:

```js
function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Respostas");
  const data = JSON.parse(e.postData.contents);
  const timestamp = new Date();

  sheet.appendRow([
    timestamp,
    data.endereco,
    data.tipo,
    data.separacao,
    data.responsavel,
    data.tipos,
    data.destino,
    data.controle,
    data.volume,
    data.capacitacao,
    data.info,
    data.politicas,
    data.iniciativas,
    data.dificuldade,
    data.observacoes
  ]);

  return ContentService
    .createTextOutput(JSON.stringify({ status: "success" }))
    .setMimeType(ContentService.MimeType.JSON);
}
```

---

## 🚀 Hospedagem

O site pode ser publicado gratuitamente em plataformas como:

* [**Netlify**](https://www.netlify.com/)
* [**Vercel**](https://vercel.com/)
* [**GitHub Pages**](https://pages.github.com/)

### Passos:

1. Faça upload de `index.html` e `style.css`.
2. No HTML, substitua `SUA_URL_DO_APPS_SCRIPT_AQUI` pela URL gerada ao publicar o script.
3. Abra o link do seu site e comece a coletar dados diretamente pelo celular.

---

## 💻 Tecnologias utilizadas

* **HTML5** e **CSS3**
* **JavaScript (Fetch API)**
* **Google Apps Script**
* **Google Sheets**
* **Netlify (hospedagem gratuita)**

---

## 📱 Recursos de design

* Responsividade total (funciona em celulares e tablets)
* Fonte **Roboto (Google Fonts)**
* Estilo limpo, leve e acessível
* Checkboxes estilizados e alinhados em duas colunas
* Feedback visual de envio (mensagem “✅ Enviado com sucesso!”)

---

## 👨‍💻 Autor

**Sabuat Urbina Ribeiro**
Projeto Integrador I – Curso de Ciência de Dados (UFMS Digital)
São Paulo – 2025

📧 *Contato acadêmico disponível sob solicitação.*

---

## 📄 Licença

Este projeto é distribuído sob a licença **MIT**, permitindo livre uso e modificação para fins acadêmicos e comunitários, desde que mantidos os créditos do autor.

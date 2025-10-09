# Automação de Lembrete de Escala de Sexta-Feira

Este script automatiza o envio de e-mails de lembrete para os colaboradores escalados a trabalhar presencialmente na sexta-feira. Ele foi desenvolvido em **Python** e utiliza **PySpark** para consulta de dados e **SMTP** para envio de e-mails.

---

## 🧩 Funcionalidades

- Consulta automática à tabela `escala_sexta_feira_conteudo` no ambiente Spark.
- Verifica a data da próxima sexta-feira.
- Envia e-mails personalizados para cada colaborador escalado.
- Adiciona cópias (CC) automáticas para responsáveis.

---

## ⚙️ Tecnologias Utilizadas

- **Python 3**
- **PySpark**
- **smtplib** (para envio de e-mails)
- **email.mime.text** (para formatar o corpo do e-mail)
- **dbutils.secrets** (para gerenciamento seguro da senha SMTP)

---

## 📦 Dependências

Instale as dependências necessárias (caso não estejam disponíveis):

```bash
pip install pyspark
```

---

## 🚀 Como Executar

1. Certifique-se de estar no ambiente Databricks (ou outro compatível com `dbutils.secrets`).
2. Configure o **scope** de segredos com a senha do e-mail:
   ```python
   dbutils.secrets.put(scope="smtp", key="password", string_value="SUA_SENHA_AQUI")
   ```
3. Execute o script Python:
   ```bash
   python lembrete_escala.py
   ```

---

## ✉️ Estrutura do E-mail

**Assunto:** Lembrete de Escala de Conteúdo [Sexta-Feira]

**Corpo:**
```
Olá {nome},

Você está escalado(a) para trabalhar presencialmente esta sexta-feira! ({data_sexta}).
```

**Cópias (CC):**
- xxxxx@bemol.com.br
- xxxxx@bemol.com.br

---

## 🔒 Segurança

As credenciais de e-mail (senha SMTP) **não devem ser armazenadas diretamente no código**. Elas são acessadas de forma segura via `dbutils.secrets`.

---

## 👨‍💻 Autor

**Fabricio Baraúna Macedo**  
E-mail: fabriciomacedo@bemol.com.br  
Empresa: Bemol S.A.

---

## 🗓️ Última atualização
09/10/2025

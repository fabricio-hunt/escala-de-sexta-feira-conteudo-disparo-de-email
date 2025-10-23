# Automação de Lembrete de Escala de Sexta-Feira

Este script automatiza o envio de e-mails de lembrete para colaboradores escalados para trabalho presencial na sexta-feira.  
Foi desenvolvido em **Python** com **PySpark** e integração SMTP para envio de e-mails com corpo HTML responsivo.

---

## 🧩 Funcionalidades

- Consulta automática à tabela `escala_sexta_feira_conteudo` no ambiente Spark.
- Calcula a data alvo automaticamente (dia seguinte à execução do script).
- Gera e envia e-mails personalizados com layout responsivo em HTML.
- Inclui cópias automáticas (CC) para os responsáveis definidos.
- Exibe logs de envio no terminal.

---

## ⚙️ Tecnologias Utilizadas

- **Python 3**
- **PySpark**
- **smtplib** – envio de e-mails SMTP.
- **email.mime.text** – formatação HTML do corpo do e-mail.
- **dbutils.secrets** – gerenciamento seguro da senha SMTP.

---

## 📦 Dependências

Para garantir o funcionamento correto, instale o PySpark caso ainda não esteja disponível:

```bash
pip install pyspark
```

---

## 🚀 Como Executar

1. Certifique-se de estar executando o script em um ambiente Databricks (ou compatível com `dbutils.secrets`).
2. Configure o **scope** com a senha de e-mail:
   ```python
   dbutils.secrets.put(scope="smtp", key="password", string_value="SUA_SENHA_AQUI")
   ```
3. Execute o script:
   ```bash
   python lembrete_escala.py
   ```
4. O sistema enviará e-mails automaticamente para todos os colaboradores escalados na data correspondente.

---

## ✉️ Estrutura do E-mail

**Assunto:** Lembrete de Escala de Conteúdo [Sexta-Feira]

**Corpo (HTML):**
```
Olá {nome},

Você está escalado(a) para trabalho presencial nesta sexta-feira, dia {data_sexta}.
Este agendamento não permanece válido em caso de feriados ou pedidos de troca.

Dica: se houver dúvidas, responda este e-mail ou contate seu gestor imediato.
```

O e-mail também contém:
- Logotipo oficial da Bemol.
- Botão “Ver detalhes da escala” com link direto para o arquivo no SharePoint.
- Estilo responsivo para celulares e desktops.
- Rodapé informando que a mensagem é automática.

---

## 📬 Cópias Automáticas (CC)

- alinesantiago@bemol.com.br  
- conteudobol@bemol.com.br

---

## 🔒 Segurança

As credenciais de e-mail **não devem ser armazenadas diretamente no código**.  
Elas são acessadas de forma segura via `dbutils.secrets.get(scope="smtp", key="password")`.

---

## 🧠 Lógica de Funcionamento

1. O script obtém a data de hoje e soma +1 dia para identificar a sexta-feira alvo.
2. Realiza consulta na tabela `escala_sexta_feira_conteudo` usando SparkSQL.
3. Para cada colaborador encontrado:
   - Gera o e-mail com HTML personalizado.
   - Envia a mensagem via servidor SMTP do Outlook (`smtp.office365.com`).
4. Exibe no console o nome e o e-mail de cada colaborador notificado.

---

## 🧑‍💻 Autor

**Fabricio Baraúna Macedo**  
E-mail: fabriciomacedo@bemol.com.br  
Empresa: Bemol S.A.

---

## 🗓️ Última atualização
23/10/2025

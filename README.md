README.md
# Instruções para executar o projeto de Chat com IA — UC10

Este projeto utiliza **Streamlit** para a interface, **Groq** para respostas de IA, **ChromaDB** e **Sentence Transformers** para RAG (consulta a documentos), **SQLite** para histórico e **MySQL/MariaDB** para consultas ao banco de dados.

## 1. Pré-requisitos

* Python 3.13 instalado (ou ambiente Python compatível com as bibliotecas).
* MySQL/MariaDB em execução caso deseje utilizar as consultas ao banco.
* Uma chave de API da Groq.
* Terminal do **VS Code** ou **PowerShell** aberto na pasta que contém `app.py`.

## 2. Instale as bibliotecas

Execute no terminal:

```
c:\python313\python.exe -m pip install streamlit groq python-dotenv pandas pymupdf openpyxl chromadb sentence-transformers mysql-connector-python sqlglot
```

Se o comando `python` já aponta para a versão correta, você também pode usar:

```
python -m pip install streamlit groq python-dotenv pandas pymupdf openpyxl chromadb sentence-transformers mysql-connector-python sqlglot
```

> As bibliotecas `os`, `json`, `sqlite3`, `uuid`, `hashlib`, `re`, `datetime`, `io` e `pathlib` já vêm com o Python.

## 3. Configure o arquivo `.env`

Crie um arquivo chamado `.env` na **mesma pasta do `app.py`** e configure os dados da sua instalação:

```
GROQ_API_KEY=coloque_sua_chave_aqui
GROQ_MODEL=openai/gpt-oss-20b

MYSQL_HOST=127.0.0.1
MYSQL_PORT=3306
MYSQL_USER=root
MYSQL_PASSWORD=
MYSQL_DATABASE=lojatech

# Opcional: restringe as tabelas que a IA pode consultar.
# Use nomes existentes no banco; deixe comentado para não aplicar filtro.
# MYSQL_ALLOWED_TABLES=pedidos,produtos,clientes,itens_pedido

```

**Atenção:** nunca compartilhe sua chave de API ou senha do banco. Não envie o arquivo `.env` para repositórios públicos. O usuário do MySQL utilizado pela IA deve ter **apenas permissão SELECT** nas tabelas autorizadas.

## 4. Execute a aplicação

Na pasta do projeto, utilize:

```
c:\python313\python.exe -m streamlit run app.py --server.fileWatcherType none
```

Ou, se a versão correta do Python estiver configurada no terminal:

```
python -m streamlit run app.py --server.fileWatcherType none
```

Abra no navegador o endereço que aparecer no terminal, geralmente:

```
http://localhost:8501
```

Para encerrar a aplicação, pressione **Ctrl + C** no terminal.

## 5. Como utilizar o chat

1. **Documentos (RAG):** envie arquivos PDF, TXT, CSV ou XLSX e clique em  **Indexar arquivos** ; depois faça perguntas sobre os documentos.
2. **MySQL Loja Tech:** utilize os relatórios disponíveis ou escreva perguntas no chat para que a IA gere consultas SQL de leitura automaticamente.
3. **Ambos:** combine documentos e resultados do banco; quando necessário, habilite a consulta automática ao MySQL.
4. **Histórico:** selecione conversas antigas, crie novas conversas ou exporte o histórico.

A aplicação cria a pasta `dados_locais` para armazenar o histórico SQLite e os dados persistentes do ChromaDB.

## 6. Solução de problemas comuns

| Mensagem ou problema                  | O que verificar                                                                                        |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| `ModuleNotFoundError`               | Execute novamente a instalação usando o**mesmo Python**que roda o Streamlit.                   |
| `GROQ_API_KEY`não encontrada       | Confira o nome da variável no `.env`e se o arquivo está na pasta do projeto.                       |
| Erro de conexão MySQL                | Verifique se o MySQL/MariaDB está ligado e se host, porta, usuário e senha estão corretos.          |
| `Não há tabelas disponíveis`     | Confira `MYSQL_DATABASE`, as permissões de `lojatech_leitura`e o filtro `MYSQL_ALLOWED_TABLES`. |
| Groq: erro `413`ou limite de tokens | Reduza a quantidade de contexto/documentos enviados ou aguarde a renovação do limite da conta.       |
| Porta `8501`ocupada                 | Pare outra instância do Streamlit ou use `--server.port 8502`.                                      |

## 7. Comando rápido

Depois de configurar o `.env` e instalar as bibliotecas, basta executar:

```
c:\python313\python.exe -m streamlit run app.py --server.fileWatcherType none
```

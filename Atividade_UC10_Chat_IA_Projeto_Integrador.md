# Testes, validação e adaptação do chat com IA ao projeto integrador

## Objetivo da atividade

Executar, testar e adaptar o projeto de Chat com Inteligência Artificial desenvolvido em aula, utilizando **Python, Streamlit, Groq, ChromaDB, SQLite e MySQL**.

Cada grupo deverá transformar o exemplo utilizado em aula em um **assistente inteligente relacionado ao tema de seu Projeto Integrador**, capaz de consultar informações relevantes, responder perguntas e armazenar o histórico das conversas.

Também será necessário analisar o banco SQLite gerado pela aplicação e verificar como as conversas se relacionam com as mensagens.

## Etapa 1 – Executar e testar a aplicação

No terminal do VS Code, execute:

```powershell
c:\python313\python.exe -m streamlit run app.py --server.fileWatcherType none
```

Depois, abra `http://localhost:8501` no navegador.

1. Crie uma nova conversa.
2. Envie pelo menos **cinco perguntas** para a IA.
3. Verifique se as respostas correspondem às perguntas.
4. Crie uma segunda conversa e faça novas perguntas.
5. Retorne à primeira conversa e confirme se o histórico foi preservado.
6. Exporte o histórico usando a funcionalidade da aplicação.

**Resultado esperado:** criar conversas, recuperar mensagens e manter o histórico armazenado.

## Etapa 2 – Testar a leitura de documentos com RAG

Selecione **pelo menos dois arquivos** relacionados ao Projeto Integrador (PDF, TXT, CSV ou Excel).

1. Faça o upload dos documentos.
2. Execute a indexação.
3. Verifique se os documentos foram adicionados ao ChromaDB.
4. Elabore **cinco perguntas** baseadas nos arquivos.
5. Compare as respostas com o conteúdo original e anote eventuais erros ou informações não encontradas.

**Resultado esperado:** a IA deverá localizar informações relevantes sem inventar dados ausentes dos documentos.

## Etapa 3 – Testar consultas inteligentes ao MySQL

Utilize o banco Loja Tech ou uma base de testes autorizada e formule **cinco perguntas** que exijam consultas ao banco.

**Exemplos de perguntas:**

- Qual é o total de produtos cadastrados?
- Quais produtos possuem maior preço?
- Qual foi o faturamento total?
- Quantos pedidos foram feitos em determinado período?
- Quais produtos possuem maior quantidade em estoque?

Para cada pergunta, registre a pergunta, o SQL gerado pela IA, o resultado apresentado e se ele confere com os dados do banco.

> **Atenção:** execute somente consultas de leitura (`SELECT`). Não use operações de alteração ou exclusão; o usuário do MySQL destinado à IA deve ter permissão apenas de leitura.

## Etapa 4 – Verificar o banco SQLite gerado

Encontre o arquivo `dados_locais/historico.sqlite3` na pasta do projeto:

```text
projeto/
├── app.py
├── .env
└── dados_locais/
    ├── historico.sqlite3
    └── chroma/
```

Acesse o visualizador online: **[SQLite Viewer](https://sqliteviewer.app/#/historico.sqlite3)**.

Abra o arquivo local `historico.sqlite3` usando a opção de selecionar arquivo ou arrastando-o para a página. O endereço do site não acessa automaticamente o arquivo de seu computador.

![1792741060914](image/Atividade_UC10_Chat_IA_Projeto_Integrador/1792741060914.${ext})

### Tabelas a analisar

**`conversas`** — identificar as colunas `id`, `titulo` e `criado_em`.

**`mensagens`** — identificar as colunas `id`, `conversa_id`, `papel`, `conteudo` e `criado_em`.

### Questões para responder

1. Qual é a finalidade da tabela `conversas`?
2. Qual é a finalidade da tabela `mensagens`?
3. Qual campo estabelece o relacionamento entre elas?
4. Qual é a diferença entre os papéis `user` e `assistant`?
5. O que acontece com os registros quando uma nova conversa é criada?
6. As mensagens permanecem armazenadas depois de fechar e reabrir a aplicação?
7. Por que o projeto usa SQLite para o histórico e ChromaDB para os documentos?

**Registre capturas de tela** das duas tabelas e exemplos dos registros gerados. Utilize dados fictícios, sem expor dados sensíveis.

## Etapa 5 – Adaptar a aplicação ao Projeto Integrador

Adapte o chat ao problema, público-alvo e objetivos do PI do seu grupo.

1. **Personalização:** altere o título, a descrição e a identidade visual para representar o PI.
2. **Base de conhecimento:** indexe documentos relevantes ao tema do projeto.
3. **Banco de dados:** se aplicável, conecte o banco do PI ou uma base de testes representativa.
4. **Consultas inteligentes:** faça perguntas relacionadas à problemática e aos dados do PI.
5. **Testes:** elabore ao menos **dez perguntas específicas** e avalie as respostas.
6. **Histórico:** confirme se as conversas continuam sendo gravadas corretamente no SQLite.

**Resultado esperado:** o assistente deixa de ser um exemplo genérico da Loja Tech e passa a oferecer funcionalidades relacionadas ao PI do grupo.

## Etapa 6 – Testes finais e validação

Marque cada item conforme os testes forem concluídos:

- [ ] A aplicação Streamlit inicia corretamente.
- [ ] Uma nova conversa pode ser criada.
- [ ] Perguntas e respostas são registradas no SQLite.
- [ ] O histórico permanece disponível após reiniciar a aplicação.
- [ ] Documentos podem ser enviados e indexados.
- [ ] A IA responde com base nos documentos enviados.
- [ ] As consultas MySQL de leitura são executadas corretamente.
- [ ] O SQL gerado pela IA pode ser visualizado e conferido.
- [ ] A interface está adaptada ao tema do Projeto Integrador.
- [ ] Perguntas sem resposta disponível são tratadas adequadamente.

## Etapa 7 – Entrega da atividade

Cada grupo deverá entregar um relatório com integrantes, nome do Projeto Integrador, adaptações realizadas e resultados dos testes.

**Itens obrigatórios:**

- Capturas de tela da aplicação e de respostas da IA.
- Capturas das tabelas `conversas` e `mensagens` abertas no SQLite Viewer.
- Registro das **dez perguntas** usadas para validar a versão adaptada ao PI.
- Explicação das alterações feitas, dificuldades encontradas e soluções adotadas.
- Link do repositório GitHub contendo código e documentação.

## Resultado esperado

Ao concluir a atividade, o grupo deverá apresentar uma **versão funcional e personalizada do assistente inteligente**, demonstrando integração entre IA generativa, recuperação de informações via RAG, consultas ao MySQL e persistência do histórico em SQLite.

A atividade deve contribuir para a evolução técnica do Projeto Integrador e para a aplicação prática dos conhecimentos desenvolvidos na UC10.

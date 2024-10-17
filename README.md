# Desafio Devops

Correções feitas no arquivos.

Pasta mysql

- Arquivo init.sql alterado a query **primary key** para **PRIMARY KEY**

Pasta nginx

- Arquivo Dockerfile do nginx, adicionado o COPY para o path correto do arquivo.
- Arquivo nginx.conf adicionado o bloco server dentro do bloco http e adicionado o bloco events.

Pasta node

- Correção no arquivo connectionDb.js onde a variável node_db estava nodedb.
- Atualização da versão do node de 15 para versão 18.
- Atualização no Dockerfile adicionado dependências e instalação de dependências e inicialização da aplicação.
- Atualização no docker-compose para adição da seção networks e adição do driver bridge para comunicação entre os containers.

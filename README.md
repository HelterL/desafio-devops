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

Subindo aplicação no Kubernetes

MYSQL

- Criação de uma namespace
- Criação de uma Configmap com os dados da Database name e do password root (Não é o cenário ideal)
- Criação de um service headless na porta 3306
- Criação de um StatefulSet para subir o banco mysql
- Não consegui automatizar a query da criação da tabela peoples, nisso tive que criar uma imagem custom para o banco e subir para o dockerhub(Não é o ideal)

NGINX

- Criação de uma Namespace
- Criação de uma ConfigMap contendo a configuração do nginx.conf
- Criação de um Deployment para o serviço
- Criação de um serviço ClusterIP para o Nginx

Aplicação NODE

- Criação de uma namespace
- Criação de uma secret contendo os seguintes dados DATABASE,PASSWORD, HOST e USER
- Criação de um Deployment para a aplicação
- Criação de um serviço ClusterIP para a aplicação.

Os testes foram feitos utilizando a ferramenta kind que significa kubernetes in docker que provisiona um cluster local e que é utilizado para ambientes de testes e estudos.

Para rodar os manifestos bastar criar um cluster simples com kind, aplicar os manifestos e rodar o seguinte comando.

kubectl port-forward svc/desafio-app-service 3000:3000 -n desafio-app

Pontos a serem melhorados em um ambiente real

- Envio das imagens para um repositório como ECR, ACR e etc.
- Criação de uma pipeline para build e envio da imagem docker
- Para testes em uma cloud como AWS, Azure ou GCP, criar o serviço da aplicação Node como LoadBalancer ou instalar o nginx-ingress e criar um ingress para a aplicação e apontar o host em um serviço de DNS como Cloudflare, Route53 e etc.

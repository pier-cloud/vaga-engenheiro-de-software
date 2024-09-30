#Teste Engenheiro de Software - Pier Cloud

Neste teste serão avaliados seus conhecimentos em desenvolvimento de software, arquitetura, organização e estrutura de código.

##O Desafio

Você é Engenheiro de Software de uma empresa de Marketplace de venda de produtos na internet. Essa empresa possui diversos vendedores divulgando seus produtos dentro do marketplace. 
A empresa precisa de um relatório consolidado de vendas por vendedor. Para isso, você precisa criar uma aplicação que consuma a API de vendas e consolide todas as vendas em um único relatório para cada vendedor, no final exporte esse relatório em um arquivo CSV.
A aplicação precisa ser capaz de escalonar para um grande volume de vendedores, apesar de nessa API de teste ter poucos vendedores.
Sua aplicação deve utilizar boas práticas de programação, ser escalável e de fácil manutenção. Também é necessário utilizar um broker de mensageria para comunicação entre os serviços e garantir a escalabilidade da aplicação.

##Requisitos
Esses requisitos são obrigatórios e devem ser desenvolvidos para a entrega do teste.

###Requisitos técnicos:
  - Linguagem de programação: Python, Go ou Node
  - Utilizar Brocker de mensageria (Nats, RabbitMQ, Kafka, etc)
  - Utilizar README.md para documentação do projeto

###Requisitos Funcionais:
  - Consumir a API de Vendedores e publicar em um tópico do broker de mensageria.
  - Consumir o tópico do broker de mensageria, consumir a API de vendas, clientes e produtos, e consolidar os dados em um relatório por vendedor.
  - Exportar o relatório em um arquivo CSV para cada vendedor.

##Arquitetura
A aplicação deve ser dividida em 2 serviços:
  - Serviço 1 (Job): Deve consumir a API de Vendedores e publicar em um tópico do broker de mensageria.
  - Serviço 2 (Worker): Deve consumir o tópico do broker de mensageria, consumir a API de vendas, clientes e produtos, depois consolidar os dados em um relatório por vendedor. Ao final, exportar o relatório em um arquivo CSV para cada vendedor.

##Dados

  - API de Vendedores: https://66ec84422b6cf2b89c5eabf1.mockapi.io/piercloud/api/v1/vendedores
  Resposta:
  ```json
  [
      {
          "name": "June Kuphal",
          "telefone": "(875) 478-1340",
          "id": "1"
      }
  ]
  ```
  
  
  - API de Clientes: https://66ec84422b6cf2b89c5eabf1.mockapi.io/piercloud/api/v1/clientes
  Resposta:
  ```json
  [
      {
          "name": "Dr. Kenneth Toy",
          "telefone": "(329) 491-0744",
          "email": "Edythe.Runolfsson@yahoo.com",
          "id": "1"
      }
  ]
  ```
  
  - API de Produtos: https://66ec84422b6cf2b89c5eabf1.mockapi.io/piercloud/api/v1/produtos
  Resposta:
  ```json
  [
      {
          "created_at": "2024-09-30T00:45:52.367Z",
          "name": "Recycled Steel Computer",
          "kind": "Shoes",
          "price": "64.00",
          "sku": "2188",
          "vendedor_id": "1",
          "id": "1"
      }
  ]
  
  - API de Vendas: https://66ec84422b6cf2b89c5eabf1.mockapi.io/piercloud/api/v1/vendas
  Resposta:
  ```json
  [
      {
          "created_at": "2024-09-30T17:55:04.391Z",
          "vendedor_id": "8",
          "produto_id": "7",
          "client_id": "6",
          "id": "1"
      }
  ]
  ```

##CSV de Saída
O CSV de saída deve conter as seguintes colunas:
  - ID do Vendedor
  - Nome do Vendedor
  - Telefone do Vendedor
  - ID do Cliente
  - Nome do Cliente
  - Telefone do Cliente
  - Email do Cliente
  - ID do Produto
  - Nome do Produto
  - Preço do Produto
  - SKU do Produto


##Critérios de Avaliação
  - Organização do código
  - Boas práticas de programação
  - Escalabilidade
  - Facilidade de manutenção
  - Utilização de broker de mensageria
  - Documentação


##Entrega
  - O código deve ser entregue em um repositório público no Github.
  - Deve conter um README.md com instruções de como rodar a aplicação.
  - Deve conter os CSVs gerados no projeto para cada vendedor.
  - Deve conter a arquitetura da aplicação.
  - Enviar o link do repositório para o e-mail do recrutador.

# Aceleração Global Dev #5 Impulso
### Subject: Advanced integrations for Ruby On Rails, PostgreSQL and Sidekiq

# Descrição do Sistema
Este sistema é uma aplicação Rails que gerencia marcas de carros, carros, vendas, e avaliações. Ele foi projetado para fornecer uma interface robusta para manipulação de dados relacionados a marcas, carros e transações de vendas, além de fornecer suporte para buscas e relatórios de receitas.

## Funcionalidades Principais
### Gerenciamento de Marcas e Carros
- Marcas: Criação, leitura, atualização e exclusão de registros de marcas.
- Carros: Criação, leitura, atualização e exclusão de registros de carros, incluindo atributos como nome, marca associada, pontuação, número de série, e status ativo.
### Gerenciamento de Vendas
- Vendas: Criação e gerenciamento de registros de vendas, associando carros, compradores, vendedores e referências de valor de carros.
- Referências de Valor de Carros: Armazenamento de valores de carros em diferentes datas de competência.
### Avaliações
- Avaliações: Criação e gerenciamento de avaliações de diferentes entidades (e.g., carros, vendedores).
### Busca e Indexação
- Busca: Implementação de um campo de busca para blog posts utilizando tsvector e indexação GIN.
- Indexação: Utilização de diferentes tipos de índices (btree e hash) para otimização de buscas por números de série de carros.
### Relatórios e Vistas Materializadas
- Vistas Materializadas: Implementação de vistas materializadas para relatórios eficientes:
  - brand_with_cars: Exibe marcas com seus respectivos carros e valores mais recentes.
  - revenues: Relatório de receitas mensais baseado nas vendas de carros.
## Testes e Performance
- Testes de Performance: Utilização de RSpec para testar a performance de consultas, comparando iteração simples com operações em massa (insert_all e upsert_all).
- Teste de Duplicidade: Verificação do comportamento do sistema ao lidar com duplicatas ao usar upsert_all.
## Estrutura do Banco de Dados
- Tabelas:

  - brands: Armazena informações das marcas.
  - cars: Armazena informações dos carros.
  - sales: Armazena informações das vendas.
  - car_value_references: Armazena os valores dos carros em diferentes datas de competência.
  - reviews: Armazena avaliações.
  - buyers e sellers: Armazena informações dos compradores e vendedores.
  - blog_posts: Armazena posts de blog com suporte a buscas.
- Vistas Materializadas:

  - brand_with_cars: Contém marcas com seus carros e valores mais recentes.
  - revenues: Contém o relatório de receitas mensais.
## Migrations
- As definições do esquema do banco de dados são geradas automaticamente a partir do estado atual do banco de dados usando o recurso de migrações do Active Record.
## Requisitos de Sistema
- Rails 6 ou superior: O sistema utiliza funcionalidades como upsert_all e insert_all introduzidas no Rails 6.
- PostgreSQL: Utilizado como banco de dados principal, com extensões como plpgsql habilitadas.

Este sistema oferece uma solução completa para o gerenciamento de marcas e carros, transações de vendas, e avaliações, com suporte a buscas eficientes e relatórios detalhados. A estrutura robusta do banco de dados e os testes de performance garantem uma aplicação ágil e confiável.

## Hosts

- Lucas Santos - https://github.com/lsantosc - https://www.linkedin.com/in/lsantosc/
- Caio Nascimento - https://github.com/caio-nas - https://www.linkedin.com/in/caiomvnascimento/

## Table of contents

### insert_all/upsert_all
New Rails 6 methods for bulk operations

- spec/database/insert_all_spec.rb
- spec/database/upsert_all_spec.rb

## How to run profiler tests

```
RAILS_ENV=test bundle exec rspec -fd --profile

# Docker setup is available for your convenience <3
docker-compose run web RAILS_ENV=test bundle exec rspec -fd --profile
```

## References
- https://bigbinary.com/blog/bulk-insert-support-in-rails-6
- https://www.citusdata.com/blog/2017/10/17/tour-of-postgres-index-types/
- https://karolgalanciak.com/blog/2018/08/19/indexes-on-rails-how-to-make-the-most-of-your-postgres-database/
- https://medium.com/better-programming/how-to-use-sidekiq-in-rails-6-f3b76678362d
- https://bigbinary.com/blog/rails-5-adds-support-for-expression-indexes-for-postgresql
- https://medium.com/captain-contrat-engineering/how-to-execute-arel-queries-431639047e91

## Videos

[Guru-SP 39: Porque usar PostgreSQL por Nando Vieira](https://www.youtube.com/watch?v=VWtvJsjpOjY)
[Dicas e truques com PostgreSQL por Nando Vieira - DevInSantos 2015](https://www.youtube.com/watch?v=unFnLc9f3dg)
[Postgres The Bits You Haven’t Found, Heroku’s Peter van Hardenberg at Waza 2013](https://vimeo.com/61044807)

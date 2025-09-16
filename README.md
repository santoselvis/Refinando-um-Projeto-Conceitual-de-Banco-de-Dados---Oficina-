# Projeto Conceitual de Banco de Dados - Oficina
Este repositório contém a documentação e os refinamentos de um projeto conceitual de banco de dados voltado para um sistema de abertura de OS para oficina. O objetivo principal é transformar os requisitos de negócio em um modelo conceitual claro, estruturado e alinhado com as boas práticas de modelagem de dados.

##  Conecte-se comigo 
<i> 

[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/elvis-franklin)
[![GitHub](https://img.shields.io/badge/GitHub-0077B5?style=for-the-badge&logo=github&logoColor=white)](https://github.com/santoselvis)
[![Perfil DIO](https://img.shields.io/badge/-Meu%20Perfil%20na%20DIO-0077B5?style=for-the-badge&logo=gitbook&logoColor=white)](https://web.dio.me/users/efasantosaju?tab=skills&page=1)
[![E-mail](https://img.shields.io/badge/-Email-0077B5?style=for-the-badge&logo=microsoft-outlook&logoColor=white)](mailto:efasantosaju@gmail.com)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-0077B5?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/5579991342224) 
<br />
<br />
[![Status](https://img.shields.io/badge/status-%20concluido-blue)](#)

---
## Sumario
- 1.0 Levantamento de Requisitos
- 1.1 Requisitos Funcionais
- 1.2 Regras de Negócio
- 1.3 Modelo Conceitual Oficina
- 1.4 Entidades e Atributos
- 1.5 Relacionamentos
- 2.0 Refinando o Modelo Conceitual
- 2.1 Criação da Entidade Associativa "Item_Pedido"
- 2.2 Adição de Status do Pedido
- 2.3 Registro da Forma de Pagamento 
- 2.4 Registro da Entrega do Produto
- 2.5 Registro da Transportadora do Produto
- 3.0 Caso de Uso - Compra de Produtos
- 3.1 Loja Virtual de Eletrônicos

### 1.0 Levantamento de Requisitos
Todos os requisitos aqui destacados foram levantados com base no modulo Refinando um Projeto Conceitual de Banco de Dados - Oficina, parte do Bootcamp Randstad Analise de Dados da DIO. O objetivo é desenvolver um projeto conceitual de banco de dados para criação de um sistema de ordem de serviço para oficina que permita o gerenciamento eficiente de aberturas de ordens de serviço, clientes, veiculos, pagamentos e etc...
 
### 1.1 Requisitos Funcionais
Este repositório contém o projeto de banco de dados para um sistema de controle e gerenciamento da execução de ordens de serviço(OS) em uma oficina mecânica. O objetivo é modelar, refinar e estruturar o projeto conceitual que dará suporte ao sistema, com foco na organização de processos, registro de serviços e cálculo de valores.

1. Clientes levam seus veículos à oficina para conserto ou revisões periódicas.

2. Recepção do veículo e designação a uma equipe de mecânicos;

3. Identificação dos serviços necessários e geração da Ordem de Serviço (OS);

4. Consulta à tabela de mão-de-obra e valores de peças para calcular o custo total da OS;

5. O cliente autoriza a execução dos serviços;

6. A mesma equipe executa os serviços e atualiza o status da OS.

### 1.2 Regras de Negócio
O banco deve ser estruturado para refletir corretamente os relacionamentos entre as principais entidades envolvidas no processo de abertura de ordem de serviço, garantindo a integridade dos dados e o funcionamento adequado dos fluxos operacionais. Essa estrutura inicial esta sendo desenvolvida conforme as regras de negócio.

1. Relacionamento Cliente–Serviço
Cada cliente pode realizar múltiplos serviços ao longo do tempo, caracterizando uma relação do tipo um-para-muitos. Essa estrutura permite o rastreamento do histórico de compras de cada cliente, bem como a análise de comportamento de consumo.

2. Relacionamento Pedido–Produto
Um pedido pode conter múltiplos produtos, e cada produto pode estar presente em diversos pedidos distintos, estabelecendo uma relação muitos-para-muitos. Para representar essa relação, é necessária a utilização de uma entidade associativa, como Item_Pedido, que armazena informações adicionais como quantidade, preço no momento da compra e possíveis descontos aplicados.

3. Gestão de Estoque
O sistema deve implementar uma rotina automática de atualização de estoque. A quantidade disponível de cada produto deve ser decrementada com base na quantidade adquirida em pedidos concluídos. Isso evita inconsistências e possibilita o controle preciso da disponibilidade de produtos na plataforma.

4. Produtos Vendidos por Terceiros
Os produtos cadastrados na plataforma podem ser vendidos tanto pela empresa responsável pelo sistema quanto por vendedores terceiros. Cada produto deve manter um vínculo direto com o seu respectivo vendedor, permitindo o gerenciamento individualizado de estoque, preço e condições de venda.

5. Pagamentos
Cada pedido deve possuir um pagamento associado, contendo informações como data, forma de pagamento (ex: cartão, boleto, Pix), e status (pago, pendente, recusado). A associação entre pedido e pagamento é do tipo um-para-um e é essencial para o controle financeiro e liberação da entrega.

6. Gestão de Entregas
O sistema deve controlar a entrega de cada pedido, mantendo registros como:
- Status da entrega (ex: em separação, em transporte, entregue, devolvido)
- Código de rastreio, fornecido pela transportadora para que o cliente possa acompanhar o envio.
- A entidade Entrega deve estar diretamente associada a um pedido e atualizada conforme os eventos logísticos ocorram.

### 1.3 Modelo Conceitual – E-commerce
Abaixo está a representação do modelo conceitual, usando a notação Entidade-Relacionamento (ER) com base nos requisitos levantados.
<div align="center">
    <img src="Files/Diagrama - Projeto Conceitual de Banco de Dados - E-commerce.png" alt="Create a resource" width="600"/>
</div>

### 1.4 Entidades e Atributos
Abaixo iremos especificar as entidades, seus atributos, e respectivos relacionamentos com o intuito de identificar corretamente se é possível garantir a integridade dos dados, facilitar a manutenção do sistema e assegurar que os processos de negócio sejam devidamente representados. Além disso, uma modelagem conceitual bem definida permite a comunicação clara entre técnicos e não técnicos, reduzindo ambiguidades na fase de desenvolvimento.

***Cliente***
- id_cliente (PK)
- tipo_cliente
- endereco
- email

***Cliente_PF (Entidade Fraca)***
- Cliente_id_cliente (FK)
- nome
- cpf
- data_nascimento
- celular

***Cliente_PJ (Entidade Fraca)***
- Cliente_id_cliente (FK)
- razao_social
- cnpj
- inscricao_estadual
- telefone

***Fornecedor***
- id_fornecedor (PK)
- razao_social
- endereco
- cnpj

***Produto***
- id_produto (PK)
- descricao
- preco
- estoque

***Pedido***
- id_pedido (PK)
- Cliente_id_cliente (FK)
- Produto_id_produto (FK)
- Entrega_id_entrega (FK)
- data_pedido
- status_pedido
- valor_pedido

***Pagamento***
- id_pagamento (PK)
- Pedido_id_pedido (FK)
- forma_pagamento
- data_pagamento
- status_pagamento

***Item_Pedido (Entidade Associativa)***
- id_pedido (FK)
- id_produto (FK)
- quantidade
- preco_unitario

***Entrega***
- id_entrega (PK)
- status
- data_entrega
- previsao_entrega
- rastreio
- endereco_entrega

### 1.5 Relacionamentos
Os relacionamentos entre entidades são tão essenciais quanto a definição das próprias entidades. Eles representam as interações e dependências entre os elementos do sistema, sendo responsáveis por estruturar os fluxos de informação e garantir a integridade dos dados. Citando por exemplo a nossa modelagem de um e-commerce, a entidade Cliente pode realizar vários Pedidos, enquanto cada Pedido está associado a um ou mais Produtos. Essa relação muitos-para-muitos entre Pedido e Produto geralmente é intermediada por uma entidade associativa, como Item do Pedido, que também armazena informações contextuais, como quantidade e preço unitário. Da mesma forma, um Pedido pode estar vinculado a um Pagamento e a um Endereço de Entrega, estabelecendo relações um-para-um ou um-para-muitos, dependendo da lógica de negócio.

- **Cliente 1:N Pedido** – Um cliente pode fazer vários pedidos.
- **Fornecedor N:M Produto** - Representado pela entidade associativa "Fornecedor_Produto".
- **Pedido N:M Produto** – Representado pela entidade associativa "Item_Pedido".
- **Pedido 1:N Pagamento** – Cada pedido possui um ou varios pagamentos associados.
- **Produto N:M Estoque** - Representado pela entidade associativa "Produto_Estoque".
- **Pedido 1:N Entrega** - Cada pedido possui uma ou varias entregas.
- **Entrega 1:N Trasportadora** - Uma entrega possui uma ou varias transportadoras vinculadas.

### 2.0 Refinando o Modelo Conceitual
A partir deste momento, serão registrados os aprimoramentos e ajustes efetuados após a elaboração inicial do modelo conceitual, fundamentados nas diretrizes apresentadas ao longo do módulo. Outros refinamentos poderão ser realizados conforme novos requisitos forem identificados, ou correções sejam propostas no modulo.

### 2.1 Criação da Entidade Associativa "Item_Pedido"
Durante a modelagem do sistema de e-commerce, identificou-se a necessidade de representar de forma mais precisa a relação muitos-para-muitos entre as entidades Pedido e Produto. Essa relação, por sua natureza, envolve não apenas a associação entre os registros, mas também informações específicas de cada instância de produto dentro de um pedido.
- Motivação: A relação muitos-para-muitos entre Pedido e Produto precisava ser melhor representada.
- Solução: Criamos a entidade associativa "Item_Pedido", permitindo registrar quantidade e preço por item no pedido.

### 2.2 Adição de status ao Pedido
Durante a evolução do modelo de dados do sistema de e-commerce, identificou-se a necessidade de acompanhar o ciclo de vida de um pedido de forma mais estruturada, permitindo maior visibilidade do processo de compra, logística e atendimento ao cliente.
- Motivação: Era necessário acompanhar o ciclo de vida de um pedido.
- Solução: Adicionado o atributo `status_pedido` na entidade Pedido (em processamento, enviado, entregue, cancelado). Para complementar o refinamento tambem foi adicionado o atributo data_pedido para registrar as datas em que cada um dos pedidos foram abertos.

### 2.3 Registro da Forma de Pagamento
Durante a análise do processo de recebimento de valores, identificou-se a necessidade de distinguir as diferentes formas de pagamento utilizadas pelos clientes, como cartão de crédito, boleto bancário, pix, entre outros, numa relação com a entidade Pedido de 1:N. Essa diferenciação é essencial para fins de controle financeiro, conciliação bancária e geração de relatórios mais detalhados, além de permitir a implementação de regras de negócio específicas para cada tipo de pagamento.
- Motivação: Era importante diferenciar pagamentos (cartão, boleto, pix etc.).
- Solução: Adicionado o atributo `forma_pagamento` na entidade Pagamento.

### 2.4 Registro da Entrega do Produto
Foi identificada a necessidade de representar, de forma mais clara, as informações relacionadas ao processo de entrega dos pedidos, com o intuito facilitar a rastreabilidade, o controle logístico e a evolução do sistema com funcionalidades específicas, como o acompanhamento de status da entrega, previsão de chegada e informações do transportador. Era importante diferenciar pagamentos (cartão, boleto, pix etc.).
- Motivação: Necessidade de controlar e rastrear os pedidos enviados aos clientes.
- Solução: Foi criada a entidade Entrega, responsável por representar de forma independente os dados e eventos logísticos relacionados ao envio de um pedido. Essa nova entidade foi associada à entidade Pedido por meio de uma relação 1:N, permitindo que um pedido tenha uma ou mais entregas vinculadas a ele.

### 2.5 Registro da Transportadora do Produto
Identificamos a necessidade de representar, de forma estruturada, as informações referentes às empresas responsáveis pelo transporte dos pedidos. Até então, os dados de entrega estavam concentrados apenas na entidade Entrega, sem uma separação clara da transportadora utilizada, o que dificultava o controle logístico, a análise de desempenho e a manutenção de contratos e regras específicas por transportadora.
- Motivação: Necessidade de identificar e avaliar os transporte dos produtos estabelecendo um vínculo direto entre cada entrega realizada e a transportadora responsável.
- Solução: A introdução da entidade Transportadora abriu espaço para melhorias operacionais, análises logísticas e evoluções futuras no processo de entrega.

### 3.0 Caso de Uso - Compra de Produtos
O presente estudo de caso tem como objetivo demonstrar a aplicação de um modelo de dados para um sistema de gestão de vendas e logística em uma loja virtual de eletrônicos. O sistema foi desenvolvido para contemplar as principais entidades envolvidas no processo comercial, desde a realização do pedido pelo cliente até a entrega final do produto.
A proposta é apresentar, a partir de um exemplo prático fictício, como os relacionamentos entre as entidades (Cliente, Pedido, Produto, Fornecedor, Estoque, Pagamento, Entrega e Transportadora) são utilizados para dar suporte às operações do negócio.

### 3.1 Loja Virtual de Eletrônicos
Para ilustrar o funcionamento do modelo, foi criado um pedido fictício realizado pelo cliente João da Silva em 10/09/2025.
🧑 Cliente
Cliente: João da Silva
Email: joao.silva@email.com
Telefone: (11) 99999-8888

📦 Pedido
Pedido #1234
Data: 10/09/2025
Status: Pago Parcialmente

🛒 Produtos do Pedido (via Item_Pedido)
Notebook Dell XPS 13 – Qtd: 1 – Valor: R$ 7.500,00
Mouse Logitech MX Master 3S – Qtd: 2 – Valor: R$ 650,00 cada
Total do Pedido: R$ 8.800,00

🏭 Fornecedores (via Fornecedor_Produto)
Dell Brasil → Fornece o Notebook Dell XPS 13
Ingram Micro → Fornece tanto o Notebook Dell XPS 13 quanto o Mouse Logitech MX Master 3S
Logitech Brasil → Fornece o Mouse Logitech MX Master 3S

🏢 Estoques (via Produto_Estoque)
Estoque SP → Possui 10 notebooks Dell XPS 13
Estoque RJ → Possui 50 mouses Logitech MX Master 3S

💳 Pagamentos (via Pedido 1:N Pagamento)
Pagamento 1: R$ 4.400,00 – Cartão de Crédito (Visa) – 10/09/2025
Pagamento 2: R$ 4.400,00 – Boleto Bancário – 12/09/2025

🚚 Entregas (via Pedido 1:N Entrega)
Entrega 1 (SP → Cliente):
Produto: Notebook Dell XPS 13
Data: 12/09/2025
Transportadora: JadLog

Entrega 2 (RJ → Cliente):
Produtos: 2x Mouse Logitech MX Master 3S
Data: 13/09/2025
Transportadoras: DHL + Loggi

> Este é apenas um exemplo para ilustrar como o modelo pode ser utilizado em situações reais.

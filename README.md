# Projeto Conceitual de Banco de Dados - Oficina Mecanica
Este repositório contém a documentação e os refinamentos de um projeto conceitual de banco de dados para um sistema de gestão de ordens de serviço (OS) em uma oficina mecânica. O objetivo é criar um modelo conceitual claro e estruturado, transformando os requisitos de negócio em um banco de dados funcional, que possibilite o gerenciamento eficiente das OS, clientes, veículos, serviços e pagamento

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


## Sumario
- 1.0 Levantamento de Requisitos
- 1.1 Requisitos Funcionais
- 1.2 Regras de Negócio
- 1.3 Modelo Conceitual Oficina
- 1.4 Entidades e Atributos
- 1.5 Relacionamentos
- 2.0 Refinando o Modelo Conceitual
- 2.1 Criação da Entidade Associativa "Item_OS"
- 2.2 Adição de Status da OS
- 2.3 Registro da Forma de Pagamento 
- 2.4 Registro de Entrega do Veiculo
- 3.0 Caso de Uso - Sistema de Abertura de Ordem de Serviço
- 3.1 Processo de Reparação de Veiculo

### 1.0 Levantamento de Requisitos
Este projeto foi desenvolvido para criar um sistema de gerenciamento de Ordens de Serviço (OS) para uma oficina mecânica. O objetivo principal é modelar e refinar o banco de dados de forma a refletir os requisitos de negócio e otimizar os processos operacionais da oficina.
 

### 1.1 Requisitos Funcionais
Os requisitos funcionais do banco de dados são definidos com o intuito de suportar o processo de atendimento e manutenção dos veículos dos clientes. O sistema deve abranger os seguintes fluxos:
1. Cadastro de Clientes: A oficina deve registrar informações detalhadas sobre seus clientes, tanto pessoas físicas quanto jurídicas.
2. Cadastro de Veículos: Cada cliente pode ter um ou mais veículos registrados no sistema.
3. Abertura de Ordem de Serviço (OS): O cliente solicita a abertura de uma ordem de serviço para reparo ou revisão de seu veículo.
4. Atribuição de Serviços: A oficina define os serviços a serem executados, registrando os tipos de serviços e peças necessárias.
5. Cálculo de Custos: O sistema deve calcular o valor total da OS com base nos serviços e peças utilizadas.
6. Pagamento e Status da OS: O sistema deve registrar os pagamentos efetuados e permitir o acompanhamento do status da OS (ex: em andamento, concluída).
7. Entrega do Veículo: Após a conclusão dos serviços, o veículo é entregue ao cliente.

### 1.2 Regras de Negócio
Em uma oficina mecânica, as regras de negócio desempenham um papel fundamental para garantir que os processos operacionais sejam realizados de forma eficiente, precisa e sem erros. Elas ajudam a organizar informações de clientes, veículos, serviços prestados e estoque de peças, garantindo que o sistema funcione de acordo com as necessidades da oficina e do cliente. Estas regras de negócio têm como objetivo garantir a integridade dos processos operacionais da oficina, otimizando a gestão de ordens de serviço e permitindo o acompanhamento eficiente da execução dos serviços, custos e pagamentos, com transparência para os clientes e para a equipe da oficina.

- Cadastro de Clientes e Veículos:
Os clientes podem registrar um ou mais veículos na oficina mecânica. Cada veículo possui um identificador único e está associado a um cliente. Para cada veículo, são registrados dados como modelo, ano de fabricação e placa.

- Designação de Equipe de Mecânicos:
Ao receber um veículo para reparo ou revisão, a oficina designa uma equipe de mecânicos para avaliar e executar os serviços necessários. Cada equipe é composta por mecânicos especializados, e os serviços são atribuídos com base na especialidade de cada membro da equipe.

- Identificação de Serviços:
A equipe de mecânicos realiza uma avaliação inicial do veículo e identifica os serviços a serem executados. Com base nessa avaliação, é criada uma Ordem de Serviço (OS) que inclui a lista de serviços, peças necessárias, o valor estimado de mão de obra, a data de entrega e o status da OS.

- Geração da OS:
Cada Ordem de Serviço (OS) gerada para um veículo deve conter os seguintes dados obrigatórios:
Número da OS: Identificador único gerado automaticamente pelo sistema.
Data de Emissão: Data em que a OS foi gerada.
Valor de Mão de Obra: O valor para execução dos serviços, calculado com base na tabela de referência de mão-de-obra.
Valor das Peças: Valor das peças necessárias para a execução do serviço, conforme consulta à tabela de preços de peças.
Data de Conclusão Estimada: A data prevista para a entrega do veículo ao cliente.
Status da OS: Indicação do status atual da OS (ex: em análise, em andamento, concluída, aguardando peças).

- Autorização para Execução:
A execução dos serviços será iniciada somente após a autorização do cliente. O cliente pode autorizar a execução total ou parcial dos serviços descritos na OS. O sistema registra o momento da autorização e qualquer alteração posterior no escopo dos serviços.

- Execução dos Serviços:
A equipe de mecânicos é responsável por executar os serviços conforme a OS. Cada mecânico possui um código único, nome, endereço e especialidade, que devem ser registrados para controle e acompanhamento. Durante a execução, o status da OS é atualizado conforme o progresso dos serviços (ex: em andamento, aguardando peça, concluído).

- Avaliação de Serviços:
A equipe de mecânicos deve avaliar e registrar quaisquer alterações necessárias nos serviços durante a execução (por exemplo, se for identificado um serviço adicional ou alteração no valor das peças). A OS será atualizada conforme essas mudanças, e o cliente será notificado para autorizar os ajustes antes da execução.

- Cálculo e Controle do Custo de Mão de Obra:
O sistema deve calcular automaticamente o valor de cada serviço com base em uma tabela de referência de mão de obra, que define o custo de cada tipo de serviço realizado. O custo é calculado com base no tempo estimado para a execução do serviço e no valor da hora trabalhada, conforme a tabela de preços da oficina.

- Cálculo do Custo de Peças:
O custo de peças necessárias para o serviço será calculado com base no valor unitário de cada peça registrada no sistema. O valor total das peças será somado ao valor da mão de obra para compor o custo total da OS.

- Status e Conclusão da OS:
Cada OS deve ter um status que reflete seu estágio no processo de execução. Os principais status da OS são:
Em Análise: Quando a OS está sendo analisada pela equipe de mecânicos, mas ainda não foi autorizada pelo cliente.
Em Andamento: Quando o serviço está sendo executado.
Aguardando Peças: Quando a execução do serviço está aguardando a entrega de peças.
Concluída: Quando todos os serviços foram executados e o veículo está pronto para ser entregue ao cliente.
Cancelada: Caso o cliente ou a oficina cancele a OS antes da conclusão dos serviços.

- Data de Conclusão:
Cada OS deve ter uma data de conclusão estimada. Essa data pode ser alterada conforme o andamento dos serviços, com o cliente sendo informado sobre qualquer alteração no prazo.

- Entrega ao Cliente:
Após a conclusão dos serviços, a OS é finalizada, e o veículo é entregue ao cliente. O cliente pode ser notificado por e-mail ou SMS quando o veículo estiver pronto para ser retirado, e o status da OS é atualizado para Concluída.

- Registro dos Mecânicos:
Cada mecânico da oficina é cadastrado no sistema com as seguintes informações:
Código do Mecânico: Identificador único.
Nome: Nome completo do mecânico.
Endereço: Endereço de trabalho ou residência.
Especialidade: A especialidade do mecânico (ex: motor, suspensão, eletrônica, etc.).

- Atribuição de Mecânicos às OS:
Cada OS é atribuída a uma equipe de mecânicos, com base nas especialidades necessárias para a execução dos serviços identificados na avaliação inicial do veículo.

Controle de Pagamento:
Após a execução dos serviços e entrega do veículo, o cliente deve efetuar o pagamento do valor total da OS, que inclui o custo de mão de obra e peças. O sistema permite o registro de pagamentos parciais ou totais, com as formas de pagamento sendo registradas (ex: dinheiro, cartão de crédito, Pix).

### 1.3 Modelo Conceitual – Oficina Mecanica
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

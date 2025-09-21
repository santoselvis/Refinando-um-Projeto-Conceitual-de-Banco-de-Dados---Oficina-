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
- 2.1 Criação da Entidade Associativa "Servico_Executado"
- 2.2 Adição de Status da OS
- 2.3 Registro da Forma de Pagamento 
- 2.4 Registro de Entrega do Veiculo
- 2.5 Registro de Alterações na OS
- 3.0 Caso de Uso - Abertura de Ordem de Serviço
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

- Controle de Pagamento:
Após a execução dos serviços e entrega do veículo, o cliente deve efetuar o pagamento do valor total da OS, que inclui o custo de mão de obra e peças. O sistema permite o registro de pagamentos parciais ou totais, com as formas de pagamento sendo registradas (ex: dinheiro, cartão de crédito, Pix).

### 1.3 Modelo Conceitual – Oficina Mecanica
Abaixo está a representação visual do modelo conceitual, usando a notação Entidade-Relacionamento (ER) com base nos requisitos levantados.
<div align="center">
    <img src="Files/Diagrama - Projeto Conceitual de Banco de Dados - E-commerce.png" alt="Create a resource" width="600"/>
</div>

### 1.4 Entidades e Atributos
Abaixo iremos especificar as entidades, seus atributos, e respectivos relacionamentos com o intuito de identificar corretamente se é possível garantir a integridade dos dados, facilitar a manutenção do sistema e assegurar que os processos de negócio sejam devidamente representados. Além disso, uma modelagem conceitual bem definida permite a comunicação clara entre técnicos e não técnicos, reduzindo ambiguidades na fase de desenvolvimento.

***Cliente***
- id_cliente (PK)
- nome
- tipo_cliente (PF ou PJ)
- contato
- endereco
- email

***Veiculo***
- id_veiculo (PK)
- Cliente_id_cliente (FK)
- marca
- modelo
- ano
- chassi
- placa

***OS***
- id_ordemservico (PK)
- Veiculo_id_veiculo (FK)
- Status_OS_idStatus_OS (FK)
- valor_orcado
- valor_final
- data_abertura
- data_previsao
- data_fechamento
- notifica_cliente (boolean)

***Status_OS***
- idstatus_os (PK)
- descricao

***Servico***
- id_servico (PK)
- Tabela_Preco_id_tabela (FK)
- descricao
- valor_servico
- tempo_servico

***Tabela_Preco***
- id_tabela (PK)
- valor_hora
- vigencia_inicio
- vigencia_fim

***Servico_Executado (Relacionamento - OS + Servico)***
- OS_id_ordemservico (FK)
- Servico_id_servico (FK)
- quantidade
- valor_total
- autorizacao_cliente (boolean)
- data_autorizacao

***Pecas***
- id_pecas (PK)
- descricao
- preco_unitario
- codigo_fabricante

***Estoque***
- id_estoque (PK)
- Pecas_id_pecas (FK)
- quantidade_atual 

***Itens_Pecas (Relacionamento - Pecas + OS)***
- OS_id_ordemservico (FK)
- Pecas_id_pecas (FK)
- quantidade
- valor_total
- autorizacao_cliente (boolean)
- data_autorizacao

***Mecanico***
- id_mecanico (PK)
- nome
- especialidade
- endereco

***Equipe_OS (Relacionamento - Mecanico + OS)***
- id_equipe (PK)
- OS_id_ordemservico (FK)
- Mecanico_id_mecanico (FK)
- funcao

***Pagamento***
- id_pagamento (PK)
- OS_id_ordemservico (FK)
- Forma_Pagamento_idforma_pagamento (FK)
- valor_pago
- data_pagamento

***Forma_Pagamento***
- idforma_pagamento (PK)
- descricao

***Alteracao***
- id_alteracao
- OS_id_ordemservico (FK)
- tipo_alteracao
- descricao_alteracao
- valor_alteracao
- data_alteracao
- status_alteracao

### 1.5 Relacionamentos
Os relacionamentos entre entidades são tão essenciais quanto a definição das próprias entidades. Eles representam as interações e dependências entre os elementos do sistema, estruturando os fluxos de informação e garantindo a integridade dos dados.

No caso da oficina mecânica, a entidade Cliente pode possuir vários veículos cadastrados, e cada Veículo pode gerar múltiplas Ordens de Serviço (OS). Cada OS pode envolver diferentes serviços, peças, pagamentos e mecânicos responsáveis. Para tratar essas relações muitos-para-muitos, utilizamos entidades associativas como OrdemServico_Servico, OrdemServico_Peca e Equipe_OS, que registram informações adicionais como quantidade, autorização do cliente e função do mecânico. Abaixo os relacionamentos do modelo:

- Cliente 1:N Veículo – Um cliente pode cadastrar vários veículos.

- Veículo 1:N Ordem_Servico – Um veículo pode gerar diversas ordens de serviço.

- Ordem_Servico N:M Serviço – Representado pela entidade associativa Servico_Executado, que armazena quantidade, valor total e autorização do cliente.

- Ordem_Servico N:M Peça – Representado pela entidade associativa Itens_Pecas, que registra peças utilizadas, quantidades e valores.

- Ordem_Servico N:M Mecânico – Representado pela entidade associativa Equipe_OS, que define os mecânicos responsáveis e suas funções.

- Ordem_Servico 1:N Pagamento – Cada ordem pode ser liquidada com um ou mais pagamentos.

- Pagamento N:1 Forma_Pagamento – Cada pagamento está vinculado a uma forma específica (dinheiro, cartão, Pix etc.).

- Pecas 1:N Estoque – Cada peça cadastrada está associada ao controle de estoque.

- Ordem_Servico 1:N Alteracao – Uma OS pode sofrer diversas alterações, registrando histórico e valores adicionais.

- Ordem_Servico N:1 Status_OS – Cada OS possui um status definido em tabela de domínio (Ex: Em Análise, Em Andamento, Concluída, Cancelada).

### 2.0 Refinando o Modelo Conceitual
A partir deste momento, registramos os aprimoramentos e ajustes efetuados no modelo conceitual da oficina mecânica, com base nos requisitos de negócio. Outros refinamentos poderão ser incorporados conforme novos requisitos forem identificados.

### 2.1 Criação da Entidade Associativa "Servico_Executado"
Identificamos a necessidade de representar de forma precisa a relação muitos-para-muitos entre Ordem_Servico e Servico. Essa entidade associativa permite armazenar não apenas o vínculo, mas também informações específicas.
- Motivação: Uma OS pode incluir vários serviços, e um mesmo serviço pode estar em várias OS.
- Solução: Criada a entidade Servico_Executado, registrando quantidade, valor total, autorização do cliente e data da autorização.

### 2.2 Adição de Status da OS
Durante a evolução do modelo, percebemos a importância de acompanhar o ciclo de vida da OS de forma estruturada.
- Motivação: Necessidade de registrar o andamento da ordem (em análise, em execução, aguardando peças, concluída, cancelada).
- Solução: Criada a entidade Status_OS como tabela de domínio, vinculada à OrdemServico.

### 2.3 Registro da Forma de Pagamento
O controle financeiro da oficina exige o registro detalhado das formas de pagamento utilizadas pelos clientes.
- Motivação: Diferenciar meios de pagamento e permitir pagamentos parciais.
- Solução: Criada a entidade Forma_Pagamento, vinculada à entidade Pagamento.

### 2.4 Registro da Entrega do Veículo
Era necessário representar, de forma mais clara, o momento da entrega do veículo ao cliente após a conclusão da OS.
- Motivação: Melhorar rastreabilidade do processo e comunicação com o cliente.
- Solução: Adicionados os atributos data_entrega e notifica_cliente à entidade Ordem_Servico, possibilitando registrar a entrega e notificar o cliente.

### 2.5 Registro de Alterações na OS
Durante a execução, pode haver mudanças nos serviços ou peças previstas inicialmente.
- Motivação: Garantir histórico e rastreabilidade das alterações autorizadas pelo cliente.
- Solução: Criada a entidade Alteracao, vinculada a entidade Ordem_Servico, para armazenar tipo de alteração, descrição, valor, data e status da alteração.

### 3.0 Caso de Uso – Abertura de Ordem de Serviço
O caso de uso demonstra como o modelo de dados é aplicado para o processo de abertura, execução e conclusão de uma OS em uma oficina mecânica. O cliente leva o veículo para manutenção, autoriza os serviços e peças necessários, e realiza o pagamento após a conclusão.

### 3.1 Processo de Reparação de Veículo
> Este é apenas um exemplo para ilustrar como o modelo pode ser utilizado em situações reais.
- Vamos ao exemplo prático fictício:
🧑 Cliente
Cliente: João da Silva
Email: joao.silva@email.com
Telefone: (11) 99999-8888

🚗 Veículo
Marca: Toyota
Modelo: Corolla XEi
Ano: 2020
Placa: ABC-1234

📄 Ordem de Serviço (OS)
OS #2025
Data de Abertura: 10/09/2025
Status: Em andamento

🔧 Serviços (via OrdemServico_Servico)
Troca de óleo – R$ 150,00 – Autorizado em 10/09/2025
Alinhamento e Balanceamento – R$ 200,00 – Autorizado em 10/09/2025

🔩 Peças (via OrdemServico_Peca)
Filtro de óleo – Qtd: 1 – Valor: R$ 50,00 – Autorizado em 10/09/2025

👨‍🔧 Mecânicos (via Equipe_OS)
Carlos Andrade – Especialidade: Motor – Função: Execução da troca de óleo
Marcos Lima – Especialidade: Suspensão – Função: Execução de alinhamento/balanceamento

💳 Pagamentos (via Pagamento)
Pagamento 1: R$ 200,00 – Cartão de Crédito – 10/09/2025
Pagamento 2: R$ 200,00 – Pix – 11/09/2025

📦 Alterações (via Alteracao)
Nenhuma alteração registrada até o momento.

🚘 Entrega do Veículo
Previsão: 12/09/2025
Cliente será notificado por WhatsApp quando a OS for concluída.

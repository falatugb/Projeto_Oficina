<h1> Introdução </h1>

<p>
Esse projeto tem como objetivo demonstrar todo o processo de criação de um banco de dados de uma oficina de pequeno porte. Os processos documentados serão: 

  <strong>Análise de Requisitos</strong> – A primeira etapa e mais importante para a criação de um banco de dados. Consiste no conhecimento sobre a empresa e suas regras de negócio, nesta etapa são realizadas reuniões com o intuito de compreender o que faz a empresa , quais tipos de cliente a empresa possui, seu ramo de atuação e demais características que possam ser fundamentais para a criação de um banco de dados.

  <strong>Criação do Modelo Conceitual</strong> – Etapa onde serão definidas as entidades, atributos das entidades e como serão os relacionamentos com base no Modelo Entidade Relacionamento. A criação desse modelo tem como função captar os requisitos de informação e regras de negócio sob o ponto de vista da empresa, visando o entendimento da regra de negócio da empresa e utilizar como base para a criação do banco de dados.  

  <strong>Criação do Modelo Lógico</strong> – Etapa onde serão definidas as estruturas de armazenamento dos dados no banco e também seus relacionamentos. Serão definidos os registros, tipos de dados dos campos, tamanhos, chaves primárias e estrangeiras etc.

  <strong>Criação do Modelo Físico</strong> – Etapa onde será realizado o design do banco de dados de acordo com o modelo lógico definido. Nesta etapa também definimos o SGBD que será utilizado, nesse projeto utilizaremos o SGBD Microsoft SQL Server 2019.

Neste projeto será criado o modelo de banco de dados de uma Oficina Auto elétrica de pequeno porte, cenário o qual já tive experiência profissional durante dois anos antes de iniciar os estudos na área de tecnologia. Algumas informações serão simuladas afim de garantir um melhor desempenho nos processos criados para a conclusão do projeto.

</p>

<h1>
Análise de Requisitos
</h1>

<p>
O primeiro e mais importante processo a ser realizado durante a criação de um banco de dados, é a análise de requisitos. Etapa onde analisamos e conhecemos as regras de negócio da empresa, tendo como foco reuniões para conhecer melhor o mercado e público alvo da empresa, o tipo de serviço oferecido, tipos de cliente, seu ramo de atuação, suas características e demais informações que possam ser importantes para a criação do banco de dados.
Essa oficina será simulada como uma empresa de pequeno porte, a qual terá os seguintes setores:
  
•	<strong>Financeiro</strong> – Responsável pelo gerenciamento das contas gerais da empresa, pagamentos de funcionários e notas fiscais da empresa.

•	<strong>Produção</strong> – Responsável pela mão de obra principal da empresa, reparo de veículos e negociação direta com clientes. 
  
Para esses setores, serão listados os seguintes profissionais.
  
  •	<strong>Um assistente financeiro</strong>
  
  •	<strong>Três mecânicos eletricistas</strong>

  A partir das regras de negócio e entendendo a necessidade do cliente, a documentação das informações necessárias foram detalhadas abaixo.

  • <strong>Veículos</strong> – Identificação do veículo, Nome, Cor, Placa, Identificação do cliente (dono do veículo), Observações.

  •	<strong>Serviço Prestado</strong> – Identificação do serviço presto, Tipo de serviço, Data do serviço, Valor de peças, Valor de mão de obra, Descontos, Forma de Pagamento, Valor Total, Descrição do Serviço, Identificação do funcionário que realizou o serviço, identificação do veículo.

  •	<strong>Tipo de serviço</strong> – Identificação do tipo de serviço prestado, Tipo de serviço prestado, Descrição do tipo de serviço

  •	<strong>Funcionários</strong> – Identificação do funcionário, Identificação do setor de trabalho, Nome, Cargo, Sexo, Telefone, Endereço, Bairro, Data de Nascimento, Data de Admissão, Salário, Observações.

  •	<strong>Clientes</strong> – Identificação do cliente, Nome, Sexo, Endereço, Bairro, Data de Nascimento, CPF, Telefone

  •	<strong>Setores</strong> – Identificação do Setor, Nome do Setor, Quantidade de funcionários, identificação dos funcionários.

Tendo essas informações definidas, a próxima etapa será a criação do modelo conceitual.

</p>

<h1>
Modelo Conceitual
</h1>

<p>
A criação do modelo conceitual é o segundo processo para a criação do banco de dados, utilizaremos como base o Modelo Entidade-Relacionamento. Nessa etapa, será definida a estrutura do banco de dados de forma independente do SGBD utilizado. Definiremos os atributos das entidades e seus relacionamentos e modelo de cardinalidade entre as tabelas, tendo como objetivo visualizar, definir e gerar o entendimento da regra de negócio aplicada a criação do banco de dados. Segue abaixo exemplo do modelo conceitual desenvolvido para esse projeto.
</p>

![Modelo_Conceitual_Oficina](https://github.com/falatugb/Projeto_Oficina/blob/main/Modelo_Oficina_Conceitual1.jpg)


<h1>
Cardinalidade e Relacionamento
</h1>

<p>
A cardinalidade é caracterizada pelo número máximo e mínimo de ocorrências de uma entidade associada a ocorrências de outra entidade. Seguindo o modelo conceitual desenvolvido e regra de negócio apresentada na análise de requisitos, segue abaixo o modelo de cardinalidade desenvolvido para esse projeto.
<strong>
  
•	Veículos (1,N) <--> (1,1) Clientes <br>
Um veículo pertence a apenas um cliente, enquanto um cliente pode ter diversos veículos.

•	Veículos (1,N) <---> (1,1) Serviço Prestado <br>
Um veículo gera apenas um serviço, enquanto os serviços são gerados por diversos veículos.

•	Funcionários (1,1) <--> (1,N) Serviço Prestado <br>
Um funcionário pode fazer diversos serviços, porém cada serviço é vinculado a apenas um funcionário. 

•	Serviços Prestado (1,N) <--> (1,1) Tipo de pagamento <br>
Um serviço pode ter apenas um tipo de pagamento, enquanto os tipos de pagamento podem ser vinculados a diversos serviços.

•	Serviços Prestados (1,N) <--> (1,1) Tipos de serviço <br>
Um serviço pode ter apenas um tipo registrado, enquanto os tipos de serviços podem ser registrados em diversos serviços diferentes.

•	Funcionários (1,N) <--> (1,1) Setores <br>
Um funcionário pode ser vinculado à apenas um setor, enquanto cada setor pode ter diversos funcionários.
  </strong>
  </p>

<h1>
Modelo Lógico
</h1>

<p>
Etapa onde será definida as estruturas de armazenamento dos dados e seus relacionamentos. Serão definidos os principais componentes como Entidades, Atributos, Relacionamentos, Chaves primárias e estrangeiras e afins. Neste projeto iremos adotar o SGBD Microsoft SQL Server 2016, o qual utiliza o modelo relacional.
Segue abaixo exemplo do modelo lógico definido para esse projeto.
</p>


![Modelo_Lógico_Oficina](https://github.com/falatugb/Projeto_Oficina/blob/main/Modelo_Oficina_Lógico1.png)
  
<h1>
    Modelo Físico
</h1>
  
  <p>
 A fase final do processo envolve o desenvolvimento e a execução dos scripts para a implementação física do banco de dados, incorporando os requisitos coletados durante as fases de modelagem lógica e conceitual. Nessa etapa, serão desenvolvidas as tabelas, colunas, índices, restrições e outros elementos estruturais do banco de dados. 
Para este projeto, faremos uso do sistema de gerenciamento de banco de dados (SGBD) Microsoft SQL Server 2019.
Os SGBDs são softwares responsáveis pelo gerenciamento eficiente de bases de dados, desempenhando um papel fundamental na organização, armazenamento e manipulação dos dados. 

  <h2>•	Criação do banco de dados </h2>
Para darmos início ao nosso projeto, o primeiro passo para a modelagem física é a criação do nosso banco de dados. 

Utilizaremos as configurações padrão do SQL Server 2019 para propriedades do banco de dados como Autogrowth, Recovery Model, Endpoints e quantidade de arquivos de log e dados de linhas também serão padrão. O comando utilizado para a criação do banco de dados é o seguinte:
 
```SQL  
CREATE DATABASE PROJETO_OFICINA
ON PRIMARY
(
	NAME = PROJETO_OFICINA_DATA,
	FILENAME = 'C:\DATAFILES\PROJETO_OFICINA.MDF'
)

LOG ON 
(
	NAME = PROJETO_OFICINA_LOG,
	FILENAME = 'C:\DATAFILES\PROJETO_OFICINA.LDF'
)
```
  </p>
 <p>
  <h2>• Criação das tabelas </h2>
Após a criação do banco de dados, a próxima etapa será a criação das tabelas. Serão definidos os campos, tamanhos, tipos e restrições, incluindo também a chave primária de cada tabela. Abaixo estão os comandos utilizados para criar as tabelas.
  </p>
  
 
 ```SQL
CREATE TABLE SETORES
(
    ID_SETOR         INT IDENTITY (100,1) PRIMARY KEY,
    NOME_SETOR       VARCHAR (30) NOT NULL,
    QNT_FUNC         INT
)


CREATE TABLE FUNCIONARIOS
(
    ID_FUNC          INT IDENTITY (1,1) PRIMARY KEY,
    FK_ID_SETOR      INT,
    NOME             VARCHAR (50) NOT NULL, 
    CARGO            VARCHAR (30) NOT NULL,
    SEXO             VARCHAR (20) NOT NULL,
    TELEFONE         VARCHAR (11) NOT NULL,
    ENDERECO         VARCHAR (40) NOT NULL,
    BAIRRO           VARCHAR (30) NOT NULL,
    DATA_NASC        DATE NOT NULL,
    DATA_ADMISSAO    DATE NOT NULL,
    SALARIO          FLOAT NOT NULL,
    OBSERVACAO       VARCHAR (100)
)

CREATE TABLE TIPO_PAGAMENTO
(
    ID_TIPOPG        INT IDENTITY(1,1) PRIMARY KEY,
    TIPO_PAGAMENTO   VARCHAR(50),
    DESC_SERVICO     VARCHAR(300)
)

CREATE TABLE SERVICO_PRESTADO
(
    ID_SERVICO       INT IDENTITY (1,1) PRIMARY KEY,
    TIPO_SERVICO     INT,
    HORA_INICIO      DATETIME,
    HORA_TERMINO     DATETIME,
    VALOR_PECA       FLOAT,
    VALOR_MO         FLOAT,
    DESCONTOS        FLOAT,
    FK_FORMA_PG      INT,
    VALOR_TOTAL      FLOAT,
    DESC_SERVICO     VARCHAR (100),
    FK_ID_FUNC       INT,
    FK_ID_VEICULO    INT
)

CREATE TABLE CLIENTES
(
    ID_CLIENTE       INT IDENTITY (1,1) PRIMARY KEY,
    NOME_CLIENTE     VARCHAR (50) NOT NULL,
    ENDERECO         VARCHAR (40),
    BAIRRO           VARCHAR (30),
    DATA_NASC        DATE,
    CPF              CHAR (14),
    TELEFONE         VARCHAR (11) NOT NULL
)

CREATE TABLE VEICULOS 
(
    ID_VEICULO       INT IDENTITY (100,1) PRIMARY KEY,
    NOME_VEICULO     VARCHAR (50) NOT NULL,
    COR_VEICULO      VARCHAR (10) NOT NULL,
    DATA_ENTRADA     DATE NOT NULL,
    DATA_SAIDA       DATE NOT NULL,
    PLACA            VARCHAR (10) NOT NULL,
    OBSERVACAO       VARCHAR (100),
    FK_ID_CLIENTE    INT
)

CREATE TABLE TIPO_SERVICO
(
    ID_TIPOSERVICO 	INT PRIMARY KEY,
    TIPO_SERVICO 	VARCHAR(50),
    DESC_SERVICO 	VARCHAR(300)
)

 
 ```
   <p>
  <h2>• Criação dos relacionamentos entre as tabelas </h2>
Após a criação das tabelas, precisamos criar os relacionamentos entre elas, para isso serão criadas as restrições de integridade (CONSTRAINTS) relacionando o campo de uma tabela com outro campo de outra tabela, criando o relacionamento entre duas tabelas distintas, nomeados como Foreign Key.
  </p>
  
 ```SQL
ALTER TABLE VEICULOS
ADD CONSTRAINT FK_ID_CLIENTE 
FOREIGN KEY (FK_ID_CLIENTE)
REFERENCES CLIENTES (ID_CLIENTE) 

ALTER TABLE FUNCIONARIOS
ADD CONSTRAINT FK_ID_SETOR
FOREIGN KEY (FK_ID_SETOR)
REFERENCES SETORES (ID_SETOR)

ALTER TABLE SERVICO_PRESTADO
ADD CONSTRAINT FK2_ID_FUNC
FOREIGN KEY (FK_ID_FUNC)
REFERENCES FUNCIONARIOS (ID_FUNC)

ALTER TABLE SERVICO_PRESTADO
ADD CONSTRAINT FK_ID_VEICULO
FOREIGN KEY (FK_ID_VEICULO)
REFERENCES VEICULOS (ID_VEICULO)

ALTER TABLE SERVICO_PRESTADO
ADD CONSTRAINT FK_TIPO_PAGAMENTO
FOREIGN KEY (FK_FORMA_PG)
REFERENCES TIPO_PAGAMENTO (ID_TIPOPG)

ALTER TABLE SERVICO_PRESTADO
ADD CONSTRAINT FK_TIPO_SERVICO
FOREIGN KEY (TIPO_SERVICO)
REFERENCES TIPO_SERVICO (ID_TIPOSERVICO)
 ```
  <p>
	  <h2>• Criação de usuários e definição de permissões </h2>
	  
Para este projeto, serão criados dois usuários com diferentes níveis de permissão para acessar o banco de dados, com o objetivo de restringir o acesso aos dados conforme necessário.

• Gerente – Para este projeto, será criado um usuário com o papel de “Gerente”. Esse usuário terá permissões para executar operações de alteração, inserção, atualização e exclusão de dados no banco de dados. Além disso, o usuário terá permissão para criar views que serão utilizadas para a geração de relatórios personalizados que se encaixem nas necessidades da empresa.

Para criarmos o usuário GERENTE utilizaremos o seguinte script.
```SQL
-- Criando LOGIN e USUÁRIO no banco de dados
CREATE LOGIN GERENCIA WITH PASSWORD = 'GERENCIA_OFICINA';
CREATE USER GERENCIA FOR LOGIN GERENCIA;
```

No SQL Server, há uma restrição que impede a criação de vários usuários a um único login em um banco de dados. Portanto, será necessário criar logins e usuários separados para cada caso.

• Funcionários – Esse usuário terá permissões para executar apenas operações de consultas no banco de dados, sendo o nível mais básico de acesso à base de dados
```SQL
CREATE LOGIN FUNCIONARIOS WITH PASSWORD = 'FUNCIONARIOS_OFICINA'
CREATE USER FUNCIONARIOS FOR LOGIN FUNCIONARIOS;
```

<h2>• Permissões </h2>

Para conceder permissões aos usuários, devemos informar quais tabelas o usuário poderá acessar. Por tratar-se de um projeto com poucas tabelas, o script de permissões pode ser visualizado abaixo.

- GERENCIA
```SQL
-- PERMISSÕES: GERENCIA
GRANT SELECT, UPDATE, DELETE, INSERT ON CLIENTES          TO GERENCIA
GRANT SELECT, UPDATE, DELETE, INSERT ON FUNCIONARIOS      TO GERENCIA
GRANT SELECT, UPDATE, DELETE, INSERT ON SERVICO_PRESTADO  TO GERENCIA
GRANT SELECT, UPDATE, DELETE, INSERT ON SETORES           TO GERENCIA
GRANT SELECT, UPDATE, DELETE, INSERT ON TIPO_PG           TO GERENCIA
GRANT SELECT, UPDATE, DELETE, INSERT ON TIPO_SERVICO      TO GERENCIA
GRANT SELECT, UPDATE, DELETE, INSERT ON VEICULOS          TO GERENCIA
GRANT CREATE VIEW TO GERENCIA

```

- FUNCIONARIOS
```SQL
-- PERMISSÕES: FUNCIONARIOS
GRANT SELECT ON CLIENTES          TO FUNCIONARIOS
GRANT SELECT ON FUNCIONARIOS      TO FUNCIONARIOS
GRANT SELECT ON SERVICO_PRESTADO  TO FUNCIONARIOS
GRANT SELECT ON SETORES           TO FUNCIONARIOS
GRANT SELECT ON TIPO_PG           TO FUNCIONARIOS
GRANT SELECT ON TIPO_SERVICO      TO FUNCIONARIOS
GRANT SELECT ON VEICULOS          TO FUNCIONARIOS

```
  </p>
  
  <small><i>-- Atualizado em 14/06/2023</i></small>

<h1> Introdução </h1>

<p>
Esse projeto tem como objetivo demonstrar todo o processo de criação de um banco de dados de uma oficina de pequeno porte. Os processos documentados serão: 

  <strong>Análise de Requisitos</strong> – A primeira etapa e mais importante para a criação de um banco de dados. Consiste no conhecimento sobre a empresa e suas regras de negócio, nesta etapa são realizadas reuniões com o intuito de compreender o que faz a empresa , quais tipos de cliente a empresa possui, seu ramo de atuação e demais características que possam ser fundamentais para a criação de um banco de dados.

  <strong>Criação do Modelo Conceitual</strong> – Etapa onde serão definidas as entidades, atributos das entidades e como serão os relacionamentos com base no Modelo Entidade Relacionamento. A criação desse modelo tem como função captar os requisitos de informação e regras de negócio sob o ponto de vista da empresa, visando o entendimento da regra de negócio da empresa e utilizar como base para a criação do banco de dados.  

  <strong>Criação do Modelo Lógico</strong> – Etapa onde serão definidas as estruturas de armazenamento dos dados no banco e também seus relacionamentos. Serão definidos os registros, tipos de dados dos campos, tamanhos, chaves primárias e estrangeiras etc.

  <strong>Criação do Modelo Físico</strong> – Etapa onde será realizado o design do banco de dados de acordo com o modelo lógico definido. Nesta etapa também definimos o SGBD que será utilizado, nesse projeto utilizaremos o SGBD Microsoft SQL Server 2016.

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

![Modelo_Conceitual_Oficina](https://github.com/falatugb/Projeto_Oficina/blob/main/Modelo_Oficina_Conceitual.png)


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


![Modelo_Lógico_Oficina](https://github.com/falatugb/Projeto_Oficina/blob/main/Modelo_Oficina_Lógico.png)
  
  
  


  
  <small><i>-- Atualizado em 31/05/2023</i></small>

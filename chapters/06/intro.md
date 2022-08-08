# Capítulo 6 - Data Warehouses

Data Warehouses são bancos de dados otimizados para consulta de grandes volumes de dados. Ele faz parte das aplicações chamadas OLAP (‘On-line Analytical Processing’) em contraponto aos bancos de dados transacionais OLTP ('Online Transaction Processing’). Embora em muitos casos sejam apresentados como tecnologias distintas, não é incomum que tanto bancos transacionais como DW utilizem o mesmo banco de dados relacional ou alguma variação dele (ex. Amazon Redshift é baseado em PostgreSQL).

Na prática, as principais diferenças entre um DW e um banco transacional dizem respeito à arquitetura dos modelos de dados, isto é, a forma como tabelas, entidades e relações estão dispostas dentro do banco de dados. Um banco transacional com alto grau de normalização permite realizar operações de leitura e escrita de pequenas transações de uma forma muito eficiente e consistente, de modo que se realizamos uma consulta do saldo de um usuário na sua conta corrente temos uma garantia que entre o momento que iniciamos nossa consulta e a resposta do banco de dados esse mesmo usuário não fez um saque desses recursos e portanto tornaria esse saldo incorreto.   

Por outro lado, se ao invés de consultar os dados de um usuário específico quiséssemos fazer a contagem de todos os correntistas de um banco que possuem pelo menos R$500,00 na conta corrente teríamos provavelmente que conhecer o modelo de dados do sistema do Banco, realizar uma consulta com algumas dezenas de JOINs e não raramente ter que esperar alguns dias até um Analista de TI nos trazer essa informação. 

Ao longo dos anos, diferentes metodologias foram desenvolvidas para facilitar o acesso e processamento de consultas analíticas e o desenvolvimento dos data warehouses. Grande parte do sucesso de algumas dessas metodologias se deu em razão de dois prolíficos autores no campo de analytics, Ralph Kimball e William Inmon. Muito do que foi desenvolvido originalmente tinha como objetivo contornar limitações técnicas dos bancos de dados e tecnologias disponíveis à época e de certa forma se tornaram obsoletos no mundo da computação em nuvem e armazenamento barato. No entanto, a forma com que esses autores abordaram os principais problemas de analytics e muitas de suas soluções são de certa forma independentes da tecnologia disponível e permanecem cruciais para o desenvolvimento de processo de analytics até os dias de hoje. Em especial, a ênfase dada por esses autores em criar modelos de dados que facilitem o entendimento do usuário de negócios não técnicos continua mais atual do que nunca. Processo de analytics são processo de negócio, não de TI.


|                  | **Banco de Dados Transacional**                                                  | **Data Warehouse**                                                                       |
|------------------|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Características  | "Alto volume de Transações, Pequenas Transações, Normalizado, Consultas Rápidas" | "Alto volume de Dados,  Transações Grandes, Denormalizado, Consultas Agregadas, Colunar" |
| Tipo de pergunta | Qual o saldo do usuário com CPF xyz?                                             | Quantos usuários possuem saldo maior que R$500,00?                                       |
| Aplicações       | SQL Server, MySQL, Oracle SQL, PostgreSQL                                        | Amazon Redshift, Google Big Query, Snowflake

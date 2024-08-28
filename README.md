# RecuperacaobancoDeDados

Descrição do dataset escolhido:
O F1 GrandPrix Dataset é uma coleção meticulosamente selecionada de dados que fornece uma visão aprofundada do mundo das corridas de Fórmula 1. 
Este conjunto de dados abrange uma ampla gama de informações, 
incluindo circuitos, construtores, pilotos, resultados de corrida, tempos de volta, pit stops e muito mais.

-----------------------------------------------------------------------------------
Estrutura do Banco de Dados:
Tabela circuits:

circuit_id: INT, Chave Primária
circuitRef: VARCHAR(50)
nome: VARCHAR(20)
location: VARCHAR(45)
country: VARCHAR(45)
lat: DECIMAL(3) (Correção sugerida: DECIMAL(9,6) ou FLOAT)
ing: DECIMAL(3) (Correção sugerida: DECIMAL(9,6) ou FLOAT)
alt: INT
Tabela drivers:

driver_id: INT, Chave Primária
driverRef: VARCHAR(50)
numero: INT
codigo: VARCHAR(45)
forename: VARCHAR(45)
surname: VARCHAR(45)
dob: DATE
nationality: VARCHAR(45)
Tabela results:

result_id: INT, Chave Primária
driver_id: INT (Provavelmente uma chave estrangeira que referencia drivers.driver_id)
numero: INT
position: INT
points: INT

-------------------------------------------------------


Descrição das Consultas SQL:
select * from results;

Descrição: Esta consulta seleciona todos os registros da tabela results. O resultado incluirá todas as colunas (result_id, driver_id, numero, position, points) e todas as linhas presentes na tabela.
select * from results where driver_id = "3";

Descrição: Esta consulta seleciona todos os registros da tabela results onde o driver_id é igual a "3". Note que o driver_id é um INT e deveria ser tratado como tal (sem aspas).
select driver_id, driverRef from drivers;

Descrição: Esta consulta retorna duas colunas da tabela drivers: driver_id e driverRef. Isso mostra todos os identificadores e referências dos pilotos cadastrados.
select nome, count(*) from circuits group by nome;

Descrição: Esta consulta conta o número de registros em circuits para cada valor único na coluna nome. Ela agrupa os resultados pelo nome do circuito e exibe o nome do circuito e o número de vezes que esse nome aparece na tabela.
select country from circuits order by country asc;

Descrição: Esta consulta seleciona todas as entradas da coluna country da tabela circuits e as ordena em ordem alfabética ascendente.



---------------------------------------------------------------------------------------------------------
Insights Obtidos com as Consultas:
Todos os Resultados de Corridas:

Você pode visualizar todas as entradas na tabela results, incluindo informações sobre o piloto, sua posição e pontos.
Resultados de um Piloto Específico:

Se driver_id = "3" fosse um valor numérico, você obteria os resultados apenas para o piloto com esse ID específico. Isso ajuda a analisar o desempenho de um piloto específico.
Referências dos Pilotos:

A consulta fornece uma visão clara dos pilotos cadastrados no banco de dados, mostrando suas identificações e referências. Isso é útil para associar resultados a pilotos.
Contagem de Circuitos por Nome:

Você pode identificar quantos circuitos diferentes têm o mesmo nome. Isso é útil para detectar possíveis duplicidades ou verificar a consistência dos dados.
Listagem de Países de Circuitos:

A consulta ordenada ajuda a ver a distribuição dos circuitos por país, facilitando a análise das localizações geográficas.

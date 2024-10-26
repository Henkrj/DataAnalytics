# DataAnalytics
CoderHouse Course

Criação do Projeto do curso de Data Analytics CoderHouse. 


# Objetivo do projeto:
Desenvolver um Dashboard de Análise Estratégica que forneça insights sobre o desempenho de pilotos, construtores, e corridas ao longo das temporadas. 
O dashboard deve apresentar visualizações estratégicas que auxiliem na tomada de decisões e no entendimento de tendências ao longo do tempo, com foco em dados como classificação de pilotos, desempenho de equipes, detalhes de corridas, e estatísticas de performance.

# Escopo do Projeto
O Dashboard incluirá:

Análise de Performance dos Pilotos: classificação de pilotos por corrida e temporada, estatísticas de voltas mais rápidas, posições de largada e chegada.
Desempenho dos Construtores: rankings de construtores por temporada, resultados em corridas específicas e análise de pontos acumulados.
Detalhes e Resultados de Corridas: resumo das corridas com classificação final, dados de pit stops, tempos de volta, e resultados das sessões de qualificação.
Estatísticas de Temporada e Circuitos: comparação entre temporadas e análise das pistas, com detalhes geográficos e de altitude que impactam as corridas.


# Usuário Final e Nível de Aplicação da Análise
Usuário Final: Executivos e analistas estratégicos da equipe de esportes de motor, interessados em entender tendências e otimizar a performance.

Nível de Análise: Estratégico, com o objetivo de obter insights de longo prazo para a tomada de decisões e melhoria de performance.

# Diagrama de entidade-relacionamento das tabelas que contêm as informações a serem analisadas.

![MER_F1](https://github.com/user-attachments/assets/32be2d81-0ec0-4fc4-a66d-5e07cd9424dc)




# Lista de Tabelas e Descrições
<li>Constructors: Armazena informações sobre cada construtor/equipe.
Chave Primária (PK): constructorId — Identificador único do construtor.</li>

<li>Circuits: Contém dados geográficos e descritivos dos circuitos onde as corridas acontecem.

 
Chave Primária (PK): circuitId — Identificador único do circuito.</li>

<li>constructor_results: Guarda os resultados de cada construtor por corrida.
Chave Primária (PK): constructorResultsId.
Chave Estrangeira (FK): raceId (liga-se à tabela races), constructorId (liga-se à tabela constructors).</li>

4. constructor_standings
Descrição: Armazena as classificações de cada construtor em determinada corrida.
Chave Primária (PK): constructorStandingsId.
Chave Estrangeira (FK): raceId (liga-se à tabela races), constructorId (liga-se à tabela constructors).

5. driver_standings
Descrição: Guarda as classificações dos pilotos em cada corrida.
Chave Primária (PK): driverStandingsId.
Chave Estrangeira (FK): raceId (liga-se à tabela races), driverId (liga-se à tabela drivers).

6. drivers
Descrição: Armazena informações pessoais e de identificação dos pilotos.
Chave Primária (PK): driverId.

7. lap_times
Descrição: Guarda o tempo de cada volta realizada por cada piloto em cada corrida.
Chaves Estrangeiras (FK): raceId e driverId.

8. pit_stops
Descrição: Contém informações sobre as paradas nos boxes de cada piloto por corrida.
Chaves Estrangeiras (FK): raceId e driverId.

9. qualifying
Descrição: Armazena dados das sessões de qualificação para determinar a ordem de largada.
Chave Primária (PK): qualifyId.
Chaves Estrangeiras (FK): raceId, driverId, constructorId.

10. races
Descrição: Contém os detalhes de cada corrida, incluindo data, horário, e local.
Chave Primária (PK): raceId.
Chave Estrangeira (FK): circuitId e year (referente a seasons).

11. results
Descrição: Guarda os resultados detalhados de cada piloto em cada corrida.
Chave Primária (PK): resultId.
Chaves Estrangeiras (FK): raceId, driverId, constructorId, statusId.

12. seasons
Descrição: Armazena informações sobre as temporadas de corrida.
Chave Primária (PK): year.

13. sprint_results
Descrição: Guarda resultados das corridas do tipo sprint.
Chave Primária (PK): resultId.
Chaves Estrangeiras (FK): raceId, driverId, constructorId, statusId.

14. status
Descrição: Define os status possíveis dos resultados de corrida.
Chave Primária (PK): statusId.



# Lista de Colunas e Detalhes
Cada coluna da tabela é descrita abaixo, com especificação das chaves primárias e estrangeiras (PK e FK) conforme necessário:

Tabela: constructors
constructorId (PK): Identificador único do construtor.
constructorRef: Referência curta do construtor.
name: Nome do construtor.
nationality: Nacionalidade da equipe.
url: Link com mais informações.


Tabela: circuits
circuitId (PK): Identificador único do circuito.
circuitRef: Referência curta do circuito.
name: Nome do circuito.
location: Localização (cidade).
country: País.
lat, lng, alt: Coordenadas e altitude.
url: Link com mais informações.


Tabela: constructor_results
constructorResultsId (PK): Identificador único dos resultados do construtor.
raceId (FK): Referência para a corrida.
constructorId (FK): Referência para o construtor.
points: Pontos ganhos pelo construtor na corrida.
status: Status do resultado.


Tabela: constructor_standings
constructorStandingsId (PK): Identificador único da classificação.
raceId (FK): Referência para a corrida.
constructorId (FK): Referência para o construtor.
points: Pontos acumulados.
position: Posição do construtor.
positionText: Texto descritivo da posição.
wins: Número de vitórias.


Tabela: driver_standings
driverStandingsId (PK): Identificador único da classificação.
raceId (FK): Referência para a corrida.
driverId (FK): Referência para o piloto.
points: Pontos acumulados.
position: Posição do piloto.
positionText: Texto descritivo da posição.
wins: Número de vitórias.


Tabela: drivers
driverId (PK): Identificador único do piloto.
driverRef: Referência curta do piloto.
number, code: Número e código do piloto.
forename, surname: Nome e sobrenome.
dob: Data de nascimento.
nationality: Nacionalidade.
url: Link com mais informações.


Tabela: lap_times
raceId (FK): Referência para a corrida.
driverId (FK): Referência para o piloto.
lap: Número da volta.
position: Posição do piloto.
time, milliseconds: Tempo de volta.


Tabela: pit_stops
raceId (FK): Referência para a corrida.
driverId (FK): Referência para o piloto.
stop: Número da parada.
lap: Volta em que ocorreu a parada.
time, duration, milliseconds: Tempo de parada.


Tabela: qualifying
qualifyId (PK): Identificador único da sessão de qualificação.
raceId (FK): Referência para a corrida.
driverId (FK): Referência para o piloto.
constructorId (FK): Referência para o construtor.
number: Número do piloto.
position: Posição de largada.
q1, q2, q3: Tempos das sessões qualificatórias.


Tabela: races
raceId (PK): Identificador único da corrida.
year (FK): Referência para a temporada.
round: Número da rodada.
circuitId (FK): Referência para o circuito.
name: Nome da corrida.
date, time: Data e hora.
fp1_date, fp1_time, fp2_date, fp2_time, fp3_date, fp3_time: Datas e horários de práticas.
quali_date, quali_time, sprint_date, sprint_time: Datas e horários de qualificações e sprints.
url: Link com mais informações.


Tabela: results
resultId (PK): Identificador único do resultado.
raceId (FK): Referência para a corrida.
driverId (FK): Referência para o piloto.
constructorId (FK): Referência para o construtor.
number, grid, position, positionOrder: Dados de largada e chegada.
points, laps, time, milliseconds: Dados de pontuação e tempo.
fastestLap, rank, fastestLapTime, fastestLapSpeed: Estatísticas da volta mais rápida.
statusId (FK): Status da corrida.


Tabela: seasons
year (PK): Ano da temporada.
url: Link com mais informações.
Tabela: sprint_results
resultId (PK): Identificador único do resultado.
raceId (FK): Referência para a corrida.
driverId (FK): Referência para o piloto.
constructorId (FK): Referência para o construtor.
number, grid, position, positionOrder: Dados de largada e chegada.
points, laps, time, milliseconds: Dados de pontuação e tempo.
fastestLap, fastestLapTime: Estatísticas da volta mais rápida.
statusId (FK): Status do resultado.


Tabela: status
statusId (PK): Identificador único do status.
status: Descrição do status.

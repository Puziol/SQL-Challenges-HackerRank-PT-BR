  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-18/">Weather Observation Station 18</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Consider P1(a,b) and P2(c,d) to be two points on a 2D plane.
        <br>a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
        <br>b happens to equal the minimum value in Western Longitude (LONG_W in STATION).
        <br>c happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
        <br>d happens to equal the maximum value in Western Longitude (LONG_W in STATION).<br>
Query the Manhattan Distance between points P1 and P2 and round it to a scale of 4 decimal places.
Where LAT_N is the northern latitude and LONG_W is the western longitude.

The STATION table is described as follows:
<br>
    </td>
    </tr>
    
  <tr>
      <th colspan="2">STATION</th>
  </tr>
    
  <tr>
      <th width="50%" align="center">Field</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">ID</td>
      <td width="50%" align="center">NUMBER</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">CITY</td>
      <td width="50%" align="center">VARCHAR2 (21)</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">STATE</td>
      <td width="50%" align="center">VARCHAR2 (2)</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">LAT_N</td>
      <td width="50%" align="center">NUMBER</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">LONG_W</td>
      <td width="50%" align="center">NUMBER</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Considere P1(a, b) e P2(c, d) como dois pontos em um plano 2D.
    <br>O valor de "a" é igual ao valor mínimo da Latitude Norte (LAT_N) na tabela STATION.
    <br>O valor de "b" é igual ao valor mínimo da Longitude Oeste (LONG_W) na tabela STATION.
    <br>O valor de "c" é igual ao valor máximo da Latitude Norte (LAT_N) na tabela STATION.
    <br>O valor de "d" é igual ao valor máximo da Longitude Oeste (LONG_W) na tabela STATION.
    <br>Consultar a Distância de Manhattan (Manhattan Distance) entre os pontos P1 e P2 e arredondá-la para quatro casas decimais.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos encontrar os valores de "a", "b", "c" e "d" especificados na descrição do problema, calcular a Distância de Manhattan entre os pontos P1 e P2 e, em seguida, arredondar o resultado para quatro casas decimais.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT ROUND(ABS(c - a) + ABS(d - b), 4) AS manhattan_distance
  FROM (
    SELECT MIN(LAT_N) AS a, MIN(LONG_W) AS b, MAX(LAT_N) AS c, MAX(LONG_W) AS d
    FROM STATION
  ) AS points;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT MIN(LAT_N) AS a, MIN(LONG_W) AS b, MAX(LAT_N) AS c, MAX(LONG_W) AS d FROM STATION:</b> Essa subconsulta calcula os valores de "a", "b", "c" e "d" especificados na descrição do problema, ou seja, o valor mínimo da Latitude Norte (LAT_N) como "a", o valor mínimo da Longitude Oeste (LONG_W) como "b", o valor máximo da Latitude Norte (LAT_N) como "c" e o valor máximo da Longitude Oeste (LONG_W) como "d".<br>
    <b>2. SELECT ROUND(ABS(c - a) + ABS(d - b), 4) AS manhattan_distance FROM ... AS points:</b> Nesta parte, calculamos a Distância de Manhattan entre os pontos P1(a, b) e P2(c, d), onde "a", "b", "c" e "d" são obtidos da subconsulta. A Distância de Manhattan é calculada somando-se o valor absoluto das diferenças entre as coordenadas, ou seja, ABS(c - a) + ABS(d - b). Em seguida, arredondamos o resultado para quatro casas decimais usando a função ROUND.<br>
    <br>
    <i>A consulta retornará a Distância de Manhattan entre os pontos P1 e P2, arredondada para quatro casas decimais. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

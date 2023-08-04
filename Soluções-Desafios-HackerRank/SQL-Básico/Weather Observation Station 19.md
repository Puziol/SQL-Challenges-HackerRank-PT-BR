  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-19/">Weather Observation Station 19</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Consider P1 (a,c) and P2 (b,d) to be two points on a 2D plane where (a,b) are the respective minimum and maximum values of Northern Latitude (LAT_N) and (c,d) are the respective minimum and maximum values of Western Longitude (LONG_W) in STATION. Query the Euclidean Distance between points P1 and P2 and format your answer to display 4 decimal digits.
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
      <td colspan="2"  align="center"><b>Problema:</b><br>Considere P1(a, c) e P2(b, d) como dois pontos em um plano 2D, onde (a, b) são os valores mínimos e máximos, respectivamente, da Latitude Norte (LAT_N), e (c, d) são os valores mínimos e máximos, respectivamente, da Longitude Oeste (LONG_W) na tabela STATION.<br>
      Consultar a Distância Euclidiana (Euclidean Distance) entre os pontos P1 e P2 e formatar sua resposta para exibir 4 dígitos decimais.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos encontrar os valores de "a", "b", "c" e "d" especificados na descrição do problema, calcular a Distância Euclidiana entre os pontos P1 e P2 e, em seguida, formatar o resultado para exibir 4 dígitos decimais.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT FORMAT(SQRT(POW(b - a, 2) + POW(d - c, 2)), 4) AS euclidean_distance
  FROM (
    SELECT MIN(LAT_N) AS a, MAX(LAT_N) AS b, MIN(LONG_W) AS c, MAX(LONG_W) AS d
    FROM STATION
  ) AS points;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT MIN(LAT_N) AS a, MAX(LAT_N) AS b, MIN(LONG_W) AS c, MAX(LONG_W) AS d FROM STATION:</b> Essa subconsulta calcula os valores de "a", "b", "c" e "d" especificados na descrição do problema, ou seja, o valor mínimo da Latitude Norte (LAT_N) como "a", o valor máximo da Latitude Norte (LAT_N) como "b", o valor mínimo da Longitude Oeste (LONG_W) como "c" e o valor máximo da Longitude Oeste (LONG_W) como "d".<br>
    <b>2. SELECT FORMAT(SQRT(POW(b - a, 2) + POW(d - c, 2)), 4) AS euclidean_distance FROM ... AS points:</b> Nesta parte, calculamos a Distância Euclidiana entre os pontos P1(a, c) e P2(b, d), onde "a", "b", "c" e "d" são obtidos da subconsulta. A Distância Euclidiana é calculada usando a fórmula matemática: SQRT((b - a)^2 + (d - c)^2). Em seguida, usamos a função FORMAT para formatar o resultado para exibir 4 dígitos decimais.<br>
    <br>
    <i>A consulta retornará a Distância Euclidiana entre os pontos P1 e P2, formatada para exibir 4 dígitos decimais. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

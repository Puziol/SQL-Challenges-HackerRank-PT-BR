  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-17/">Weather Observation Station 17</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7780. Round your answer to 4 decimal places.
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
      <td colspan="2"  align="center"><b>Problema:</b><br>Consultar a Longitude Oeste (LONG_W) onde a menor Latitude Norte (LAT_N) na tabela STATION seja maior que 38.7780. Arredonde sua resposta para 4 casas decimais.Para resolver esse problema, precisamos encontrar a Longitude Oeste (LONG_W) correspondente à menor Latitude Norte (LAT_N) na tabela STATION que seja maior que 38.7780 e, em seguida, arredondar a resposta para quatro casas decimais.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos encontrar a Longitude Oeste (LONG_W) correspondente à menor Latitude Norte (LAT_N) na tabela STATION que seja maior que 38.7780 e, em seguida, arredondar a resposta para quatro casas decimais.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT ROUND(LONG_W, 4) AS min_long_w
  FROM STATION
  WHERE LAT_N = (SELECT MIN(LAT_N) FROM STATION WHERE LAT_N > 38.7780);
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT ROUND(LONG_W, 4) AS min_long_w:</b> Isso seleciona a Longitude Oeste (LONG_W) correspondente à menor Latitude Norte (LAT_N) que atende à condição especificada e, em seguida, arredonda o resultado para quatro casas decimais usando a função ROUND.<br>
    <b>2. FROM STATION:</b> Indica a tabela de onde queremos obter os dados, que é a tabela STATION.<br>
    <b>3. WHERE LAT_N = (SELECT MIN(LAT_N) FROM STATION WHERE LAT_N > 38.7780):</b> O WHERE é usado para filtrar os resultados com base na condição de que a Latitude Norte seja a menor entre as que são maiores que 38.7780.<br>
    <br>
    <i>A consulta retornará a Longitude Oeste (LONG_W) correspondente à menor Latitude Norte (LAT_N) na tabela STATION que atende à condição especificada, arredondada para quatro casas decimais. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

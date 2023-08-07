  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-20/">Weather Observation Station 20</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to 4 decimal places.
  The STATION table is described as follows:

  Where LAT_N is the northern latitude and LONG_W is the western longitude.<br>
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
      <td colspan="2"  align="center"><b>Problema:</b><br>Dado a tabela STATION, você deve calcular a mediana das latitudes norte (LAT_N) presentes na tabela. A mediana é definida como o número que separa a metade superior de um conjunto de dados da metade inferior.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>A ideia por trás dessa abordagem é que a mediana é o valor que divide o conjunto de dados em duas partes iguais. A mediana é a média dos dois valores do meio quando o número de elementos é ímpar, ou o valor do meio quando o número de elementos é par. Portanto, a abordagem tenta encontrar o intervalo de valores que inclui a mediana e, em seguida, calcula a média desses valores para obter uma aproximação da mediana.

Essa é uma solução aproximada para calcular a mediana, uma vez que o MySQL não oferece uma função MEDIAN diretamente.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT CAST(LAT_N AS DECIMAL(10,4))
  FROM (
    SELECT LAT_N, ROW_NUMBER() OVER (ORDER BY LAT_N ASC) AS RN
    FROM STATION
  ) A
  WHERE RN = (SELECT CEILING(COUNT(LAT_N) / 2.0) FROM STATION);
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT LAT_N, ROW_NUMBER() OVER (ORDER BY LAT_N ASC) AS RN FROM STATION:</b> Nesta subconsulta, selecionamos a coluna LAT_N da tabela STATION e usamos a função de janela ROW_NUMBER() para atribuir um número de linha (RN) a cada registro, ordenados pelas latitudes norte em ordem crescente.<br>
    <b>2. (SELECT CEILING(COUNT(LAT_N) / 2.0) FROM STATION):</b> Nesta subconsulta, calculamos o número da posição mediana. Contamos quantos registros existem na tabela STATION (usando COUNT(LAT_N)) e, em seguida, dividimos por 2.0 para garantir que o resultado seja um número decimal. Usamos CEILING para arredondar esse valor para cima, porque se tivermos um número ímpar de registros, queremos a posição exata da mediana.<br>
    <b>3. WHERE RN = ...:</b> Nesta parte da consulta, estamos filtrando os resultados da subconsulta anterior para encontrar o registro que corresponde à posição mediana (ou seja, onde RN é igual ao número da posição mediana calculada na subconsulta anterior).<br>
    <b>4. SELECT CAST(LAT_N AS DECIMAL(10,4)):</b> Finalmente, selecionamos a coluna LAT_N do registro que está na posição mediana. Usamos CAST para converter o valor em um tipo DECIMAL com precisão de 4 casas decimais, atendendo ao requisito de arredondamento para 4 casas decimais na resposta.<br>
    <br>
    <i>Essa consulta retorna a mediana das latitudes norte (LAT_N) da tabela STATION, arredondada para 4 casas decimais, seguindo os passos descritos acima. Note que esta abordagem funciona considerando que a função MEDIAN não está disponível no MySQL.</i>
    </td>
  </tr>
    
  </table>

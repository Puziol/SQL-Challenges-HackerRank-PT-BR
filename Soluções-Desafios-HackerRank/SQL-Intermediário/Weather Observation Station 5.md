  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-5/">Weather Observation Station 5</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
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
      <td colspan="2"  align="center"><b>Problema:</b><br>Consulte as duas cidades em STATION com os nomes mais curtos e mais longos, juntamente com seus respectivos comprimentos (ou seja, o número de caracteres no nome). Se houver mais de uma cidade com o menor ou maior tamanho, escolha aquela que aparece primeiro quando ordenada alfabeticamente.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos encontrar as duas cidades com os nomes mais curtos e mais longos, bem como seus comprimentos. Podemos usar a função LENGTH para calcular o comprimento de cada nome de cidade e, em seguida, usar a cláusula ORDER BY para classificar os resultados por ordem crescente e decrescente do comprimento do nome e alfabeticamente em caso de empate. Em seguida, podemos usar a cláusula LIMIT para selecionar apenas as duas primeiras e as duas últimas cidades.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT CITY, LENGTH(CITY) AS name_length
  FROM STATION
  ORDER BY name_length, CITY
  LIMIT 1;

  SELECT CITY, LENGTH(CITY) AS name_length
  FROM STATION
  ORDER BY name_length DESC, CITY
  LIMIT 1;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT CITY, LENGTH(CITY) AS name_length:</b> Isso seleciona o nome da cidade (CITY) da tabela STATION e calcula o comprimento do nome usando a função LENGTH, que é renomeado como "name_length".<br>
    <b>2. FROM STATION:</b> Indica a tabela de onde queremos obter os dados, que é a tabela STATION.<br>
    <b>3. ORDER BY name_length, CITY:</b> Classifica os resultados em ordem crescente com base no comprimento do nome (name_length) e, em caso de empate, em ordem alfabética pelo nome da cidade (CITY).<br>
    <b>4. LIMIT 1:</b> Seleciona apenas a primeira linha dos resultados, que representa a cidade com o nome mais curto.<br>
    <br>
    <i>A consulta retornará as duas cidades com os nomes mais curtos e mais longos, bem como seus respectivos comprimentos. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-2/">Weather Observation Station 2</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Query the following two values from the STATION table:

The sum of all values in LAT_N rounded to a scale of 2 decimal places.  
The sum of all values in LONG_W rounded to a scale of 2 decimal places.  
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
      <td colspan="2"  align="center"><b>Problema:</b><br>Consultar os seguintes dois valores da tabela STATION:  
      A soma de todos os valores em LAT_N arredondada para duas casas decimais.  
      A soma de todos os valores em LONG_W arredondada para duas casas decimais.  
      Onde LAT_N é a latitude norte e LONG_W é a longitude oeste.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos calcular a soma de todos os valores em LAT_N e LONG_W da tabela STATION e arredondar esses valores para duas casas decimais.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT ROUND(SUM(LAT_N), 2) AS sum_lat_n, ROUND(SUM(LONG_W), 2) AS sum_long_w
  FROM STATION;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT ROUND(SUM(LAT_N), 2) AS sum_lat_n:</b> Isso calcula a soma de todos os valores em LAT_N e, em seguida, arredonda o resultado para duas casas decimais usando a função ROUND.<br>
    <b>2. ROUND(SUM(LONG_W), 2) AS sum_long_w:</b> Da mesma forma, isso calcula a soma de todos os valores em LONG_W e arredonda o resultado para duas casas decimais usando a função ROUND.<br>
    <b>3. FROM STATION:</b> Indica a tabela de onde queremos obter os dados, que é a tabela STATION.<br>
    <br>
    <i>A consulta retornará a soma de todos os valores em LAT_N arredondada para duas casas decimais e a soma de todos os valores em LONG_W arredondada para duas casas decimais. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

<table width="100%" border="3" cellspacing="0" cellpadding="8">
  <tr>
    <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-4/">Weather Observation Station 4</a></th>
  </tr>
  
  <tr>
    <td colspan="2" align="center">Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.
The STATION table is described as follows:

Where LAT_N is the northern latitude and LONG_W is the western longitude.<br>
For example, if there are three records in the table with CITY values 'New York', 'New York', 'Bengalaru', there are 2 different city names: 'New York' and 'Bengalaru'. The query returns , because: total number of records - number of unique city names = 3 - 2 = 1.
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
    <td colspan="2"  align="center"><b>Problema:</b><br>Encontre a diferença entre o número total de entradas de cidades (CITY) na tabela e o número de entradas de cidades distintas na tabela STATION. Por exemplo, se houver três registros na tabela com valores de cidades 'Nova Iorque', 'Nova Iorque', 'Bengalaru', haverá 2 nomes de cidades diferentes: 'Nova Iorque' e 'Bengalaru'. A consulta deve retornar a diferença, porque: número total de registros - número de nomes de cidades únicas = 3 - 2 = 1.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos calcular a diferença entre o número total de entradas de cidades (CITY) na tabela STATION e o número de entradas de cidades distintas.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="left">
      <b>Solução em MYSQL</b><br>
      
```sql
SELECT COUNT(CITY) - COUNT(DISTINCT CITY) AS DIFFERENCA
FROM STATION;
```
<br>
</td>
  </tr>
  
<tr>
  <td colspan="2"  align="center">
      <b>Explicação:</b><br>
<b>1. SELECT COUNT(CITY):</b> Isso calcula o número total de entradas de cidades (CITY) na tabela STATION.<br>
<b>2. -:</b> Subtrai o resultado da contagem total pelo próximo cálculo.<br>
<b>3. COUNT(DISTINCT CITY):</b> Isso calcula o número de entradas de cidades distintas na tabela STATION.<br>
<b>4. AS DIFFERENCA:</b> Renomeia a coluna resultante como "DIFFERENCA".<br>
<b>5. FROM STATION:</b> Indica a tabela de onde queremos obter os dados, que é a tabela STATION.<br> 
<br>
<i>A consulta retornará um único valor representando a diferença entre o número total de entradas de cidades e o número de entradas de cidades distintas na tabela STATION. Isso fornecerá o resultado solicitado no problema, onde é calculada a diferença entre o número total de registros e o número de nomes de cidades únicas na tabela.</i>
</td>
  </tr>
  
</table>

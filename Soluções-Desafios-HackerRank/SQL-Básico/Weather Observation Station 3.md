<table width="100%" border="3" cellspacing="0" cellpadding="8">
  <tr>
    <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-3/">Weather Observation Station 3</a></th>
  </tr>
  
  <tr>
    <td colspan="2" align="center">Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
The STATION table is described as follows:

Where LAT_N is the northern latitude and LONG_W is the western longitude.
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
    <td colspan="2"  align="center"><b>Problema:</b><br>Escreva uma consulta SQL para obter uma lista de nomes de cidades (CITY) da tabela STATION para cidades que possuem um número de ID par. Imprima os resultados em qualquer ordem, mas exclua duplicatas da resposta.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos usar uma consulta SQL que selecione os nomes de cidades (CITY) da tabela STATION, onde o número de ID seja par. Além disso, devemos garantir que os resultados não contenham duplicatas.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="left">
      <b>Solução em MYSQL</b><br>
      
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE ID % 2 = 0;
```
<br>
</td>
  </tr>
  
<tr>
  <td colspan="2"  align="center">
      <b>Explicação:</b><br>
<b>1. SELECT DISTINCT CITY:</b> Isso indica que queremos selecionar os nomes de cidades únicos (sem duplicatas) da tabela STATION.<br>
<b>2. FROM STATION:</b> Indica a tabela de onde queremos obter os dados, que é a tabela STATION.<br>
<b>3. WHERE ID % 2 = 0:</b> O WHERE é uma cláusula que filtra os resultados com base em condições específicas. Aqui, estamos filtrando as cidades onde o número de ID é par. O operador % calcula o resto da divisão do ID por 2, e se o resultado for igual a 0, significa que o ID é par.<br>
<i>A consulta retornará uma lista de nomes de cidades (CITY) que possuem um número de ID par na tabela STATION, sem duplicatas. Isso fornecerá os nomes de cidades que atendem aos critérios especificados no problema.</i>
</td>
  </tr>
  
</table>

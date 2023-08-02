<table width="100%" border="3" cellspacing="0" cellpadding="8">
  <tr>
    <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-9/">Weather Observation Station 9</a></th>
  </tr>
  
  <tr>
    <td colspan="2" align="center">Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.
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
    <td colspan="2"  align="center"><b>Problema:</b><br>Consulte a lista de nomes de cidades (CITY) da tabela STATION que não começam com vogais. Seu resultado não pode conter duplicatas.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos consultar os nomes de cidades (CITY) da tabela STATION que não começam com vogais e garantir que o resultado não contenha duplicatas.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="left">
      <b>Solução em MYSQL</b><br>
      
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT REGEXP '^[aeiouAEIOU]';
```
<br>
</td>
  </tr>
  
<tr>
  <td colspan="2"  align="center">
      <b>Explicação:</b><br>
<b>1. SELECT DISTINCT CITY:</b> Isso indica que queremos selecionar os nomes de cidades únicos (sem duplicatas) da tabela STATION.<br>
<b>2. FROM STATION:</b> Indica a tabela de onde queremos obter os dados, que é a tabela STATION.<br>
<b>3. WHERE CITY NOT REGEXP '^[aeiouAEIOU]':</b> O WHERE é uma cláusula que filtra os resultados com base em condições específicas. Aqui, estamos filtrando as cidades onde o nome da cidade não começa com uma vogal. A expressão regular '^[aeiouAEIOU]' verifica se o primeiro caractere do nome da cidade não é uma vogal (minúscula ou maiúscula).<br>
<br>
<i>A consulta retornará uma lista de nomes de cidades (CITY) da tabela STATION que atendem aos critérios de ter vogais como primeiros e últimos caracteres, sem duplicatas. Isso fornecerá o resultado solicitado no problema.</i>
</td>
  </tr>
  
</table>

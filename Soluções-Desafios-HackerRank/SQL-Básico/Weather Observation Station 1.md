<table width="100%" border="3" cellspacing="0" cellpadding="8">
  <tr>
    <th colspan="2"><a href="https://www.hackerrank.com/challenges/weather-observation-station-1/">Weather Observation Station 1</a></th>
  </tr>
  
  <tr>
    <td colspan="2" align="center">Query a list of CITY and STATE from the STATION table.
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
    <td colspan="2"  align="center"><b>Problema:</b><br>Escreva uma consulta SQL para obter uma lista das colunas CITY e STATE da tabela STATION.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Descrição da tabela STATION:</b><br>A tabela STATION contém informações sobre diferentes estações meteorológicas. Ela possui várias colunas, como ID da Estação, Nome da Cidade (CITY), Nome do Estado (STATE), Latitude Norte (LAT_N), Longitude Oeste (LONG_W) e outras informações relevantes.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos usar uma consulta SQL que selecione as colunas CITY e STATE da tabela STATION, que correspondem ao nome da cidade e nome do estado, respectivamente.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="left">
      <b>Solução em MYSQL</b><br>
      
```sql
SELECT CITY, STATE
FROM STATION;
```
<br>
</td>
  </tr>
  
<tr>
  <td colspan="2"  align="center">
      <b>Explicação:</b><br>
<b>1. SELECT CITY, STATE:</b> Isso indica que queremos selecionar apenas os campos "CITY" e "STATE" da tabela STATION, que correspondem ao nome da cidade e ao nome do estado, respectivamente.<br>
<b>2. FROM STATION:</b> Indica a tabela de onde queremos obter os dados, que é a tabela STATION.<br>
<i>A consulta retornará uma lista das cidades (CITY) e estados (STATE) presentes na tabela STATION. Isso fornecerá uma lista com o nome da cidade e o nome do estado para cada estação meteorológica registrada no banco de dados.</i>
</td>
  </tr>
  
</table>

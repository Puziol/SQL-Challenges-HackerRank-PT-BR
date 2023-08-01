<table width="100%" border="3" cellspacing="0" cellpadding="8">
  <tr>
    <th colspan="2"><a href="https://www.hackerrank.com/challenges/revising-the-select-query-2/">Revising the Select Query II</a></th>
  </tr>
  
  <tr>
    <td colspan="2">Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

The CITY table is described as follows:
  </td>
  </tr>
  
  <tr>
    <th colspan="2">CITY</th>
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
    <td width="50%" align="center">NAME</td>
    <td width="50%" align="center">VARCHAR2 (17)</td>
  </tr>
  
  <tr>
    <td width="50%" align="center">COUNTRYCODE</td>
    <td width="50%" align="center">VARCHAR2 (3)</td>
  </tr>
  
  <tr>
    <td width="50%" align="center">DISTRICT</td>
    <td width="50%" align="center">VARCHAR2 (20)</td>
  </tr>
  
  <tr>
    <td width="50%" align="center">POPULATION</td>
    <td width="50%" align="center">NUMBER</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Problema:</b><br>Escreva uma consulta SQL para obter o campo "NAME" de todas as cidades americanas na tabela CITY, onde a população seja maior que 120.000. O código do país para os Estados Unidos é "USA".</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Descrição da tabela CITY:</b><br>A tabela CITY contém informações sobre diferentes cidades. Ela possui várias colunas, como Nome da Cidade, Código do País, Distrito, População e outras informações relevantes.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos usar uma consulta SQL que selecione o campo "NAME" da tabela CITY onde o Código do País é "USA" e a População é maior que 120.000.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center">
      <b>Solução em MYSQL</b><br>
      
```sql
SELECT NAME
FROM CITY
WHERE CountryCode = 'USA' AND Population > 120000;
```
<br>
</td>
  </tr>
  
<tr>
  <td colspan="2"  align="center">
      <b>Explicação:</b><br>
<b>1. SELECT NAME:</b>  Isso indica que queremos selecionar apenas o campo "NAME" da tabela CITY.<br>
<b>2. FROM CITY:</b> Indica a tabela de onde queremos obter os dados, que é a tabela CITY.<br>
<b>3. WHERE CountryCode = 'USA' AND Population > 120000:</b> O WHERE é uma cláusula que filtra os resultados com base em condições específicas. Aqui, estamos filtrando as cidades em que o Código do País é "USA" e a População é maior que 120.000.<br>
<i>A consulta retornará o campo "NAME" das cidades americanas que atendem aos critérios especificados (Código do País é "USA" e População maior que 120.000).</i>
</td>
  </tr>
  
</table>

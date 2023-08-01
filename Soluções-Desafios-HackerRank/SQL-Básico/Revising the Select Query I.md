<table width="100%" border="3" cellspacing="0" cellpadding="8">
  <tr>
    <th colspan="2"><a href="https://www.hackerrank.com/challenges/revising-the-select-query/">Revising the Select Query I</a></th>
  </tr>
  
  <tr>
    <td colspan="2">Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.

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
    <td colspan="2"  align="center"><b>Problema:</b><br>Escreva uma consulta SQL para obter todas as colunas das cidades americanas na tabela CITY com população maior que 100.000. O código do país para os Estados Unidos é "USA".</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Descrição da tabela CITY:</b><br>A tabela CITY contém informações sobre diferentes cidades. Ela possui várias colunas, como Nome da Cidade, Código do País, Distrito, População e outras informações relevantes.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos usar uma consulta SQL que selecione todas as colunas da tabela CITY onde o Código do País é "USA" e a População é maior que 100.000.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center">
      <b>Solução em MYSQL</b>
      
```sql
SELECT * 
FROM CITY
WHERE POPULATION > 100000 AND COUNTRYCODE = 'USA';
```
<br>
</td>
  </tr>
  
<tr>
  <td colspan="2"  align="center">
      <b>Explicação:</b><br>
<b>1. SELECT *:</b> Isso indica que queremos selecionar todas as colunas da tabela CITY.<br>
<b>2. FROM CITY:</b> Indica a tabela de onde queremos obter os dados, que é a tabela CITY.<br>
<b>3. WHERE CountryCode = 'USA' AND Population > 100000:</b> O WHERE é uma cláusula que filtra os resultados com base em condições específicas. Aqui, estamos filtrando as cidades em que o Código do País é "USA" e a População é maior que 100.000.<br>
<i>A consulta retornará todas as colunas das cidades americanas com uma população maior que 100.000, atendendo aos critérios especificados.</i>
</td>
  </tr>
  
</table>

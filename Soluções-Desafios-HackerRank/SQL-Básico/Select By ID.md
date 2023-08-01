<table width="100%" border="3" cellspacing="0" cellpadding="8">
  <tr>
    <th colspan="2"><a href="https://www.hackerrank.com/challenges/select-by-id/">Select By ID</a></th>
  </tr>
  
  <tr>
    <td colspan="2" align="center">Query all columns for a city in CITY with the ID 1661.

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
    <td colspan="2"  align="center"><b>Problema:</b><br>Escreva uma consulta SQL para obter todas as colunas de uma cidade na tabela CITY com o ID 1661.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Descrição da tabela CITY:</b><br>A tabela CITY contém informações sobre diferentes cidades. Ela possui várias colunas, como Nome da Cidade, Código do País, Distrito, População e outras informações relevantes.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos usar uma consulta SQL que selecione todas as colunas de uma cidade específica na tabela CITY, onde o ID da Cidade é igual a 1661.</td>
  </tr>
  
  <tr>
    <td colspan="2"  align="left">
      <b>Solução em MYSQL</b><br>
      
```sql
SELECT *
FROM CITY
WHERE ID = 1661;
```
<br>
</td>
  </tr>
  
<tr>
  <td colspan="2"  align="center">
      <b>Explicação:</b><br>
<b>1. SELECT *:</b> Isso indica que queremos selecionar todas as colunas (atributos) da tabela CITY. O asterisco (*) é um coringa que representa todas as colunas na tabela.<br>
<b>2. FROM CITY:</b> Indica a tabela de onde queremos obter os dados, que é a tabela CITY.<br>
<b>3. WHERE ID = 1661:</b> O WHERE é uma cláusula que filtra os resultados com base em condições específicas. Neste caso, estamos filtrando as cidades onde o ID da Cidade é igual a 1661.<br>
<i>A consulta retornará todas as colunas da cidade que possui o ID igual a 1661 na tabela CITY. Isso fornecerá todas as informações disponíveis sobre essa cidade específica presente no banco de dados.
</i>
</td>
  </tr>
  
</table>

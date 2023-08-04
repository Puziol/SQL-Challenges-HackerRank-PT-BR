  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/population-density-difference/">Population Density Difference</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Query the difference between the maximum and minimum populations in CITY.

The CITY table is described as follows:<br>
    </td>
  </tr>
    
  <tr>
    <th colspan="2">CITY</th>
  </tr>
  
  <tr>
    <th width="50%" align="center">Campo</th>
    <th width="50%" align="center">Tipo</th>
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
      <td colspan="2"  align="center"><b>Problema:</b><br>Consultar a diferença entre as populações máxima e mínima na tabela CITY.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela CITY:</b><br>A tabela CITY contém informações sobre várias cidades. Ela possui várias colunas, como ID da Cidade (ID), Nome da Cidade (Name), Código do País (CountryCode), Distrito (District) e População (Population).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos encontrar a população máxima e a população mínima na tabela CITY e, em seguida, calcular a diferença entre esses valores.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT MAX(Population) - MIN(Population)
  FROM CITY;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT MAX(Population) - MIN(Population):</b> Isso indica que queremos calcular a diferença entre a população máxima e a população mínima de todas as cidades na tabela CITY.<br>
    <b>2. FROM CITY:</b> Indica a tabela de onde queremos obter os dados, que é a tabela CITY.<br>
    <br>
    <i>A consulta retornará a diferença entre as populações máxima e mínima na tabela CITY. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

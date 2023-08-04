  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/average-population/">Average Population</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Query the average population for all cities in CITY, rounded down to the nearest integer.

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
      <td colspan="2"  align="center"><b>Problema:</b><br>Consultar a média da população de todas as cidades na tabela CITY, arredondada para o número inteiro mais próximo.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela CITY:</b><br>A tabela CITY contém informações sobre várias cidades. Ela possui várias colunas, como ID da Cidade (ID), Nome da Cidade (Name), Código do País (CountryCode), Distrito (District) e População (Population).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos usar a função de agregação AVG para calcular a média da população de todas as cidades na tabela CITY e, em seguida, arredondar esse valor para o número inteiro mais próximo.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT ROUND(AVG(Population))
  FROM CITY;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT ROUND(AVG(Population)):</b> Isso indica que queremos calcular a média da população de todas as cidades na tabela CITY usando a função AVG e, em seguida, arredondar o resultado para o número inteiro mais próximo usando a função ROUND.<br>
    <b>2. FROM CITY:</b> Indica a tabela de onde queremos obter os dados, que é a tabela CITY.<br>
    <br>
    <i>A consulta retornará a média da população de todas as cidades na tabela CITY, arredondada para o número inteiro mais próximo. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/japan-population/">Japan Population</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

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
      <td colspan="2"  align="center"><b>Problema:</b><br>Consultar a soma das populações de todas as cidades japonesas na tabela CITY. O COUNTRYCODE para o Japão é JPN.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela CITY:</b><br>A tabela CITY contém informações sobre várias cidades. Ela possui várias colunas, como ID da Cidade (ID), Nome da Cidade (Name), Código do País (CountryCode), Distrito (District) e População (Population).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos usar a função de agregação SUM para somar as populações de todas as cidades japonesas na tabela CITY, onde o COUNTRYCODE é "JPN".</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT SUM(Population)
  FROM CITY
  WHERE CountryCode = 'JPN';
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT SUM(Population):</b> Isso indica que queremos calcular a soma das populações de todas as cidades que atendem à condição especificada.<br>
    <b>2. FROM CITY:</b> Indica a tabela de onde queremos obter os dados, que é a tabela CITY.<br>
    <b>3. WHERE CountryCode = 'JPN':</b> O WHERE é usado para filtrar os resultados com base em condições específicas. Aqui, estamos filtrando as cidades onde o COUNTRYCODE é igual a "JPN", que representa o Japão.<br>
    <br>
    <i>A consulta retornará a soma das populações de todas as cidades japonesas na tabela CITY. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

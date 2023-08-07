  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/african-cities/">African Cities</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

The CITY and COUNTRY tables are described as follows:<br>
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
    <th colspan="2">COUNTRY</th>
  </tr>
  
  <tr>
    <th width="50%" align="center">Field</th>
    <th width="50%" align="center">Type</th>
  </tr>
  
  <tr>
    <td width="50%" align="center">CODE</td>
    <td width="50%" align="center">VARCHAR2 (3)</td>
  </tr>
  
  <tr>
    <td width="50%" align="center">CONTINENT</td>
    <td width="50%" align="center">VARCHAR2 (13)</td>
  </tr>
  
  <tr>
    <td colspan="2" align="center">...</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Dadas as tabelas CITY e COUNTRY, consultar os nomes de todas as cidades onde o CONTINENTE é 'Africa'.

Observação: As colunas CITY.CountryCode e COUNTRY.Code são chaves correspondentes.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela CITY e COUNTRY:</b><br>A tabela CITY contém informações sobre várias cidades, incluindo colunas como ID da cidade (ID), Nome da cidade (Name), População (Population), Código do País (CountryCode) e outras.  
      A tabela COUNTRY contém informações sobre vários países, incluindo colunas como Código do País (Code), Nome do País (Name), Continente (Continent) e outras.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos realizar um JOIN entre as tabelas CITY e COUNTRY usando a chave correspondente (CITY.CountryCode = COUNTRY.Code) para obter as cidades que pertencem ao continente 'Africa'. Em seguida, selecionamos os nomes das cidades.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT CITY.Name
  FROM CITY
  JOIN COUNTRY ON CITY.CountryCode = COUNTRY.Code
  WHERE COUNTRY.Continent = 'Africa';
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT CITY.Name:</b> Isso seleciona a coluna "Name" da tabela CITY, que representa o nome da cidade.<br>
    <b>2. FROM CITY:</b> Indica a tabela de onde queremos obter os dados, que é a tabela CITY.<br>
    <b>3. JOIN COUNTRY ON CITY.CountryCode = COUNTRY.Code:</b> Realiza um INNER JOIN entre as tabelas CITY e COUNTRY usando a chave correspondente CITY.CountryCode e COUNTRY.Code para obter as informações do país de cada cidade.
    <b>4. WHERE COUNTRY.Continent = 'Africa':</b> Filtra os resultados para incluir apenas as cidades cujo país tem o continente 'Africa'..<br>
    <br>
    <i>A consulta retornará os nomes de todas as cidades que pertencem ao continente 'Africa'. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

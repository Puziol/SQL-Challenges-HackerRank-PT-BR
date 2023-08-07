  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/average-population-of-each-continent/">Average Population of Each Continent</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

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
      <td colspan="2"  align="center"><b>Problema:</b><br>Dadas as tabelas CITY e COUNTRY, consultar os nomes de todos os continentes (COUNTRY.Continent) e suas respectivas médias das populações das cidades (CITY.Population) arredondadas para o inteiro mais próximo.

Observação: As colunas CITY.CountryCode e COUNTRY.Code são chaves correspondentes.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição das tabela CITY e COUNTRY:</b><br>A tabela CITY contém informações sobre várias cidades, incluindo colunas como ID da cidade (ID), Nome da cidade (Name), População (Population), Código do País (CountryCode) e outras.  
      A tabela COUNTRY contém informações sobre vários países, incluindo colunas como Código do País (Code), Nome do País (Name), Continente (Continent) e outras.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos realizar um JOIN entre as tabelas CITY e COUNTRY usando a chave correspondente (CITY.CountryCode = COUNTRY.Code) para obter as informações do país de cada cidade. Em seguida, agrupamos os resultados pelo continente (COUNTRY.Continent) e calculamos a média das populações das cidades para cada continente, arredondando para o inteiro mais próximo.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT COUNTRY.Continent, FLOOR(AVG(CITY.Population)) AS average_population
  FROM CITY
  JOIN COUNTRY ON CITY.CountryCode = COUNTRY.Code
  GROUP BY COUNTRY.Continent;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT COUNTRY.Continent:</b> Isso seleciona a coluna "Continent" da tabela COUNTRY, que representa o continente.<br>
    <b>2. FLOOR(AVG(CITY.Population)) AS average_population:</b> Calculamos a média das populações das cidades (CITY.Population) usando a função AVG e arredondamos para o inteiro mais próximo usando a função FLOOR. O resultado é atribuído à coluna "average_population" na saída.<br>
    <b>3. FROM CITY:</b> Indica que estamos selecionando dados da tabela CITY.<br>
    <b>4. JOIN COUNTRY ON CITY.CountryCode = COUNTRY.Code:</b> Realiza um INNER JOIN entre as tabelas CITY e COUNTRY usando a chave correspondente CITY.CountryCode e COUNTRY.Code para obter as informações do país de cada cidade.<br>
    <b>5. GROUP BY COUNTRY.Continent:</b> Agrupa os resultados pelo continente (COUNTRY.Continent), para que possamos calcular a média das populações das cidades para cada continente.<br>
    <br>
    <i>A consulta retornará os nomes de todos os continentes e suas respectivas médias das populações das cidades, arredondadas para o inteiro mais próximo. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

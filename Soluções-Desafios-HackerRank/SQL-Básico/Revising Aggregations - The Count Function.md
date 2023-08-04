  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/revising-aggregations-the-count-function/">Revising Aggregations - The Count Function</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Query a count of the number of cities in CITY having a Population larger than 100000.

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
      <td colspan="2"  align="center"><b>Problema:</b><br>Consultar a contagem do número de cidades na tabela CITY que têm uma População maior que 100000.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela CITY:</b><br>A tabela CITY contém informações sobre várias cidades. Ela possui várias colunas, como ID da Cidade (ID), Nome da Cidade (Name), Código do País (CountryCode), Distrito (District) e População (Population).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos usar a função de agregação COUNT para contar o número de cidades na tabela CITY que têm uma população maior que 100000.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT COUNT(*)
  FROM CITY
  WHERE Population > 100000;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT COUNT(*):</b> Isso indica que queremos selecionar a contagem do número de registros que atendem às condições especificadas.<br>
    <b>2. FROM CITY:</b> Indica a tabela de onde queremos obter os dados, que é a tabela CITY.<br>
    <b>3. WHERE Population > 100000:</b> O WHERE é usado para filtrar os resultados com base em condições específicas. Aqui, estamos filtrando as cidades onde a população é maior que 100000.<br>
    <br>
    <i>A consulta retornará o número de cidades na tabela CITY que têm uma população maior que 100000. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

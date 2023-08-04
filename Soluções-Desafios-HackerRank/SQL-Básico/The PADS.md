  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/the-pads/">The PADS</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Generate the following two result sets:

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:  
There are a total of [occupation_count] [occupation]s.  
where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.  
Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.
Note: There will be at least two entries in the table for each type of occupation.  

The OCCUPATIONS table is described as follows:<br>
    </td>
  </tr>
    
  <tr>
      <th colspan="2">OCCUPATIONS</th>
  </tr>
    
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">Name</td>
      <td width="50%" align="center">String</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">Occupation</td>
      <td width="50%" align="center">String</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Gerar os seguintes dois conjuntos de resultados:

Consultar uma lista ordenada alfabeticamente de todos os nomes em OCCUPATIONS, seguido imediatamente pela primeira letra de cada profissão entre parênteses. Por exemplo: AnActorName(A), ADoctorName(D), AProfessorName(P) e ASingerName(S).

Consultar o número de ocorrências de cada profissão em OCCUPATIONS. Ordenar as ocorrências em ordem crescente e apresentá-las no seguinte formato:
"There are a total of' [occupation_count] [occupation]s."
onde [occupation_count] é o número de ocorrências de uma profissão em OCCUPATIONS e [occupation] é o nome da profissão em letras minúsculas. Se mais de uma profissão tiver o mesmo [occupation_count], elas devem ser ordenadas alfabeticamente. A tabela OCCUPATIONS conterá apenas um dos seguintes valores: Doctor, Professor, Singer ou Actor. Observação: Haverá pelo menos duas entradas na tabela para cada tipo de profissão.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela OCCUPATIONS:</b><br>A tabela OCCUPATIONS contém informações sobre várias profissões. Ela possui duas colunas, Name (nome) e Occupation (profissão).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos gerar dois conjuntos de resultados distintos. No primeiro conjunto, precisamos juntar os nomes das pessoas e a primeira letra de sua profissão entre parênteses. No segundo conjunto, precisamos contar o número de ocorrências de cada profissão e apresentar o resultado no formato solicitado.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT CONCAT(Name, '(', LEFT(Occupation, 1), ')')
    FROM OCCUPATIONS
      ORDER BY Name;
  SELECT CONCAT('There are a total of ', COUNT(*), ' ', LOWER(Occupation), 's.')
    FROM OCCUPATIONS
      GROUP BY Occupation
        ORDER BY COUNT(*), Occupation;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação consulta 1:</b><br>
    <b>1. CONCAT(Name, '(', LEFT(Occupation, 1), ')'):</b> Isso combina o nome e a primeira letra da profissão entre parênteses.<br>
    <b>2. FROM OCCUPATIONS:</b> Indica a tabela de onde queremos obter os dados, que é a tabela OCCUPATIONS.<br>
    <b>3. ORDER BY Name:</b> Ordena os resultados em ordem alfabética pelo nome.<br>
    <b>Explicação consulta 2:</b><br>
    <b>4. CONCAT('There are a total of ', COUNT(*), ' ', LOWER(Occupation), 's.'):</b> Combina o texto com o número de ocorrências da profissão em OCCUPATIONS, convertendo a profissão para minúsculas.<br>
    <b>5. FROM OCCUPATIONS:</b> Indica a tabela de onde queremos obter os dados, que é a tabela OCCUPATIONS.<br>
    <b>6. GROUP BY Occupation:</b> Agrupa os resultados por profissão.<br>
    <b>7. ORDER BY COUNT(*), Occupation:</b> Ordena os resultados pelo número de ocorrências e, em caso de empate, alfabeticamente pela profissão.<br>
    <br>
    <i>A primeira consulta retornará a lista de nomes em OCCUPATIONS seguida da primeira letra da profissão entre parênteses, em ordem alfabética. A segunda consulta retornará o número de ocorrências de cada profissão em OCCUPATIONS, ordenado conforme especificado.
    A junção das duas consultas apresentará os resultados conforme solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

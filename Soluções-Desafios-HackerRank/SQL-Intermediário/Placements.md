  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/placements/">Placements</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). Packages contains two columns: ID and Salary (offered salary in $ thousands per month).

Write a query to output the names of those students whose best friends got offered a higher salary than them. Names must be ordered by the salary amount offered to the best friends. It is guaranteed that no two students got same salary offer.<br>
    </td>
    </tr>

  <tr>
      <th colspan="2">STUDENTS</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">ID</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">Name</td>
      <td width="50%" align="center">String</td>
  </tr>

  <tr>
      <th colspan="2">FRIENDS</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">ID</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">Friend_ID</td>
      <td width="50%" align="center">Integer</td>
  </tr>

  <tr>
      <th colspan="2">PACKAGES</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">ID</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">Salary</td>
      <td width="50%" align="center">Float</td>
  </tr>

  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>O problema apresenta três tabelas: Students (Estudantes), Friends (Amigos) e Packages (Ofertas de Salários). Cada tabela tem duas colunas:

A tabela Students contém duas colunas: ID e Name (ID e Nome do estudante).
A tabela Friends contém duas colunas: ID e Friend_ID (ID do estudante e ID do melhor amigo).
A tabela Packages contém duas colunas: ID e Salary (ID do estudante e Salário oferecido em milhares de dólares por mês).
O objetivo é escrever uma consulta SQL para obter os nomes dos estudantes cujos melhores amigos receberam um salário maior do que eles. Os resultados devem ser ordenados pelo valor do salário oferecido aos melhores amigos em ordem crescente.

É garantido que nenhum estudante recebeu duas ofertas de salário iguais, ou seja, os salários oferecidos a cada estudante são únicos.

Portanto, a consulta SQL deve comparar os salários dos estudantes com os salários dos melhores amigos e retornar os nomes dos estudantes cujos melhores amigos têm um salário maior, ordenados pelo valor do salário oferecido aos melhores amigos em ordem crescente.
</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
SELECT S.NAME
FROM STUDENTS AS S
INNER JOIN FRIENDS AS F ON S.ID = F.ID
INNER JOIN PACKAGES AS P1 ON F.ID = P1.ID
INNER JOIN PACKAGES AS P2 ON F.FRIEND_ID = P2.ID
WHERE P2.SALARY > P1.SALARY
ORDER BY P2.SALARY ASC
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT S.NAME:</b> Nesta linha, estamos selecionando a coluna "NAME" (nome) da tabela "STUDENTS". Isso significa que o resultado da consulta será uma lista de nomes dos estudantes que atendem às condições especificadas nas junções e no filtro (WHERE).<br>
    <b>2. FROM STUDENTS AS S:</b> Aqui, estamos selecionando a tabela "STUDENTS" e atribuindo um alias (apelido) "S" a ela. O alias "S" será usado como uma forma mais curta de se referir à tabela "STUDENTS" nas outras partes da consulta.<br>
    <b>3. INNER JOIN FRIENDS AS F ON S.ID = F.ID:</b> Nesta linha, estamos fazendo uma junção interna (INNER JOIN) entre a tabela "STUDENTS" (com o alias "S") e a tabela "FRIENDS" (com o alias "F") usando a coluna "ID" como chave de junção. Isso combina os registros das duas tabelas com base no ID do estudante e no ID do melhor amigo.<br>
    <b>4. INNER JOIN PACKAGES AS P1 ON F.ID = P1.ID:</b> Aqui, estamos fazendo outra junção interna, desta vez entre a tabela "FRIENDS" (com o alias "F") e a tabela "PACKAGES" (com o alias "P1"), usando a coluna "ID" como chave de junção. Isso combina os registros das tabelas "FRIENDS" e "PACKAGES" para obter os salários oferecidos aos estudantes.<br>
    <b>5. INNER JOIN PACKAGES AS P2 ON F.FRIEND_ID = P2.ID:</b> Novamente, estamos fazendo uma junção interna entre a tabela "FRIENDS" (com o alias "F") e a tabela "PACKAGES" (com o alias "P2"), desta vez usando a coluna "FRIEND_ID" como chave de junção. Isso combina os registros das tabelas "FRIENDS" e "PACKAGES" para obter os salários oferecidos aos melhores amigos dos estudantes.<br>
    <b>6. WHERE P2.SALARY > P1.SALARY:</b> Esta cláusula WHERE é usada para filtrar os resultados da junção, mantendo apenas os registros onde o salário do melhor amigo (P2.SALARY) é maior que o salário do estudante (P1.SALARY).<br>
    <b>7. ORDER BY P2.SALARY ASC:</b> Por fim, estamos ordenando os resultados em ordem crescente com base no salário do melhor amigo (P2.SALARY). Isso significa que os nomes dos estudantes serão listados em ordem crescente de acordo com os salários oferecidos aos seus melhores amigos.<br>
    </td>
  </tr>
    
  </table>

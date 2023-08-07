  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/challenges/">Challenges</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Julia asked her students to create some coding challenges. Write a query to print the hacker_id, name, and the total number of challenges created by each student. Sort your results by the total number of challenges in descending order. If more than one student created the same number of challenges, then sort the result by hacker_id. If more than one student created the same number of challenges and the count is less than the maximum number of challenges created, then exclude those students from the result.

The following tables contain challenge data:

Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker. 

Challenges: The challenge_id is the id of the challenge, and hacker_id is the id of the student who created the challenge.<br>
    </td>
    </tr>

  <tr>
      <th colspan="2">HACKERS</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">hacker_id</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">name</td>
      <td width="50%" align="center">String</td>
  </tr>

  <tr>
      <th colspan="2">CHALLENGES</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">challenge_id</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">hacker_id</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Julia pediu aos seus alunos para criarem alguns desafios de codificação. A tarefa é escrever uma consulta que imprima o hacker_id, nome e o número total de desafios criados por cada aluno. Os resultados devem ser ordenados pelo número total de desafios em ordem decrescente. Se mais de um aluno criar o mesmo número de desafios, então os resultados devem ser ordenados pelo hacker_id. Além disso, se mais de um aluno criar o mesmo número de desafios e a contagem for menor que o número máximo de desafios criados, esses alunos devem ser excluídos do resultado.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT
      h.hacker_id, 
      h.name, 
      COUNT(c.challenge_id) AS contador 
  FROM 
      Hackers h 
      JOIN 
      Challenges c 
      ON h.hacker_id = c.hacker_id 
  GROUP BY 
      h.hacker_id,
      h.name
  HAVING
      contador = (SELECT COUNT(challenge_id) AS cn 
                  FROM Challenges 
                  GROUP BY hacker_id 
                  ORDER BY cn DESC 
                  LIMIT 1) 
      OR 
      contador IN (SELECT t.total 
                   FROM (SELECT COUNT(*) AS total 
                         FROM Challenges 
                         GROUP BY hacker_id) t 
                   GROUP BY t.total 
                   HAVING COUNT(t.total) = 1) 
  ORDER BY 
      contador DESC,
      h.hacker_id;

  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    1. A consulta começa selecionando o hacker_id, nome e contando o número de desafios usando a função COUNT para cada hacker na tabela Hackers, juntamente com a tabela Challenges.<br>
    2. Os resultados são agrupados pelo hacker_id e nome usando a cláusula GROUP BY.<br>
    3. A cláusula HAVING é usada para filtrar os resultados com base nas condições definidas:  
Primeiro, verifica se a contagem de desafios (contador) é igual à contagem máxima de desafios criados por um único hacker, que é obtida de uma subconsulta.  
Em seguida, verifica se a contagem de desafios (contador) está presente nos totais únicos de desafios criados por um hacker, onde apenas um hacker tem aquele total de desafios.<br>
    4. Os resultados finais são ordenados pelo contador em ordem decrescente e, em seguida, pelo hacker_id em caso de empate.<br>
    <br>
    <i>Em resumo, a solução realiza junções entre as tabelas "Hackers" e "Challenges", calcula o número total de desafios para cada aluno, aplica os filtros necessários para atender aos critérios do problema e, finalmente, ordena os resultados de acordo com as especificações dadas.</i>
    </td>
  </tr>
    
  </table>

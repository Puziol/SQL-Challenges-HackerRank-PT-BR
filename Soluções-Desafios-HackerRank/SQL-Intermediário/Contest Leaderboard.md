  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/contest-leaderboard/">Contest Leaderboard</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!

The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of 0 from your result.<br>
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
      <th colspan="2">SUBMISSIONS</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">submission_id</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">hacker_id</td>
      <td width="50%" align="center">Integer</td>
  </tr>

  <tr>
      <td width="50%" align="center">challenge_id</td>
      <td width="50%" align="center">Integer</td>
  </tr>

  <tr>
      <td width="50%" align="center">score</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>O problema se refere a um concurso de programação onde vários hackers participam e enfrentam diferentes desafios. Cada hacker recebe uma pontuação para cada desafio, e a pontuação total de um hacker é a soma de suas pontuações máximas em todos os desafios.

O objetivo é escrever uma consulta SQL para imprimir o ID do hacker (hacker_id), o nome do hacker (name) e a pontuação total (total score) de todos os hackers. Os resultados devem ser ordenados em ordem decrescente com base na pontuação total. Se mais de um hacker tiver a mesma pontuação total, então os resultados devem ser ordenados em ordem crescente pelo ID do hacker.

Além disso, o problema requer que sejam excluídos do resultado os hackers que tenham uma pontuação total igual a zero.

Em resumo, a consulta SQL deve calcular a pontuação total de cada hacker, classificá-los pela pontuação total em ordem decrescente e, em caso de empate na pontuação total, ordenar os hackers pelo ID do hacker em ordem crescente. Também é necessário garantir que hackers com pontuação total igual a zero não sejam incluídos na resposta.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT 
      T.HACKER_ID, 
      H.NAME, 
      SUM(T.S) AS TOTAL
  FROM 
      (SELECT 
          HACKER_ID,
          CHALLENGE_ID,
          MAX(SCORE) AS S
      FROM
          SUBMISSIONS
      GROUP BY
          HACKER_ID,
          CHALLENGE_ID
      ) T
      JOIN
      HACKERS H
      ON H.HACKER_ID= T.HACKER_ID
  GROUP BY
      T.HACKER_ID,
      H.NAME
  HAVING 
      TOTAL>0
  ORDER BY 
      TOTAL DESC,
      T.HACKER_ID;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT T.HACKER_ID, H.NAME, SUM(T.S) AS TOTAL:</b> Nesta linha, estamos selecionando três colunas para a nossa saída final. "T.HACKER_ID" representa o ID do hacker, "H.NAME" representa o nome do hacker e "SUM(T.S) AS TOTAL" representa a soma das pontuações máximas de cada hacker em todos os desafios.<br>
    <b>2. FROM (SELECT HACKER_ID, CHALLENGE_ID, MAX(SCORE) AS S FROM SUBMISSIONS GROUP BY HACKER_ID, CHALLENGE_ID) T:</b> Aqui, estamos criando uma subconsulta (subquery). Essa subconsulta seleciona três colunas da tabela "SUBMISSIONS": "HACKER_ID", "CHALLENGE_ID" e "MAX(SCORE) AS S". A subconsulta agrupa os resultados pelo ID do hacker e pelo ID do desafio e, para cada grupo, seleciona a pontuação máxima (MAX) entre todas as submissões desse hacker para esse desafio. Chamamos essa subconsulta de "T".<br>
    <b>3. JOIN HACKERS H ON H.HACKER_ID = T.HACKER_ID:</b> Nesta linha, estamos juntando a tabela "HACKERS" à subconsulta "T" usando a coluna "HACKER_ID" como chave de junção. Isso nos permite obter o nome do hacker correspondente para cada "HACKER_ID" na subconsulta "T".<br>
    <b>4. GROUP BY T.HACKER_ID, H.NAME:</b> Estamos agrupando os resultados pelo ID do hacker (HACKER_ID) e pelo nome do hacker (NAME). Isso é necessário para calcular a soma das pontuações máximas de cada hacker em todos os desafios.<br>
    <b>5. HAVING TOTAL > 0:</b> Com essa cláusula "HAVING", estamos filtrando os resultados após a agregação para incluir apenas os hackers cuja pontuação total (TOTAL) é maior que zero. Isso é para excluir os hackers com uma pontuação total de zero, conforme exigido pelo problema.<br>
    <b>6. ORDER BY TOTAL DESC, T.HACKER_ID:</b> Por fim, estamos ordenando os resultados. Primeiro, ordenamos em ordem decrescente com base na pontuação total (TOTAL), garantindo que os hackers com a maior pontuação apareçam primeiro. Em caso de empate na pontuação total, ordenamos os hackers em ordem crescente pelo ID do hacker (HACKER_ID).<br>
    </td>
  </tr>
    
  </table>

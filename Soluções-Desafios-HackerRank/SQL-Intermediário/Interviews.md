  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/interviews/">Interviews</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Samantha interviews many candidates from different colleges using coding challenges and contests. Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are 0.

Note: A specific contest can be used to screen candidates at more than one college, but each college only holds 1 screening contest.

Input Format

The following tables hold interview data:

Contests: The contest_id is the id of the contest, hacker_id is the id of the hacker who created the contest, and name is the name of the hacker. 

Colleges: The college_id is the id of the college, and contest_id is the id of the contest that Samantha used to screen the candidates. 

Challenges: The challenge_id is the id of the challenge that belongs to one of the contests whose contest_id Samantha forgot, and college_id is the id of the college where the challenge was given to candidates. 

View_Stats: The challenge_id is the id of the challenge, total_views is the number of times the challenge was viewed by candidates, and total_unique_views is the number of times the challenge was viewed by unique candidates. 

Submission_Stats: The challenge_id is the id of the challenge, total_submissions is the number of submissions for the challenge, and total_accepted_submission is the number of submissions that achieved full scores. <br>
    </td>
    </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>O problema envolve dados de entrevistas realizadas por Samantha com vários candidatos de diferentes faculdades usando desafios e competições de codificação.

As tabelas envolvidas são:

Tabela "Contests": Contém informações sobre os concursos de codificação, incluindo contest_id (ID do concurso), hacker_id (ID do hacker que criou o concurso) e name (nome do hacker).

Tabela "Colleges": Contém informações sobre as faculdades, incluindo college_id (ID da faculdade) e contest_id (ID do concurso usado para selecionar candidatos na faculdade).

Tabela "Challenges": Contém informações sobre os desafios de codificação, incluindo challenge_id (ID do desafio) e college_id (ID da faculdade onde o desafio foi aplicado).

Tabela "View_Stats": Contém informações sobre as visualizações dos desafios pelos candidatos, incluindo challenge_id (ID do desafio), total_views (número total de visualizações do desafio) e total_unique_views (número total de visualizações únicas do desafio).

Tabela "Submission_Stats": Contém informações sobre as submissões dos candidatos aos desafios, incluindo challenge_id (ID do desafio), total_submissions (número total de submissões para o desafio) e total_accepted_submission (número total de submissões que alcançaram a pontuação máxima).

O objetivo é escrever uma consulta SQL para imprimir o contest_id (ID do concurso), hacker_id (ID do hacker), name (nome do hacker) e as somas de total_submissions (total de submissões), total_accepted_submissions (total de submissões aceitas), total_views (total de visualizações) e total_unique_views (total de visualizações únicas) para cada concurso. Os resultados devem ser ordenados por contest_id. Além disso, devemos excluir os concursos do resultado se todas as quatro somas (total_submissions, total_accepted_submissions, total_views e total_unique_views) forem iguais a zero.

Em resumo, a consulta SQL deve agregar os dados relevantes das diferentes tabelas com base nos concursos, calcular as somas e exibir os resultados ordenados por contest_id, excluindo os concursos sem atividade relevante (todas as somas iguais a zero).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT 
      c.contest_id, 
      c.hacker_id, 
      c.name, 
      SUM(ss.total_submissions) AS total_submissions_sum, 
      SUM(ss.total_accepted_submissions) AS total_accepted_submissions_sum, 
      SUM(vs.total_views) AS total_views_sum, 
      SUM(vs.total_unique_views) AS total_unique_views_sum
  FROM 
      contests AS c
  JOIN 
      colleges AS co ON c.contest_id = co.contest_id
  JOIN 
      challenges AS ch ON co.college_id = ch.college_id
  LEFT JOIN 
      (
          SELECT 
              challenge_id, 
              SUM(total_views) AS total_views, 
              SUM(total_unique_views) AS total_unique_views
          FROM 
              view_stats
          GROUP BY 
              challenge_id
      ) AS vs ON ch.challenge_id = vs.challenge_id
  LEFT JOIN 
      (
          SELECT 
              challenge_id, 
              SUM(total_submissions) AS total_submissions, 
              SUM(total_accepted_submissions) AS total_accepted_submissions
          FROM 
              submission_stats
          GROUP BY 
              challenge_id
      ) AS ss ON ch.challenge_id = ss.challenge_id
  GROUP BY 
      c.contest_id, 
      c.hacker_id, 
      c.name
  HAVING 
      total_submissions_sum != 0 
      AND total_accepted_submissions_sum != 0
      AND total_views_sum != 0
      AND total_unique_views_sum != 0
  ORDER BY 
      c.contest_id;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT c.contest_id, c.hacker_id, c.name, ...:</b> Nesta linha, estamos selecionando as colunas "contest_id" (ID do concurso), "hacker_id" (ID do hacker), "name" (nome do hacker) e as colunas calculadas com as somas das estatísticas relevantes: "total_submissions_sum" (soma total de submissões), "total_accepted_submissions_sum" (soma total de submissões aceitas), "total_views_sum" (soma total de visualizações) e "total_unique_views_sum" (soma total de visualizações únicas).<br>
    <b>2. FROM contests AS c:</b> Aqui, estamos selecionando a tabela "contests" e atribuindo um alias "c" a ela. O alias "c" será usado como uma forma mais curta de se referir à tabela "contests" nas outras partes da consulta.<br>
    <b>3. JOIN colleges AS co ON c.contest_id = co.contest_id:</b> Nesta linha, estamos fazendo uma junção (JOIN) interna entre as tabelas "contests" (com o alias "c") e "colleges" (com o alias "co") usando a coluna "contest_id" como chave de junção. Isso combina os registros das duas tabelas com base no ID do concurso.<br>
    <b>4. JOIN challenges AS ch ON co.college_id = ch.college_id:</b> Aqui, estamos fazendo outra junção interna entre as tabelas "colleges" (com o alias "co") e "challenges" (com o alias "ch") usando a coluna "college_id" como chave de junção. Isso combina os registros das tabelas "colleges" e "challenges" com base no ID da faculdade onde o desafio foi aplicado.<br>
    <b>5. LEFT JOIN (...) AS vs ON ch.challenge_id = vs.challenge_id:</b> Esta é uma junção externa à esquerda (LEFT JOIN) com uma subconsulta (subquery) para calcular as somas das visualizações de desafios (total_views e total_unique_views). A subconsulta calcula essas somas agrupando por "challenge_id" e, em seguida, faz uma junção com base no "challenge_id".<br>
    <b>6. LEFT JOIN (...) AS ss ON ch.challenge_id = ss.challenge_id:</b> Aqui, fazemos outra junção externa à esquerda (LEFT JOIN) com outra subconsulta para calcular as somas das submissões de desafios (total_submissions e total_accepted_submissions). A subconsulta calcula essas somas agrupando por "challenge_id" e, em seguida, faz uma junção com base no "challenge_id".<br>
    <b>7. GROUP BY c.contest_id, c.hacker_id, c.name:</b> Estamos agrupando os resultados pelo ID do concurso (contest_id), ID do hacker (hacker_id) e nome do hacker (name). Isso é necessário porque estamos usando funções de agregação (SUM) nas colunas selecionadas.<br>
    <b>8. HAVING total_submissions_sum != 0 AND total_accepted_submissions_sum != 0 AND total_views_sum != 0 AND total_unique_views_sum != 0:</b> Com a cláusula HAVING, estamos filtrando os resultados após a agregação para excluir os concursos onde todas as quatro somas (total_submissions_sum, total_accepted_submissions_sum, total_views_sum e total_unique_views_sum) são iguais a zero.<br>
    <b>9. ORDER BY c.contest_id:</b> Por fim, estamos ordenando os resultados em ordem crescente com base no ID do concurso (contest_id).<br>
    <br>
    <i>Resumindo, o código realiza junções entre as tabelas "contests", "colleges" e "challenges" para obter as informações relevantes dos concursos, e em seguida, faz junções externas com subconsultas para calcular as somas das estatísticas de visualizações e submissões de desafios. Os resultados são filtrados para excluir concursos sem atividade relevante (todas as somas iguais a zero) e são ordenados em ordem crescente pelo ID do concurso.</i>
    </td>
  </tr>
    
  </table>

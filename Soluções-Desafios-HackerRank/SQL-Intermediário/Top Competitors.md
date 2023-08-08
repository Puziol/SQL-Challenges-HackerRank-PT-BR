  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/full-score/">Top Competitors</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.

The following tables contain contest data:

Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker. 

Difficulty: The difficult_level is the level of difficulty of the challenge, and score is the score of the challenge for the difficulty level. 

Challenges: The challenge_id is the id of the challenge, the hacker_id is the id of the hacker who created the challenge, and difficulty_level is the level of difficulty of the challenge. 

Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge that the submission belongs to, and score is the score of the submission.<br>
    </td>
    </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>O problema envolve dados de um concurso de codificação conduzido por Julia. O objetivo é criar um leaderboard (classificação) com os respectivos hacker_id (ID do hacker) e name (nome do hacker) dos hackers que alcançaram pontuação máxima (full score) em mais de um desafio. A classificação deve ser organizada em ordem decrescente pelo número total de desafios em que o hacker obteve a pontuação máxima. Se houver mais de um hacker com a mesma quantidade de desafios de pontuação máxima, eles devem ser ordenados em ordem crescente pelo hacker_id.

Aqui estão as tabelas envolvidas:

Tabela "Hackers": Contém informações sobre os hackers, incluindo hacker_id (ID do hacker) e name (nome do hacker).

Tabela "Difficulty": Contém informações sobre o nível de dificuldade dos desafios, incluindo difficulty_level (nível de dificuldade do desafio) e score (pontuação do desafio para o nível de dificuldade).

Tabela "Challenges": Contém informações sobre os desafios de codificação, incluindo challenge_id (ID do desafio), hacker_id (ID do hacker que criou o desafio) e difficulty_level (nível de dificuldade do desafio).

Tabela "Submissions": Contém informações sobre as submissões dos hackers para os desafios, incluindo submission_id (ID da submissão), hacker_id (ID do hacker que fez a submissão), challenge_id (ID do desafio ao qual a submissão pertence) e score (pontuação da submissão).

Em resumo, o problema solicita que você escreva uma consulta SQL para calcular os resultados do leaderboard. Você precisa encontrar os hackers que alcançaram pontuação máxima em mais de um desafio, calcular o número total de desafios em que eles obtiveram pontuação máxima e classificar os hackers em ordem decrescente com base nesse número de desafios. Se houver empates na quantidade de desafios de pontuação máxima, ordene os hackers em ordem crescente pelo hacker_id.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT DISTINCT h.hacker_id, h.name
  FROM hackers AS h
  INNER JOIN submissions AS s ON h.hacker_id = s.hacker_id
  INNER JOIN challenges AS c ON s.challenge_id = c.challenge_id
  INNER JOIN difficulty AS d ON c.difficulty_level = d.difficulty_level
  WHERE s.score = d.score
    AND c.difficulty_level = d.difficulty_level
  GROUP BY h.hacker_id, h.name
  HAVING COUNT(s.hacker_id) > 1
  ORDER BY COUNT(s.hacker_id) DESC, h.hacker_id ASC;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT DISTINCT h.hacker_id, h.name:</b> Nesta linha, estamos selecionando as colunas "hacker_id" (ID do hacker) e "name" (nome do hacker) da tabela "hackers". O uso de "DISTINCT" garante que os resultados sejam únicos, ou seja, não haverá duplicatas no resultado final.<br>
    <b>2. FROM hackers AS h:</b> Aqui, estamos selecionando a tabela "hackers" e atribuindo um alias "h" a ela. O alias "h" será usado como uma forma mais curta de se referir à tabela "hackers" nas outras partes da consulta.<br>
    <b>3. INNER JOIN submissions AS s ON h.hacker_id = s.hacker_id:</b> Nesta linha, estamos fazendo uma junção interna (INNER JOIN) entre as tabelas "hackers" (com o alias "h") e "submissions" (com o alias "s") usando a coluna "hacker_id" como chave de junção. Isso combina os registros das duas tabelas com base no ID do hacker.<br>
    <b>4. INNER JOIN challenges AS c ON s.challenge_id = c.challenge_id:</b> Aqui, estamos fazendo outra junção interna entre as tabelas "submissions" (com o alias "s") e "challenges" (com o alias "c") usando a coluna "challenge_id" como chave de junção. Isso combina os registros das tabelas "submissions" e "challenges" com base no ID do desafio.<br>
    <b>5. INNER JOIN difficulty AS d ON c.difficulty_level = d.difficulty_level:</b> Nesta linha, estamos fazendo mais uma junção interna entre as tabelas "challenges" (com o alias "c") e "difficulty" (com o alias "d") usando a coluna "difficulty_level" como chave de junção. Isso combina os registros das tabelas "challenges" e "difficulty" com base no nível de dificuldade do desafio.<br>
    <b>6. WHERE s.score = d.score AND c.difficulty_level = d.difficulty_level:</b> A cláusula WHERE é usada para filtrar os resultados da junção, mantendo apenas os registros onde a pontuação da submissão (s.score) é igual à pontuação do nível de dificuldade do desafio (d.score) e onde o nível de dificuldade do desafio (c.difficulty_level) é igual ao nível de dificuldade do nível de dificuldade (d.difficulty_level).<br>
    <b>7. GROUP BY h.hacker_id, h.name:</b> Estamos agrupando os resultados pelo ID do hacker (h.hacker_id) e pelo nome do hacker (h.name). Isso é necessário porque estamos usando funções de agregação (COUNT) nas colunas selecionadas.<br>
    <b>8. HAVING COUNT(s.hacker_id) > 1:</b> Com a cláusula HAVING, estamos filtrando os resultados após a agregação para incluir apenas os hackers que têm mais de uma submissão com pontuação máxima.<br>
    <b>9. ORDER BY COUNT(s.hacker_id) DESC, h.hacker_id ASC:</b> Por fim, estamos ordenando os resultados em ordem decrescente pelo número de submissões com pontuação máxima (COUNT(s.hacker_id)) e em ordem crescente pelo ID do hacker (h.hacker_id).<br>
    <br>
    <i>Resumindo, o código realiza várias junções entre as tabelas "hackers", "submissions", "challenges" e "difficulty" para obter as informações relevantes dos hackers e desafios. Em seguida, ele filtra os resultados para incluir apenas os hackers que têm mais de uma submissão com pontuação máxima e os ordena de acordo com o número de submissões com pontuação máxima.</i>
    </td>
  </tr>
    
  </table>

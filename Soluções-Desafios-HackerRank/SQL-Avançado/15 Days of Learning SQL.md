  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/15-days-of-learning-sql/">15 Days of Learning SQL</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Julia conducted a 15 days of learning SQL contest. The start date of the contest was March 01, 2016 and the end date was March 15, 2016.

Write a query to print total number of unique hackers who made at least 1 submission each day (starting on the first day of the contest), and find the hacker_id and name of the hacker who made maximum number of submissions each day. If more than one such hacker has a maximum number of submissions, print the lowest hacker_id. The query should print this information for each day of the contest, sorted by the date.

The following tables hold contest data:

Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.

Submissions: The submission_date is the date of the submission, submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, and score is the score of the submission. 
<br>
    </td>
    </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Julia conduziu um concurso de aprendizado de SQL com duração de 15 dias. O concurso começou em 01 de março de 2016 e terminou em 15 de março de 2016.

O objetivo é escrever uma consulta SQL para imprimir o número total de hackers únicos que fizeram pelo menos 1 submissão em cada dia do concurso (a partir do primeiro dia do concurso). Além disso, devemos encontrar o hacker_id e o nome do hacker que fez o maior número de submissões em cada dia do concurso. Se mais de um hacker tiver o mesmo número máximo de submissões, devemos imprimir o hacker_id mais baixo. A consulta deve imprimir essas informações para cada dia do concurso, ordenadas pela data.

As tabelas envolvidas no problema são:

Tabela "Hackers": Contém informações sobre os hackers, incluindo o hacker_id (ID do hacker) e o nome (name) do hacker.

Tabela "Submissions": Contém informações sobre as submissões, incluindo a submission_date (data da submissão), submission_id (ID da submissão), hacker_id (ID do hacker que fez a submissão) e score (pontuação da submissão).

Resumindo, precisamos encontrar o número total de hackers únicos que fizeram pelo menos 1 submissão em cada dia do concurso, bem como o hacker que fez o maior número de submissões em cada dia, considerando o hacker_id mais baixo em caso de empate. Tudo isso deve ser apresentado ordenado pela data do concurso.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
SELECT 
    submission_date,
    (
        SELECT COUNT(DISTINCT hacker_id)
        FROM submissions AS s2
        WHERE s1.submission_date = s2.submission_date
        AND (
            SELECT COUNT(DISTINCT s3.submission_date)
            FROM submissions AS s3
            WHERE s2.hacker_id = s3.hacker_id
            AND s1.submission_date > s3.submission_date
        ) = DATEDIFF(s1.submission_date, '2016-03-01')
    ) AS num_hackers_same_day,
    (
        SELECT hacker_id
        FROM submissions AS s2
        WHERE s1.submission_date = s2.submission_date
        GROUP BY hacker_id
        ORDER BY COUNT(submission_id) DESC, hacker_id
        LIMIT 1
    ) AS top_hacker_id,
    (
        SELECT name
        FROM hackers
        WHERE hacker_id = top_hacker_id
    ) AS top_hacker_name
FROM (
    SELECT DISTINCT submission_date
    FROM submissions
) AS s1
GROUP BY submission_date;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT submission_date:</b> Nesta linha, estamos selecionando a coluna "submission_date" da tabela de submissões (submissions).<br>
    <b>2. (SELECT COUNT(DISTINCT hacker_id) FROM submissions AS s2 WHERE s1.submission_date = s2.submission_date AND (SELECT COUNT(DISTINCT s3.submission_date) FROM submissions AS s3 WHERE s2.hacker_id = s3.hacker_id AND s1.submission_date > s3.submission_date) = DATEDIFF(s1.submission_date, '2016-03-01')) AS num_hackers_same_day:</b> Aqui, estamos usando uma subconsulta (subquery) para calcular o número de hackers que tiveram submissões na mesma data (submission_date) em que o resultado da submissão foi igual ao número de dias entre essa data e '2016-03-01' (DATEDIFF(s1.submission_date, '2016-03-01')). A subconsulta compara a data de submissão com as datas de outras submissões do mesmo hacker (usando as tabelas "s2" e "s3") e usa COUNT(DISTINCT hacker_id) para contar o número de hackers únicos que atendem a essas condições.<br>
    <b>3. (SELECT hacker_id FROM submissions AS s2 WHERE s1.submission_date = s2.submission_date GROUP BY hacker_id ORDER BY COUNT(submission_id) DESC, hacker_id LIMIT 1) AS top_hacker_id:</b> Nesta linha, estamos usando outra subconsulta para encontrar o hacker_id do hacker que teve o maior número de submissões em uma determinada data (submission_date). A subconsulta agrupa as submissões pela coluna hacker_id (GROUP BY hacker_id), conta o número de submissões para cada hacker (COUNT(submission_id)) e, em seguida, classifica os resultados em ordem decrescente (DESC) com base no número de submissões e em ordem crescente pelo hacker_id (ORDER BY COUNT(submission_id) DESC, hacker_id). O LIMIT 1 é usado para selecionar apenas o hacker_id do hacker com o maior número de submissões.<br>
    <b>4. (SELECT name FROM hackers WHERE hacker_id = top_hacker_id) AS top_hacker_name:</b> Aqui, estamos usando outra subconsulta para obter o nome (name) do hacker com o ID (hacker_id) obtido na subconsulta anterior. Isso é feito usando o hacker_id na tabela hackers para localizar o nome correspondente.<br>
    <b>5. FROM (SELECT DISTINCT submission_date FROM submissions) AS s1:</b> Nesta parte, estamos criando uma tabela temporária (com o alias "s1") que contém todas as datas de submissão distintas (sem repetições) encontradas na tabela submissions.<br>
    <b>6. GROUP BY submission_date:</b> Estamos agrupando os resultados pelo campo submission_date. Isso é necessário porque estamos usando funções de agregação (COUNT) nas subconsultas anteriores.<br>
    <br>
    <i>Resumindo, o código realiza várias subconsultas para calcular as estatísticas relacionadas às submissões em determinadas datas (submission_date). Ele conta o número de hackers que tiveram submissões na mesma data com pontuação igual ao número de dias entre a data e '2016-03-01' e também encontra o hacker com o maior número de submissões em cada data. O resultado final inclui a data de submissão, o número de hackers com o mesmo número de dias desde '2016-03-01', o ID do hacker com o maior número de submissões e o nome do hacker correspondente.</i>
    </td>
  </tr>
    
  </table>

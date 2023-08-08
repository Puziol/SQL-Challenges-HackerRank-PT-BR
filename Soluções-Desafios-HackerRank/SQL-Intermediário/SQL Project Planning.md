  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/sql-projects/">SQL Project Planning</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!

The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of 0 from your result.<br>
    </td>
    </tr>

  <tr>
      <th colspan="2">PROJECTS</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">Task_ID</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">Start_Date</td>
      <td width="50%" align="center">Date</td>
  </tr>

  <tr>
      <td width="50%" align="center">End_Date</td>
      <td width="50%" align="center">Date</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>O problema se refere a uma tabela chamada "Projects", que contém três colunas: Task_ID (ID da tarefa), Start_Date (Data de início) e End_Date (Data de término). É garantido que a diferença entre a End_Date e a Start_Date é igual a 1 dia para cada linha na tabela.

O objetivo é encontrar o número total de projetos diferentes completados. Um projeto é considerado concluído se as datas de término (End_Date) das tarefas são consecutivas, ou seja, uma após a outra, sem lacunas. Por exemplo, se as tarefas tiverem as datas de término 2023-08-01, 2023-08-02 e 2023-08-03, elas pertencem ao mesmo projeto.

A consulta SQL deve retornar as datas de início e término dos projetos, listados em ordem crescente pelo número de dias que levaram para serem concluídos. Se houver mais de um projeto com o mesmo número de dias de conclusão, então a ordenação deve ser feita com base na data de início do projeto.

Em resumo, a consulta deve encontrar e listar os projetos concluídos, ordenando-os pelo número de dias que levaram para serem concluídos e, em caso de empate, ordenando-os pela data de início.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT Start_Date, MIN(End_Date) FROM
  (SELECT Start_Date FROM Projects WHERE Start_Date NOT IN (SELECT End_Date FROM Projects)) AS start,
  (SELECT End_Date FROM Projects WHERE End_Date NOT IN (SELECT Start_Date FROM Projects)) AS end
  WHERE Start_Date < End_Date
  GROUP BY Start_Date
  ORDER BY DATEDIFF(MIN(End_Date), Start_Date), Start_Date;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT Start_Date FROM Projects WHERE Start_Date NOT IN (SELECT End_Date FROM Projects)) AS start:</b> Nesta linha, estamos fazendo uma subconsulta (subquery) para selecionar a coluna "Start_Date" da tabela "Projects" onde a data de início (Start_Date) não está presente na coluna "End_Date" da mesma tabela. Essa subconsulta é renomeada como "start".<br>
    <b>2. SELECT End_Date FROM Projects WHERE End_Date NOT IN (SELECT Start_Date FROM Projects)) AS end:</b> Nesta linha, estamos fazendo outra subconsulta para selecionar a coluna "End_Date" da tabela "Projects" onde a data de término (End_Date) não está presente na coluna "Start_Date" da mesma tabela. Essa subconsulta é renomeada como "end".<br>
    <b>3. WHERE Start_Date < End_Date:</b> Essa cláusula é usada para filtrar os resultados das subconsultas "start" e "end", garantindo que somente os registros com datas de início (Start_Date) antes das datas de término (End_Date) sejam considerados.<br>
    <b>4. GROUP BY Start_Date:</b> Estamos agrupando os resultados pelo campo "Start_Date". Isso é necessário para calcular a diferença em dias entre a data de término mais próxima e a data de início de cada projeto.<br>
    <b>5. ORDER BY DATEDIFF(MIN(End_Date), Start_Date), Start_Date:</b> Aqui, estamos ordenando os resultados com base em duas condições. Primeiro, estamos usando a função DATEDIFF para calcular a diferença em dias entre a data de término mais próxima (MIN(End_Date)) e a data de início (Start_Date) do projeto. Ordenamos os projetos com base nessa diferença em dias em ordem crescente. Em caso de empate na diferença em dias, ordenamos os projetos pela data de início (Start_Date) em ordem crescente também.<br>
    </td>
  </tr>
    
  </table>

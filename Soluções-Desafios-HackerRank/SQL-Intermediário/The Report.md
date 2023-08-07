  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/the-report/">The Report</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.

Grades contains the following data:  
Grade, Min_Mark and Max_Mark  
1, 0, 9  
2, 10, 19  
3, 20, 29  
4, 30, 39  
5, 40, 49  
6, 50, 59  
7, 60, 69  
8, 70, 79  
9, 80, 89  
10, 90, 100  



Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.

Write a query to help Eve.<br>
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
      <td width="50%" align="center">Marks</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Você possui duas tabelas: Students (Estudantes) e Grades (Notas). A tabela Students contém três colunas: ID, Name (Nome) e Marks (Pontuação).

A tabela Grades contém os seguintes dados (csv):  
Grade (Nota), Min_Mark (Pontuação Mínima) e Max_Mark (Pontuação Máxima)  
1, 0, 9  
2, 10, 19  
3, 20, 29  
4, 30, 39  
5, 40, 49  
6, 50, 59  
7, 60, 69  
8, 70, 79  
9, 80, 89  
10, 90, 100  

Ketty dá a Eve a tarefa de gerar um relatório contendo três colunas: Name (Nome), Grade (Nota) e Mark (Pontuação). Ketty não quer os NOMES daqueles alunos que receberam uma nota menor que 8. O relatório deve estar em ordem decrescente por nota - ou seja, notas mais altas são listadas primeiro. Se houver mais de um aluno com a mesma nota (8-10), ordene esses alunos pelo nome em ordem alfabética. Finalmente, se a nota for menor que 8, use "NULL" como nome e liste-os por suas notas em ordem decrescente. Se houver mais de um aluno com a mesma nota (1-7), ordene esses alunos por suas pontuações em ordem crescente.

Você precisa escrever uma consulta SQL para ajudar Eve a gerar o relatório</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>A solução envolve o uso de cláusulas SQL como CASE, JOIN e ORDER BY para realizar as etapas necessárias e atender aos requisitos do problema.
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT 
      IF(Grade < 8, NULL, Name) AS Name,
      Grade,
      Marks
  FROM Students
  LEFT JOIN Grades ON Marks BETWEEN Min_Mark AND Max_Mark
  ORDER BY Grade DESC, IF(Grade >= 8, Name, NULL), Marks;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    1. A cláusula SELECT é usada para selecionar as colunas Name (possivelmente com "NULL"), Grade e Marks.<br>
    2. Usamos a função IF para determinar o valor da coluna Name com base nas seguintes condições:  
Se a nota (Grade) for menor que 8, usamos "NULL" como o nome.  
Se a nota for 8 ou superior, usamos o nome real do estudante.<br>
    3. Estamos realizando um LEFT JOIN entre as tabelas Students e Grades usando a condição de que a Marks (Pontuação) do aluno esteja entre Min_Mark e Max_Mark da tabela Grades.<br>
    4. A cláusula ORDER BY é usada para ordenar os resultados:  
Primeiro, os resultados são ordenados por Grade (Nota) em ordem decrescente.  
Se a nota for 8 ou superior, os nomes são ordenados alfabeticamente em ordem crescente.  
Se a nota for menor que 8, os resultados são ordenados por Marks (Pontuação) em ordem crescente.<br>
    <br>
    <i>Essa consulta irá gerar um relatório com as colunas Name, Grade e Mark, atendendo a todos os requisitos especificados no problema.</i>
    </td>
  </tr>
    
  </table>

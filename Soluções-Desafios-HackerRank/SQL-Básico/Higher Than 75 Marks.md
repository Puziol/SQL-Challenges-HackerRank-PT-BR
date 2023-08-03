  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/more-than-75-marks/">Higher Than 75 Marks</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Query the Name of any student in STUDENTS who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID. The Name column only contains uppercase (A-Z) and lowercase (a-z) letters.

The STUDENTS table is described as follows:<br>
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
      <td colspan="2"  align="center"><b>Problema:</b><br>Consulte o nome de qualquer aluno na tabela STUDENTS que obteve mais de 75 pontos. Ordene a saída pelos últimos três caracteres de cada nome. Se dois ou mais alunos tiverem nomes que terminam nos mesmos últimos três caracteres (ou seja, Bobby, Robby, etc.), ordene-os secundariamente pelo ID crescente. A coluna Name contém apenas letras maiúsculas (A-Z) e minúsculas (a-z).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela STUDENTS:</b><br>A tabela STUDENTS contém informações sobre vários alunos. Ela possui várias colunas, como ID do Aluno, Nome (Name), Pontuação (Marks) e outras informações relevantes.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos consultar o nome de qualquer aluno na tabela STUDENTS que obteve mais de 75 pontos. Em seguida, ordenamos a saída pelos últimos três caracteres de cada nome e, em caso de empate, pelo ID crescente.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT Name
  FROM STUDENTS
  WHERE Marks > 75
  ORDER BY RIGHT(Name, 3), ID;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT Name:</b> Isso indica que queremos selecionar o nome dos alunos da tabela STUDENTS.<br>
    <b>2. FROM STUDENTS:</b> Indica a tabela de onde queremos obter os dados, que é a tabela STUDENTS.<br>
    <b>3. WHERE Marks > 75:</b> O WHERE é uma cláusula que filtra os resultados com base em condições específicas. Aqui, estamos filtrando os alunos que obtiveram mais de 75 pontos.<br>
    <b>4. ORDER BY RIGHT(Name, 3), ID:</b> O ORDER BY é usado para ordenar os resultados. Estamos ordenando primeiro pelos últimos três caracteres de cada nome (usando a função RIGHT(Name, 3)) e, em caso de empate, pelo ID crescente.<br>
    <br>
    <i>A consulta retornará os nomes dos alunos que obtiveram mais de 75 pontos, ordenados pelos últimos três caracteres de cada nome e pelo ID crescente em caso de empate. Isso fornecerá o resultado solicitado no problema.
    </i>
    </td>
  </tr>
    
  </table>

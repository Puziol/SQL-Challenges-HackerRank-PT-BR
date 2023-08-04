  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/earnings-of-employees/">Top Earners</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">We define an employee's total earnings to be their monthly salary x months worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as 2 space-separated integers.  
      Where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is the their monthly salary.

The Employee table containing employee data for a company is described as follows:<br>
    </td>
  </tr>
    
  <tr>
      <th colspan="2">Employee</th>
  </tr>
    
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">employee_id</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">name</td>
      <td width="50%" align="center">String</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">months</td>
      <td width="50%" align="center">Integer</td>
  </tr>

  <tr>
      <td width="50%" align="center">salary</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Definimos os ganhos totais de um funcionário como o salário mensal multiplicado pelo número de meses trabalhados e o ganho total máximo como o maior ganho total de qualquer funcionário na tabela Employee. Escreva uma consulta para encontrar o ganho total máximo para todos os funcionários, bem como o número total de funcionários que têm ganho total máximo. Em seguida, imprima esses valores como dois inteiros separados por espaço.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela Employee:</b><br>A tabela Employee contém informações sobre vários funcionários. Ela possui várias colunas, como ID do Funcionário (employee_id), Nome (name), Meses de Trabalho (months) e Salário (salary).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos encontrar o ganho total máximo entre todos os funcionários e contar quantos funcionários têm esse ganho total máximo.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT MAX(months * salary) AS earnings, COUNT(*) AS employee_count
  FROM Employee
  WHERE months * salary = (SELECT MAX(months * salary) FROM Employee);
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT MAX(months * salary) AS earnings, COUNT(*) AS employee_count:</b> Isso calcula o ganho total máximo entre todos os funcionários (meses * salário) e, ao mesmo tempo, conta quantos funcionários têm esse ganho total máximo.<br>
    <b>2. FROM Employee:</b> Indica a tabela de onde queremos obter os dados, que é a tabela Employee.</b><br>
    <b>3. WHERE months * salary = (SELECT MAX(months * salary) FROM Employee):</b> O WHERE filtra os resultados para incluir apenas os funcionários cujo ganho total (meses * salário) é igual ao ganho total máximo encontrado usando uma subconsulta.<br>
    <b>3. ORDER BY employee_id ASC:</b> O ORDER BY é usado para ordenar os resultados. Aqui, estamos ordenando os resultados pelo employee_id em ordem crescente (ASC significa ascendente).<br>
    <br>
    <i>A consulta retornará o ganho total máximo entre todos os funcionários e o número total de funcionários que têm esse ganho total máximo. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

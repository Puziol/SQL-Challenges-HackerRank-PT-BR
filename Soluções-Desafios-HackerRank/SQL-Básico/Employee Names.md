  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/name-of-employees/">Employee Names</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order. Where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is their monthly salary.

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
      <td colspan="2"  align="center"><b>Problema:</b><br>Escreva uma consulta que imprima uma lista de nomes de funcionários (ou seja, o atributo name) da tabela Employee em ordem alfabética. Onde employee_id é o número de ID do funcionário, name é o nome dele, months é o total de meses que ele trabalhou na empresa e salary é o salário mensal dele.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela Employee:</b><br>A tabela Employee contém informações sobre vários funcionários. Ela possui várias colunas, como ID do Funcionário (employee_id), Nome (name), Meses de Trabalho (months) e Salário (salary).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos consultar os nomes dos funcionários da tabela Employee e ordená-los em ordem alfabética.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT name
  FROM Employee
  ORDER BY name;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT name:</b> Isso indica que queremos selecionar o atributo "name" da tabela Employee.<br>
    <b>2. FROM Employee:</b> Indica a tabela de onde queremos obter os dados, que é a tabela Employee.<br>
    <b>3. ORDER BY name:</b> O ORDER BY é usado para ordenar os resultados. Aqui, estamos ordenando os nomes dos funcionários em ordem alfabética.<br>
    <br>
    <i>A consulta retornará uma lista de nomes de funcionários da tabela Employee, ordenados em ordem alfabética. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

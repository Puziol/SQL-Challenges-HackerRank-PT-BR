  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/the-blunder/">The Blunder</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's 0 key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.

Write a query calculating the amount of error (i.e.: actual - miscalculated average monthly salaries), and round it up to the next integer.  
Constraints  
1000 < Salary < 10^5

The EMPLOYEES table is described as follows:<br>
    </td>
  </tr>
    
  <tr>
      <th colspan="2">EMPLOYEES</th>
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
      <td width="50%" align="center">Salary</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Samantha foi encarregada de calcular os salários médios mensais de todos os funcionários na tabela EMPLOYEES, mas não percebeu que a tecla 0 do seu teclado estava quebrada até depois de completar o cálculo. Ela quer a sua ajuda para encontrar a diferença entre o erro de cálculo dela (usando salários com quaisquer zeros removidos) e o salário médio real.

Escreva uma consulta que calcule a quantidade de erro (ou seja, real - salário médio calculado incorretamente) e arredonde para o próximo número inteiro.

Restrições:
1000 < Salário < 10^5.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela Employee:</b><br>A tabela EMPLOYEES contém informações sobre vários funcionários. Ela possui várias colunas, como ID do Funcionário (ID), Nome do Funcionário (NAME), Salário Mensal (SALARY) e outros campos.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos calcular o erro de cálculo de Samantha, que é a diferença entre o salário médio real e o salário médio que ela calculou incorretamente após remover os zeros dos salários.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT CEIL(AVG(SALARY) - AVG(REPLACE(SALARY, '0', '')))
  FROM EMPLOYEES;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT CEIL(AVG(SALARY) - AVG(REPLACE(SALARY, '0', ''))):</b> Isso calcula o erro de cálculo de Samantha da seguinte maneira:<br> 
    AVG(SALARY): Calcula o salário médio real.<br>
    AVG(REPLACE(SALARY, '0', '')): Calcula o salário médio incorretamente, removendo os zeros dos salários antes de calcular a média.  
    A diferença entre esses dois valores é o erro de cálculo.<br>
    CEIL(...): Arredonda o resultado para o próximo número inteiro.<br>
    <b>2. FROM EMPLOYEES:</b> Indica a tabela de onde queremos obter os dados, que é a tabela EMPLOYEES.<br>
    <br>
    <i>A consulta retornará a quantidade de erro de cálculo de Samantha, arredondada para o próximo número inteiro. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

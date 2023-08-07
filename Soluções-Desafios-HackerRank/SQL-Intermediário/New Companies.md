  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/the-company/">New Companies</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Amber's conglomerate corporation just acquired some new companies. Each of the companies follows this hierarchy: Founder > Lead Manager > Senior Manager > Manager > Employee  

Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code. Note: The tables may contain duplicate records. The company_code is string, so the sorting should not be numeric. For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.

The following tables contain company data:

Company: The company_code is the code of the company and founder is the founder of the company. 

Lead_Manager: The lead_manager_code is the code of the lead manager, and the company_code is the code of the working company. 

Senior_Manager: The senior_manager_code is the code of the senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company. 

Manager: The manager_code is the code of the manager, the senior_manager_code is the code of its senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company. 

Employee: The employee_code is the code of the employee, the manager_code is the code of its manager, the senior_manager_code is the code of its senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company. <br>
    </td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Amber's conglomerate corporation adquiriu algumas novas empresas. Cada uma das empresas segue esta hierarquia: Fundador > Gerente Líder > Gerente Sênior > Gerente > Funcionário. Dadas as tabelas abaixo, escreva uma consulta para imprimir o código da empresa, o nome do fundador, o número total de gerentes líderes, o número total de gerentes sêniores, o número total de gerentes e o número total de funcionários. Ordene a saída pelo código da empresa em ordem ascendente. Observação: As tabelas podem conter registros duplicados. O código da empresa é uma string, portanto, a ordenação não deve ser numérica.

Tabelas:

Company: O company_code é o código da empresa e founder é o fundador da empresa.  
Lead_Manager: O lead_manager_code é o código do gerente líder, e o company_code é o código da empresa em que trabalha.  
Senior_Manager: O senior_manager_code é o código do gerente sênior, o lead_manager_code é o código do seu gerente líder, e o company_code é o código da empresa em que trabalha.  
Manager: O manager_code é o código do gerente, o senior_manager_code é o código do seu gerente sênior, o lead_manager_code é o código do seu gerente líder, e o company_code é o código da empresa em que trabalha.  
Employee: O employee_code é o código do funcionário, o manager_code é o código do seu gerente, o senior_manager_code é o código do seu gerente sênior, o lead_manager_code é o código do seu gerente líder, e o company_code é o código da empresa em que trabalha.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos realizar junções entre as tabelas Company, Lead_Manager, Senior_Manager, Manager e Employee para calcular o total de funcionários em cada nível hierárquico e o nome do fundador da empresa. Em seguida, agrupamos os resultados pelo código da empresa (company_code) e contamos o número de registros em cada nível.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT C.company_code, C.founder,
         COUNT(DISTINCT L.lead_manager_code) AS num_lead_managers,
         COUNT(DISTINCT S.senior_manager_code) AS num_senior_managers,
         COUNT(DISTINCT M.manager_code) AS num_managers,
         COUNT(DISTINCT E.employee_code) AS num_employees
  FROM Company C
  LEFT JOIN Lead_Manager L ON C.company_code = L.company_code
  LEFT JOIN Senior_Manager S ON L.lead_manager_code = S.lead_manager_code
  LEFT JOIN Manager M ON S.senior_manager_code = M.senior_manager_code
  LEFT JOIN Employee E ON M.manager_code = E.manager_code
  GROUP BY C.company_code, C.founder
  ORDER BY C.company_code;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    1. Fazemos uma consulta a partir da tabela Company (C), que contém o código da empresa e o nome do fundador.<br>
    2. Usamos junções LEFT JOIN com as tabelas Lead_Manager (L), Senior_Manager (S), Manager (M) e Employee (E) para combinar os dados de cada nível hierárquico, usando as chaves correspondentes (ex: L.lead_manager_code = S.lead_manager_code).<br>
    3. Usamos a função COUNT(DISTINCT ...) para contar o número de ocorrências únicas de cada código (gerente líder, gerente sênior, gerente e funcionário) em cada nível.<br>
    4. Agrupamos os resultados pelo código da empresa (company_code) e pelo fundador (founder).<br>
    5. Usamos a cláusula ORDER BY para ordenar os resultados pelo código da empresa em ordem ascendente.<br>
    <br>
    <i>A consulta retornará os detalhes das empresas, incluindo o nome do fundador e o número total de gerentes líderes, gerentes sêniores, gerentes e funcionários em cada empresa, ordenados pelo código da empresa. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

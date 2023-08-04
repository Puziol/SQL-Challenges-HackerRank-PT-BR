  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/what-type-of-triangle/">Type of Triangle</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with 3 sides of equal length.  
Isosceles: It's a triangle with 2 sides of equal length.  
Scalene: It's a triangle with 3 sides of differing lengths.  
Not A Triangle: The given values of A, B, and C don't form a triangle.  
Each row in the table denotes the lengths of each of a triangle's three sides.  

The TRIANGLES table is described as follows:<br>
    </td>
  </tr>
    
  <tr>
      <th colspan="2">TRIANGLES</th>
  </tr>
    
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">A</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">B</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">C</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Escreva uma consulta que identifica o tipo de cada registro na tabela TRIANGLES usando os comprimentos dos três lados do triângulo. Imprima uma das seguintes declarações para cada registro na tabela:
      Equilátero: É um triângulo com 3 lados de comprimento igual.
      Isósceles: É um triângulo com 2 lados de comprimento igual.
      Escaleno: É um triângulo com 3 lados de comprimento diferentes.
      Não é um Triângulo: Os valores dados de A, B e C não formam um triângulo.
      Cada linha na tabela denota os comprimentos de cada um dos três lados de um triângulo.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Descrição da tabela TRIANGLES:</b><br>A tabela TRIANGLES contém informações sobre vários triângulos. Ela possui várias colunas, como A, B e C, que representam os comprimentos dos três lados de cada triângulo.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver esse problema, precisamos identificar o tipo de triângulo com base nos comprimentos de seus três lados. Podemos usar a lógica para determinar o tipo de triângulo, comparando os comprimentos dos lados usando declarações condicionais (CASE WHEN).</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT
      CASE
          WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle'
          WHEN A = B AND B = C THEN 'Equilateral'
          WHEN A = B OR B = C OR A = C THEN 'Isosceles'
          ELSE 'Scalene'
      END AS TYPE
  FROM TRIANGLES;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT:</b> Isso indica que queremos selecionar um conjunto de resultados.<br>
    <b>2. CASE WHEN:</b> É uma expressão condicional que nos permite avaliar condições e retornar um valor específico com base no resultado dessa avaliação.<br>
    <b>3. WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle':</b> Aqui, estamos verificando se as somas de dois lados são menores ou iguais ao terceiro lado. Se essa condição for verdadeira, o triângulo não pode ser formado e retornamos 'Not A Triangle'.<br>
    <b>4. WHEN A = B AND B = C THEN 'Equilateral':</b> Estamos verificando se todos os lados têm comprimentos iguais. Se essa condição for verdadeira, retornamos 'Equilateral'.<br>
    <b>5. WHEN A = B OR B = C OR A = C THEN 'Isosceles':</b> Estamos verificando se pelo menos dois lados têm comprimentos iguais. Se essa condição for verdadeira, retornamos 'Isosceles'.<br>
    <b>6. ELSE 'Scalene':</b> Se nenhuma das condições acima for verdadeira, então o triângulo deve ter três lados com comprimentos diferentes, e retornamos 'Scalene'.<br>
    <b>7. AS TYPE:</b> É um rótulo para a coluna resultante que identifica o tipo de triângulo.<br>
    <b>8. FROM TRIANGLES:</b> Indica a tabela de onde queremos obter os dados, que é a tabela TRIANGLES.<br>
    <br>
    <i>A consulta retornará o tipo de triângulo para cada registro na tabela TRIANGLES com base nos comprimentos dos seus três lados, seguindo as condições estabelecidas. Isso fornecerá o resultado solicitado no problema.</i>
    </td>
  </tr>
    
  </table>

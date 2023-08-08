  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/symmetric-pairs/">Symmetric Pairs</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">You are given a table, Functions, containing two columns: X and Y.

Two pairs (X1, Y1) and (X2, Y2) are said to be symmetric pairs if X1 = Y2 and X2 = Y1.

Write a query to output all such symmetric pairs in ascending order by the value of X. List the rows such that X1 ≤ Y1.<br>
    </td>
    </tr>

  <tr>
      <th colspan="2">FUNCTIONS</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">X</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">Y</td>
      <td width="50%" align="center">Integer</td>
  </tr>

  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>O problema apresenta uma tabela chamada "Functions", que contém duas colunas: X e Y.

Dois pares (X1, Y1) e (X2, Y2) são considerados pares simétricos se satisfizerem as seguintes condições:

X1 é igual a Y2.
X2 é igual a Y1.
O objetivo é escrever uma consulta SQL para listar todos os pares simétricos na tabela "Functions" em ordem crescente com base no valor de X. Além disso, a consulta deve listar apenas os pares em que X1 é menor ou igual a Y1.

Em resumo, a consulta SQL deve identificar os pares simétricos na tabela e exibi-los em ordem crescente com base no valor de X, desde que X1 seja menor ou igual a Y1.
</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT X, Y FROM FUNCTIONS FUNCAO_1 
      WHERE EXISTS(SELECT * FROM FUNCTIONS FUNCAO_2 WHERE FUNCAO_2.Y=FUNCAO_1.X 
      AND FUNCAO_2.X=FUNCAO_1.Y AND FUNCAO_2.X>FUNCAO_1.X) AND (X!=Y) 
  UNION 
  SELECT X, Y FROM FUNCTIONS FUNCAO_1 WHERE X=Y AND 
      ((SELECT COUNT(*) FROM FUNCTIONS WHERE X=FUNCAO_1.X AND Y=FUNCAO_1.X)>1)    
          ORDER BY X;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT X, Y FROM FUNCTIONS FUNCAO_1:</b> Nesta linha, estamos selecionando as colunas "X" e "Y" da tabela "FUNCTIONS" e atribuindo um alias "FUNCAO_1" à tabela. O alias "FUNCAO_1" será usado como uma forma mais curta de se referir à tabela "FUNCTIONS" nas outras partes da consulta.<br>
    <b>2. WHERE EXISTS(SELECT * FROM FUNCTIONS FUNCAO_2 WHERE FUNCAO_2.Y = FUNCAO_1.X AND FUNCAO_2.X = FUNCAO_1.Y AND FUNCAO_2.X > FUNCAO_1.X) AND (X != Y):</b> Nesta cláusula WHERE, estamos usando a subconsulta (subquery) "SELECT * FROM FUNCTIONS FUNCAO_2" para verificar se existe pelo menos uma linha na tabela "FUNCTIONS" (com o alias "FUNCAO_2") que satisfaça as condições "FUNCAO_2.Y = FUNCAO_1.X" e "FUNCAO_2.X = FUNCAO_1.Y" e "FUNCAO_2.X > FUNCAO_1.X". Isso garante que existam duas linhas na tabela "FUNCTIONS" com os valores correspondentes para formar um par simétrico. A segunda condição "AND (X != Y)" é usada para excluir pares onde "X" é igual a "Y", pois queremos listar apenas os pares simétricos com valores distintos.<br>
    <b>3. UNION:</b> A cláusula UNION é usada para combinar os resultados de duas consultas. A próxima parte do código irá gerar outra consulta e os resultados das duas consultas serão combinados.<br>
    <b>4. SELECT X, Y FROM FUNCTIONS FUNCAO_1 WHERE X = Y AND ((SELECT COUNT(*) FROM FUNCTIONS WHERE X = FUNCAO_1.X AND Y = FUNCAO_1.X) > 1):</b> Nesta parte, estamos selecionando as colunas "X" e "Y" da tabela "FUNCTIONS" (com o alias "FUNCAO_1"). Aqui, estamos procurando pares onde "X" é igual a "Y" e, em seguida, usamos uma subconsulta para contar quantas linhas existem na tabela "FUNCTIONS" com os mesmos valores para "X" e "Y". A condição "((SELECT COUNT(*) FROM FUNCTIONS WHERE X = FUNCAO_1.X AND Y = FUNCAO_1.X) > 1)" garante que existam pelo menos duas linhas com os mesmos valores de "X" e "Y", formando um par simétrico.<br>
    <b>5. ORDER BY X:</b> Por fim, estamos ordenando os resultados em ordem crescente com base no valor de "X". Isso garante que os pares simétricos sejam listados em ordem crescente de acordo com o valor de "X".
    </td>
  </tr>
    
  </table>

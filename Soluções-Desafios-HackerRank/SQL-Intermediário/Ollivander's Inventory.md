  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/harry-potter-and-wands/">Ollivander's Inventory</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.

Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.

The following tables contain data on the wands in Ollivander's inventory:

Wands: The id is the id of the wand, code is the code of the wand, coins_needed is the total number of gold galleons needed to buy the wand, and power denotes the quality of the wand (the higher the power, the better the wand is). 

Wands_Property: The code is the code of the wand, age is the age of the wand, and is_evil denotes whether the wand is good for the dark arts. If the value of is_evil is 0, it means that the wand is not evil. The mapping between code and age is one-one, meaning that if there are two pairs, (code1, age1) and (code2, age2), then (code1 != code2) and (age1 != age2)<br>
    </td>
    </tr>

  <tr>
      <th colspan="2">WANDS</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">id</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">code</td>
      <td width="50%" align="center">Integer</td>
  </tr>

  <tr>
      <td width="50%" align="center">coins_needed</td>
      <td width="50%" align="center">Integer</td>
  </tr>

  <tr>
      <td width="50%" align="center">power</td>
      <td width="50%" align="center">Integer</td>
  </tr>

  <tr>
      <th colspan="2">WANDS_PROPERTY</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">code</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">age</td>
      <td width="50%" align="center">Integer</td>
  </tr>

  <tr>
      <td width="50%" align="center">is_evil</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Você precisa escrever uma consulta SQL que retorne as informações das varinhas que Ron está interessado, ordenadas primeiro pelo poder em ordem decrescente e, em caso de empate no poder, ordenadas pela idade da varinha em ordem decrescente. Você deve considerar apenas varinhas não malignas (não relacionadas às artes das trevas) com alta potência e idade.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>Para resolver este problema, podemos usar uma abordagem que envolve uma junção entre as tabelas Wands e Wands_Property para combinar as informações sobre as varinhas. Além disso, utilizaremos uma subconsulta para encontrar as varinhas com o menor número de galeões necessários, para cada combinação de poder e idade.
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT 
      W.ID,
      WP.AGE,
      W.COINS_NEEDED,
      W.POWER 
  FROM 
      WANDS AS W
      JOIN 
      WANDS_PROPERTY AS WP
      ON (W.CODE = WP.CODE) 
  WHERE 
      WP.IS_EVIL = 0 
      AND 
      W.COINS_NEEDED=(SELECT 
                          MIN(COINS_NEEDED) 
                      FROM
                          WANDS AS X
                          JOIN 
                          WANDS_PROPERTY AS Y 
                          ON (X.CODE = Y.CODE) 
                      WHERE 
                          X.POWER = W.POWER 
                          AND 
                          Y.AGE = WP.AGE) 
  ORDER BY 
      W.POWER DESC, 
      WP.AGE DESC;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SELECT:</b> Seleciona as colunas ID, AGE, COINS_NEEDED e POWER da tabela combinada WANDS e WANDS_PROPERTY.<br>
    <b>2. FROM e JOIN:</b> Realiza uma junção entre as tabelas WANDS e WANDS_PROPERTY usando a condição de igualdade entre CODE em ambas as tabelas.<br>
    <b>3. WHERE:</b> Filtra as varinhas que não são malignas (com IS_EVIL igual a 0).<br>
    <b>4. Subconsulta:</b> Encontra o menor número de galeões necessários (COINS_NEEDED) para varinhas com o mesmo poder e idade.<br>
    <b>5. ORDER BY:</b> Ordena os resultados em ordem decrescente com base na coluna POWER. Em caso de empate no poder, os resultados são ordenados em ordem decrescente com base na coluna AGE.<br>
    <br>
    <i>Essa consulta irá retornar as informações das varinhas que atendem aos critérios especificados e ordená-las conforme solicitado.</i>
    </td>
  </tr>
    
  </table>

  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/draw-the-triangle-1/">Draw The Triangle 1</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):

<p>* * * * *<br>
* * * *  <br>
* * *  <br>
* *  <br>
*<br></p>
Write a query to print the pattern P(20).
<br>
    </td>
    </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>O problema pede para você criar um padrão de asteriscos que será desenhado por Julia, formando um triângulo. O padrão deve ter 20 linhas e seguir a seguinte estrutura:

<p>* * * * * * * * * * * * * * * * *<br>
* * * * * * * * * * * * * * * *<br>
* * * * * * * * * * * * * * *<br>
* * * * * * * * * * * * * *<br>
* * * * * * * * * * * * *<br>
* * * * * * * * * * * *<br>
* * * * * * * * * * *<br>
* * * * * * * * * *<br>
* * * * * * * * *<br>
* * * * * * * *<br>
* * * * * * *<br>
* * * * * *<br>
* * * * *<br>
* * * *<br>
* * *<br>
* *<br>
*<br></p>
Cada linha do padrão possui uma quantidade decrescente de asteriscos, começando com 20 asteriscos na primeira linha e terminando com apenas um asterisco na última linha.

Para resolver o problema, você precisa criar uma consulta SQL que gere esse padrão de triângulo com 20 linhas de asteriscos.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
SELECT 
SET @R = 21;
SELECT REPEAT('* ', @R := @R - 1)
FROM information_schema.tables
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SET @R = 21;:</b> Nesta linha, estamos definindo uma variável de usuário chamada "@R" e atribuindo o valor 21 a ela. Essa variável será usada para controlar o número de repetições no padrão de asteriscos.<br>
    <b>2. SELECT REPEAT('* ', @R := @R - 1) FROM information_schema.tables;:</b> Nesta linha, estamos fazendo uma consulta que consiste em uma função "REPEAT" aplicada ao padrão de asteriscos e repetindo-o várias vezes. A função "REPEAT" repete a string passada como primeiro argumento (no caso, '* ') o número de vezes especificado pelo valor da variável "@R". O valor da variável "@R" é reduzido em 1 a cada repetição usando a expressão "@R := @R - 1".<br>
    <b>3. FROM information_schema.tables;:</b> Nesta parte, estamos selecionando qualquer tabela existente na base de dados do MySQL, usando a tabela "information_schema.tables" como uma fonte temporária de dados. Essa tabela é usada apenas para gerar uma saída para a consulta; o conteúdo real da tabela não é relevante para o resultado final.
    <br>
    <i>Resumindo, o código usa uma variável de usuário para controlar o número de repetições no padrão de asteriscos e a função "REPEAT" para criar o padrão com 20 linhas de asteriscos. A tabela "information_schema.tables" é usada apenas para permitir a execução da consulta e não influencia o resultado do padrão de asteriscos. A consulta resultará em um padrão de triângulo com 20 linhas, onde cada linha tem uma quantidade decrescente de asteriscos.</i>
    </td>
  </tr>
    
  </table>

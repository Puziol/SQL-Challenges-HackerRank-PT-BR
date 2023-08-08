  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/print-prime-numbers/">Print Prime Numbers</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">Write a query to print all prime numbers less than or equal to 1000. Print your result on a single line, and use the ampersand (&) character as your separator (instead of a space).

For example, the output for all prime numbers <=10 would be:

2&3&5&7
<br>
    </td>
    </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>O problema pede para você escrever uma consulta SQL que imprima todos os números primos menores ou iguais a 1000. Você deve imprimir o resultado em uma única linha, usando o caractere '&' como separador (em vez de um espaço).

Os números primos são números naturais maiores que 1 que têm apenas dois divisores: 1 e o próprio número. Por exemplo, 2, 3, 5, 7, 11, etc., são números primos porque eles só são divisíveis por 1 e por eles mesmos.

A saída esperada é uma única linha contendo todos os números primos menores ou iguais a 1000, separados pelo caractere '&'. Por exemplo, a saída para todos os números primos menores ou iguais a 10 seria:

2&3&5&7</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
SET @number = 1;
SET @divisor = 1;

SELECT GROUP_CONCAT(n SEPARATOR '&')
FROM (
  SELECT @number := @number + 1 AS n
  FROM information_schema.tables AS t1,
       information_schema.tables AS t2
  LIMIT 1000
) AS n1
WHERE NOT EXISTS (
  SELECT *
  FROM (
    SELECT @divisor := @divisor + 1 AS d
    FROM information_schema.tables AS t1,
         information_schema.tables AS t2
    LIMIT 1000
  ) AS n2
  WHERE n % d = 0 AND n <> d
);
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    <b>1. SET @number = 1;:</b> Nesta linha, estamos definindo uma variável de usuário chamada "@number" e atribuindo o valor 1 a ela. Essa variável será usada para armazenar os números que estamos verificando se são primos.<br>
    <b>2. SET @divisor = 1;:</b> Nesta linha, estamos definindo outra variável de usuário chamada "@divisor" e atribuindo o valor 1 a ela. Essa variável será usada para armazenar os divisores potenciais dos números que estamos verificando.<br>
    <b>3. SELECT GROUP_CONCAT(n SEPARATOR '&'):</b> Nesta linha, estamos fazendo uma consulta para imprimir os números primos encontrados no formato de uma única linha de texto, onde os números são concatenados com o caractere '&' como separador.<br>
    <b>4. FROM (SELECT @number := @number + 1 AS n FROM information_schema.tables AS t1, information_schema.tables AS t2 LIMIT 1000) AS n1:</b> Nesta parte, estamos gerando uma lista de números de 1 a 1000 usando a tabela "information_schema.tables" como uma fonte temporária de dados. A variável "@number" é incrementada em 1 a cada linha, e cada valor resultante é nomeado como "n" usando a cláusula "AS n". Essa subconsulta é nomeada como "n1".<br>
    <b>1. WHERE NOT EXISTS (SELECT * FROM (SELECT @divisor := @divisor + 1 AS d FROM information_schema.tables AS t1, information_schema.tables AS t2 LIMIT 1000) AS n2 WHERE n % d = 0 AND n <-> d):</b> Nesta parte, estamos verificando se o número "n" (cada valor gerado pela subconsulta anterior) é primo ou não. Para isso, estamos gerando uma lista de possíveis divisores usando a mesma lógica da subconsulta anterior e a variável "@divisor" é incrementada em 1 a cada linha. Em seguida, verificamos se o número "n" é divisível por algum dos divisores gerados e se "n" é diferente do próprio divisor ("n <-> d"). Se o resultado dessa verificação for verdadeiro para todos os divisores gerados, significa que "n" é primo.<br>
    <br>
    <i>Resumindo, o código usa variáveis de usuário para gerar uma lista de números de 1 a 1000 e, em seguida, verifica se cada número é primo ou não. Os números primos encontrados são concatenados em uma única linha de texto, separados pelo caractere '&'. A tabela "information_schema.tables" é usada apenas para permitir a execução da consulta e não influencia o resultado dos números primos gerados. A saída do código será uma lista de números primos menores ou iguais a 1000, separados por '&'. Por exemplo, a saída para todos os números primos menores ou iguais a 10 seria "2&3&5&7".</i>
    </td>
  </tr>
    
  </table>

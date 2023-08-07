  <table width="100%" border="3" cellspacing="0" cellpadding="8">
    <tr>
      <th colspan="2"><a href="https://www.hackerrank.com/challenges/binary-search-tree-1/">Binary Tree Nodes</a></th>
    </tr>
    
  <tr>
      <td colspan="2" align="center">You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.

Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:

Root: If node is root node.  
Leaf: If node is leaf node.  
Inner: If node is neither root nor leaf node.<br>
    </td>
    </tr>

  <tr>
      <th colspan="2">BST</th>
  </tr>
  <tr>
      <th width="50%" align="center">Column</th>
      <th width="50%" align="center">Type</th>
  </tr>
    
  <tr>
      <td width="50%" align="center">N</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td width="50%" align="center">P</td>
      <td width="50%" align="center">Integer</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Problema:</b><br>Você recebe uma tabela chamada BST com duas colunas: N e P. A coluna N representa o valor de um nó em uma Árvore Binária, e a coluna P representa o pai de N.

Você precisa escrever uma consulta SQL para encontrar o tipo de nó na Árvore Binária, ordenado pelo valor do nó. A saída deve ser uma das seguintes para cada nó:

Root (Raiz): Se o nó for um nó raiz.  
Leaf (Folha): Se o nó for um nó folha.  
Inner (Interno): Se o nó não for nem raiz nem folha.</td>
  </tr>
    
  <tr>
      <td colspan="2"  align="center"><b>Resolução em SQL:</b><br>A solução envolve usar uma consulta SQL para verificar se cada nó é uma raiz, uma folha ou um nó interno. Vamos usar as funções de agregação do MySQL para ajudar a identificar esses tipos de nós.
  </tr>
    
  <tr>
      <td colspan="2"  align="left">
        <b>Solução em MYSQL</b><br>
        
  ```sql
  SELECT N,
         CASE
             WHEN P IS NULL THEN 'Root'
             WHEN N NOT IN (SELECT DISTINCT P FROM BST WHERE P IS NOT NULL) THEN 'Leaf'
             ELSE 'Inner'
         END AS NodeType
    FROM BST
   ORDER BY N;
  ```
  <br>
    </td>
  </tr>
    
  <tr>
    <td colspan="2"  align="center">
    <b>Explicação:</b><br>
    1. A cláusula SELECT seleciona as colunas N e P da tabela BST.<br>
    2. A cláusula CASE é usada para determinar o tipo de nó com base nas seguintes condições:  
Se o valor da coluna P for NULL, isso significa que o nó é uma raiz.  
Se o valor da coluna N não estiver presente na coluna P (ou seja, não é um pai em nenhuma entrada), então o nó é uma folha.  
Caso contrário, o nó é interno.<br>
    3. O resultado é ordenado por N, como solicitado no problema.<br>
    <br>
    <i>Esta consulta irá gerar uma lista de nós ordenados por valor, com seu tipo correspondente (Raiz, Folha ou Interno) ao lado de cada nó.</i>
    </td>
  </tr>
    
  </table>

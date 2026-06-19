# Trabalho_Qakaroto_Estruturas_Avancadas_de_Arvore
Este repositório é referente ao trabalho do terceiro semestre de engenharia de software NA.

Parte 1 – Tipos de Árvores

Árvore AVL (Adelson-Velsky e Landis)
Conceito: Trata-se árvore binária de busca (BST) auto-balanceada, garantindo que a diferença de altura entre as subárvores esquerda e direita de qualquer nó (denominada de Fator de Balanceamento) não seja maior que 1 ou menor que -1 
Características: Controle rigoroso do Balanceamento, verificação após cada inserção ou remoção, utiliza rotações para restaurar a ordem.
Vantagens: traz uma busca previsível e extremamente eficiente no pior cenário, mantendo a altura estritamente próxima a log2
Desvantagens: Operações de inserção e remoção demandam mais processamento já que muitas vezes é necessário realizar um rebalanceamento por meio de rotações.
Exemplo Ilustrado: 
<img width="628" height="173" alt="image" src="https://github.com/user-attachments/assets/eb34747e-9e74-4c6f-939c-54128953e187" />

Red-Black Tree (Árvore Rubro-Negra) 
Conceito: Trata-se de uma árvore binária de busca que se auto-balanceia, utilizando um bit extra por nó para armazenar uma "cor" (Vermelho ou Preto), de modo a manter a árvore aproximadamente balanceada.
Regras de coloração: 
1 - todo nó é vermelho ou preto. 
2 - A raiz é sempre preta.
3 - Todas as folhas (NIL/nulos) são pretas. 
4 - Se um nó é vermelho, então seus filhos devem ser pretos (não existem nós vermelhos consecutivos).
5 - Em cada nó, todos os caminhos simples até as folhas descendentes possuem o mesmo número de nós pretos (black-height).
Vantagens: O balanceamento é realizado com menos rotações que a AVL no caso mais desfavorável durante as modificações, o que torna as inserções e remoções mais rápidas.
Desvantagens: Regras de balanceamento e implementação mais complexas; a busca pode ser um pouco mais lenta que em uma árvore AVL, pois pode ser até duas vezes mais alta do que o necessário.
Exemplo Ilustrado:
<img width="2048" height="1536" alt="image" src="https://github.com/user-attachments/assets/84167e37-95e3-47fa-9983-f0184b95e591" />

Árvore N-ária
Conceito: é uma estrutura de árvore generalizada na qual cada nó pode ter até N filhos, invés de apenas dois.
Diferenças em relação às árvores binárias: enquanto a árvore binária limita a ramificação a no máximo dois filhos, a árvore N-ária permite múltiplos caminhos por nó, reduzindo a altura total da árvore em casos de grandes volumes de dados.
Vantagens: melhor representação de hierarquias complexas do mundo real; diminuição do número de acessos a níveis profundos (o que é ideal para armazenamento secundário, como discos rígidos e SSDs)
Desvantagens: gerenciamento de ponteiros complicado; desperdício de memória em nós que não usam a capacidade total de N filhos, a menos que seja implementado de maneira dinâmica; não é tão simples quanto uma árvore binária.
Aplicações Práticas (Geral): N-ária: estruturas de armazenamento (como NTFS, ext4), bancos de dados relacionais e não-relacionais, e árvores de decisão na inteligência artificial.
<img width="400" height="250" alt="image" src="https://github.com/user-attachments/assets/d046c78f-dddf-4ba8-b4b8-ef23d4b50ded" />

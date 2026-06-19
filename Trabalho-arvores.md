# Trabalho_Qakaroto_Estruturas_Avancadas_de_Arvore

Este repositório é referente ao trabalho do terceiro semestre de engenharia de software NA.

---

## Parte 1 – Tipos de Árvores

### Árvore AVL (Adelson-Velsky e Landis)
* **Conceito:** Trata-se árvore binária de busca (BST) auto-balanceada, garantindo que a diferença de altura entre as subárvores esquerda e direita de qualquer nó (denominada de Fator de Balanceamento) não seja maior que 1 ou menor que -1.
* **Características:** Controle rigoroso do Balanceamento, verificação após cada inserção ou remoção, utiliza rotações para restaurar a ordem.
* **Vantagens:** traz uma busca previsível e extremamente eficiente no pior cenário, mantendo a altura estritamente próxima a log2.
* **Desvantagens:** Operações de inserção e remoção demandam mais processamento já que muitas vezes é necessário realizar um rebalanceamento por meio de rotações.

**Exemplo Ilustrado:** <img width="628" height="173" alt="image" src="https://github.com/user-attachments/assets/eb34747e-9e74-4c6f-939c-54128953e187" />

---

### Red-Black Tree (Árvore Rubro-Negra) 
* **Conceito:** Trata-se de uma árvore binária de busca que se auto-balanceia, utilizando um bit extra por nó para armazenar uma "cor" (Vermelho ou Preto), de modo a manter a árvore aproximadamente balanceada.
* **Regras de coloração:** 1. Todo nó é vermelho ou preto. 
  2. A raiz é sempre preta.
  3. Todas as folhas (NIL/nulos) são pretas. 
  4. Se um nó é vermelho, então seus filhos devem ser pretos (não existem nós vermelhos consecutivos).
  5. Em cada nó, todos os caminhos simples até as folhas descendentes possuem o mesmo número de nós pretos (black-height).
* **Vantagens:** O balanceamento é realizado com menos rotações que a AVL no caso mais desfavorável durante as modificações, o que torna as inserções e remoções mais rápidas.
* **Desvantagens:** Regras de balanceamento e implementação mais complexas; a busca pode ser um pouco mais lenta que em uma árvore AVL, pois pode ser até duas vezes mais alta do que o necessário.

**Exemplo Ilustrado:**
<img width="2048" height="1536" alt="image" src="https://github.com/user-attachments/assets/84167e37-95e3-47fa-9983-f0184b95e591" />

---

### Árvore N-ária
* **Conceito:** é uma estrutura de árvore generalizada na qual cada nó pode ter até N filhos, invés de apenas dois.
* **Diferenças em relação às árvores binárias:** enquanto a árvore binária limita a ramificação a no máximo dois filhos, a árvore N-ária permite múltiplos caminhos por nó, reduzindo a altura total da árvore em casos de grandes volumes de dados.
* **Vantagens:** melhor representação de hierarquias complexas do mundo real; diminuição do número de acessos a níveis profundos (o que é ideal para armazenamento secundário, como discos rígidos e SSDs).
* **Desvantagens:** gerenciamento de ponteiros complicado; desperdício de memória em nós que não usam a capacidade total de N filhos, a menos que seja implementado de maneira dinâmica; não é tão simples quanto uma árvore binária.
* **Aplicações Práticas (Geral):** N-ária: estruturas de armazenamento (como NTFS, ext4), bancos de dados relacionais e não-relacionais, e árvores de decisão na inteligência artificial.

<img width="400" height="250" alt="image" src="https://github.com/user-attachments/assets/d046c78f-dddf-4ba8-b4b8-ef23d4b50ded" />

---

## Parte 3 - Rotação Simples à Direita

* **Finalidade:** Diminuir a altura da subárvore esquerda e elevar a da subárvore direita a fim de restaurar um desbalanceamento para a esquerda. 
* **Quando é aplicado:** Quando um nó se torna desbalanceado com sinal positivo (FB = +2) e seu filho esquerdo também indica desbalanceamento para a esquerda (FB >= 0). Trata-se do caso intitulado "Esquerda-Esquerda". 

<img width="357" height="92" alt="image" src="https://github.com/user-attachments/assets/2969cd9b-5893-4a52-907e-ecc606c95699" />

### Rotação Simples para a Esquerda

* **Objetivo:** Baixar a altura da subárvore direita e elevar a da subárvore esquerda para restaurar um desbalanceamento à direita. 
* **Situação em que é aplicada:** Quando um nó se torna desbalanceado com sinal negativo (FB = -2) e seu filho à direita também tende para a direita (FB <= 0). Trata-se do caso "Direita-Direita".

<img width="399" height="95" alt="image" src="https://github.com/user-attachments/assets/04d615d0-f175-4b78-859b-dce0f3ac21cf" />

### Rotação Dupla

Usada quando o desbalanceamento é em "joelho" ou zigue-zague (sinais opostos entre pai e filho).

#### Esquerda-Direita (LR): 
* **Situação:** O nó pai tem FB = +2 e seu filho esquerdo tem FB = -1 (Caso Left-Right).
* **Mecanismo:** Começa-se realizando uma Rotação Simples à Esquerda no filho esquerdo, assim o problema se torna um caso "Esquerda-Esquerda". Então, realiza-se uma Rotação Simples à Direita no pai desbalanceado. 

#### Direita-Esquerda (RE): 
* **Contexto:** O nó pai apresenta um FB de -2, enquanto seu filho à direita tem um FB de +1 (Exemplo de Direita-Esquerda).
* **Mecanismo:** Em primeiro lugar, efetua-se uma Rotação Simples à Direita no filho direito, convertendo o problema em um caso "Direita-Direita". Em seguida, realiza-se uma Rotação Simples à Esquerda no nó pai que está desbalanceado.

<img width="443" height="94" alt="image" src="https://github.com/user-attachments/assets/bf7a1f22-e3fa-4127-b3a4-3b3ade6077ca" />

### Inversão (Espelhamento)

* **Conceito:** Consiste em uma operação realizada em uma árvore na qual os filhos esquerdo e direito de cada nó são trocados de posição de forma recursiva. Como resultado, a estrutura final da árvore se torna uma imagem espelhada da original.
* **Aplicação:** Essa técnica é utilizada em áreas como computação gráfica, especialmente em processos de espelhamento visual e transformação de coordenadas. Além disso, é um exercício bastante comum no estudo de estruturas de dados, pois ajuda a desenvolver o raciocínio lógico e a compreensão de algoritmos recursivos aplicados a árvores.

<img width="311" height="95" alt="image" src="https://github.com/user-attachments/assets/41038409-346d-41a5-b612-13711c0456b0" />

---

## Parte 3 – Aplicação Prática

* **Escolha:** Criação de Jogos (Engine de Física e Detecção de Colisão)
* **Estrutura mais apropriada:** árvore N-ária (particularmente a variação Quadtree, em que cada nó tem exatamente N=4 filhos).
* **Desempenho de Processamento (Física em Tempo Real):** em jogos com muitos elementos na tela, como jogos de tiro, estratégia ou nave, a engine não precisa testar a colisão de cada objeto contra todos os outros a cada frame. Isso resultaria em milhares de verificações desnecessárias. Isso resulta em quedas significativas na taxa de quadros por segundo (FPS). A Quadtree diminui significativamente o custo computacional de um cenário caótico para uma busca organizada com complexidade O(log n).
* **Organização dos Dados por Quadrantes:** a árvore organiza o espaço bidimensional (a tela do jogo) de maneira hierárquica. O nó raiz é o ponto de partida de todo o mapa. Sempre que há um acúmulo de objetos em uma única área, esse nó se divide em quatro nós filhos, que representam os quadrantes: Noroeste (NW), Nordeste (NE), Sudoeste (SW) e Sudeste (SE). Os objetos reais, como jogadores, inimigos e tiros, são armazenados apenas nos nós folhas que correspondem à sua localização precisa no mapa.

**Operações Realizadas pelo sistema:**
* **Busca por colisão por proximidade:** ao disparar um projétil, a engine percorre rapidamente a árvore N-ária para determinar em qual quadrante folha ele se encontra.
* **Filtragem Eficiente:** O teste de colisão real (física pesada) é realizado apenas entre os objetos que estão no mesmo nó folha específico. Projéteis podem ser disparados simultaneamente sem travamentos, pois inimigos localizados em regiões distantes do mapa são imediatamente excluídos do cálculo.

<img width="791" height="617" alt="image" src="https://github.com/user-attachments/assets/117081a7-b25b-4705-add5-a9823ee6ce1e" />

> Apesar de ambas assegurarem buscas em tempo logarítmico, a AVL é rigidamente balanceada, tornando-a um pouco mais rápida para operações de leitura (busca). No entanto, isso vem com um custo elevado em inserções devido às rotações constantes. A Rubro-Negra permite um balanceamento mais flexível (aproximado) por meio de regras de coloração, o que reduz a necessidade de rotações e a torna a opção ideal para sistemas com inserções e remoções de dados frequentes.
>
> A Árvore N-ária se distancia da restrição de 2 filhos por nó. Ao permitir vários ponteiros internos, a árvore tem uma altura total significativamente menor. Isso a estabelece como a estrutura padrão para indexar grandes quantidades de dados que necessitam de armazenamento em disco (como bancos de dados e sistemas de arquivos), reduzindo ao mínimo o custo de leitura física em mídias secundárias.

---

## Referências: 

* CORMEN, Thomas H. et al. Algoritmos: Teoria e Prática. 3ª ed. Rio de Janeiro: Elsevier, 2012.
* SZWARCFITER, Jayme Luiz; MARKENZON, Lilian. Estruturas de Dados e seus Algoritmos. 3ª ed. Rio de Janeiro: LTC, 2010.

**imagens:** * https://upload.wikimedia.org/wikipedia/commons/2/2c/AVL_Rotação_Dupla_à_Esquerda.PNG
* https://image.slidesharecdn.com/rubronegraequipe3-170223090249/75/Arvores-Rubro-Negras-3-2048.jpg
* https://upload.wikimedia.org/wikipedia/commons/0/02/Nary_to_binary_tree_conversion.png

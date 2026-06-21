<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Motivação**
- **Limitação Prática**
  - Solução Natural
  - Pergunta
  - Definição: MT Multifita
  - Definição
  - Teorema de Equivalência
  - Teorema
  - Ideia da Simulação
  - Passo de Simulação
  - Complexidade
  - Custo da Simulação
  - Teorema
  - Análise
  - Consequências
- **Não-Determinismo**
  - Conceito
  - Definição Formal
  - Aceitação
  - Visualização: Árvore de Computação
  - Exemplo de MTN
  - Algoritmo Não-Determinístico
  - Observação
  - Equivalência: $MTN \equiv MTD$
  - Teorema
  - Ideia da Prova
  - Custo da Simulação
  - Teorema
  - Análise
  - Consequência para Complexidade
  - Não-Determinismo e Classes de Complexidade
  - Classe P
  - Classe NP
  - Questão P vs NP
- **MT com Fita Duplamente Infinita**
  - Modelo Padrão
  - Variação
  - Demonstração de Equivalência
  - MT com Fita Bidimensional
  - Descrição
  - MT com Múltiplos Cabeçotes
  - Descrição
  - Utilidade
  - MT com Alfabeto Restrito
  - Mínimo
  - MT com Estados Restritos
  - MT Probabilística
  - Descrição
  - Classes de Complexidade
  - MT Quântica
  - Descrição
  - Poder Computacional
  - Classe BQP
- **Resumo: Equivalências**
- **Variações Equivalentes à MT Padrão**
  - Para Computabilidade
  - Para Complexidade
  - Exercício 1: MT Multifita
  - Exercício 2: Simulação de Multifita
  - Exercício 3: Não-Determinismo
  - Exercício 4: Equivalências
  - Exercício 5: Alfabeto Mínimo
  - Desafio: MT com Oráculo
- **Referências I**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Variações de Máquinas de Turing

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 09

Teoria da Computabilidade e Complexidade  
Ciência da Computação

8 de abril de 2026

The logo of PUCRS, featuring a shield with a cross and a star, and the text "PUCRS" below it.

Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

{1}------------------------------------------------
## Sumário

- 1 Máquinas de Turing Multifita
- 2 Máquinas de Turing Não-Determinísticas
- 3 Outras Variações
- 4 Exercícios

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central panel containing a stylized 'M' and 'U' monogram, flanked by two panels with a repeating cross pattern. Above the shield is a crown, and on either side are crossed keys. A banner at the bottom reads 'AD VERVM DVCIT'.

Coat of arms of the University of São Paulo (USP)

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-b6cb8677b4ffb35c6468fa5c24091bff_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-63ae75eedbc0eeea2efd2ee19c2fbc7d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-7898f899fb291b02fbb353e0337c5514_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-911a4f4b97be8e1dcf81e58b080dc0e2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9cc5ec27db4e35a26008bce9b9cd0bc8_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9b77845519ed6ce33bab327fe59ace1c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9911cc821dddfed7079ce56cbb907c9e_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9642ee15d719705144037077981aaa99_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-4ca62688976b4bef770a81683f9d9eef_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-f254a67565344d514e13763a4e556a70_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-966c4b9785d85823782a007f3ecec1a7_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->
## Motivação
## Limitação Prática

Máquinas de Turing (MTs) com uma única fita são conceitualmente simples, porém a implementação de alguns algoritmos pode ser “complicada”:

- Copiar dados requer muitas passagens pela fita
- Difícil de se trabalhar com múltiplas “variáveis”
- Simular uma MT Universal é uma atividade trabalhosa
### Solução Natural

Permitir múltiplas fitas, cada uma com seu próprio cabeçote.
### Pergunta

Pergunta: isso aumenta o poder computacional? Não! MTs multifita têm o mesmo poder que MTs de uma fita.

{3}------------------------------------------------
### Definição: MT Multifita
### Definição

Uma **MT com  $k$  fitas** é uma 7-tupla

$M = (Q, \Sigma, \Gamma, \delta, q_0, q_{acc}, q_{rej})$  onde:

$$\delta : Q \times \Gamma^k \rightarrow Q \times \Gamma^k \times \{L, R, S\}^k$$

Interpretação de  $\delta(q, a_1, \dots, a_k) = (q', b_1, \dots, b_k, D_1, \dots, D_k)$

Se está no estado  $q$  lendo  $a_i$  na fita  $i$ :

- Escreve  $b_i$  na fita  $i$
- Move cabeçote da fita  $i$  na direção  $D_i$
- Vai para estado  $q'$

Onde  $D_i \in \{L, R, S\}$  ( $S$  = ficar parado).

{4}------------------------------------------------

{5}------------------------------------------------
### Teorema de Equivalência
### Teorema

Para toda MT  $M$  com  $k$  fitas, existe uma MT  $M'$  com 1 fita tal que  $L(M) = L(M')$ .
### Ideia da Simulação

A fita única de  $M'$  simula as  $k$  fitas de  $M$ :

|     |     |     |      |           |     |      |     |           |      |  |  |  |  |  |
|-----|-----|-----|------|-----------|-----|------|-----|-----------|------|--|--|--|--|--|
| $a$ | $b$ | $b$ | $\#$ | $\dot{x}$ | $y$ | $\#$ | $1$ | $\dot{o}$ | $\#$ |  |  |  |  |  |
|-----|-----|-----|------|-----------|-----|------|-----|-----------|------|--|--|--|--|--|

- $\#$  separa o conteúdo das fitas
- Símbolos com ponto ( $\dot{a}$ ) marcam posição do cabeçote
- Alfabeto expandido:  $\Gamma' = \Gamma \cup \dot{\Gamma} \cup \{\#\}$

{6}------------------------------------------------
### Passo de Simulação

Para simular um passo de  $M$  com  $k$  fitas:

- 1 Percorra a fita de  $M'$  da esquerda para a direita, memorizando os  $k$  símbolos marcados (sob os cabeçotes virtuais)
- 2 Consulte a transição de  $M$  para o estado atual e estes  $k$  símbolos
- 3 Percorra novamente, atualizando:
  - Os símbolos marcados (escrita)
  - As posições das marcas (movimento dos cabeçotes)
- 4 Se algum cabeçote virtual ultrapassar o fim de sua seção, desloque tudo para criar espaço
### Complexidade

Um passo de  $M$  é simulado em  $O(n)$  passos de  $M'$ , onde  $n$  é o comprimento total usado nas fitas.

{7}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-c036e2540a94b31357ceb0002f0cacab_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da hierarquia das linguagens de Chomsky, mostrando cinco níveis concêntricos de complexidade crescente.
<!-- /IMAGE_DESCRIPTION -->
### Custo da Simulação
### Teorema

Se uma MT com  $k$  fitas executa em tempo  $t(n)$ , a MT equivalente de 1 fita executa em tempo  $O(t(n)^2)$ .
### Análise

- Após  $t$  passos, as fitas de  $M$  usam no máximo  $O(t)$  células
- Cada passo de  $M$  requer  $O(t)$  passos de  $M'$
- Total:  $t \times O(t) = O(t^2)$  passos
### Consequências

- Para fins de **complexidade**, MTs multifita são no máximo quadraticamente mais eficientes que MTs de uma fita.
- Para questões de **computabilidade**, isso não importa.

{8}------------------------------------------------
## Não-Determinismo
### Conceito

Em cada passo de computação, a MT pode ter **múltiplas** transições possíveis. Nesse caso, a função de transição é modificada para mapear um conjunto de possíveis transições.
### Definição Formal

Uma **MT não-determinística** (MTN) possui função de transição:

$$\delta : Q \times \Gamma \rightarrow \mathcal{P}(Q \times \Gamma \times \{L, R\})$$

$\delta(q, a)$  retorna um **conjunto** de possíveis transições.
### Aceitação

Uma MTN  $M$  aceita  $w$  se **existe** alguma sequência de escolhas que leva a  $q_{acc}$ . Não precisa que **todas** as sequências levem a  $q_{acc}$ , apenas uma.

{9}------------------------------------------------
### Visualização: Árvore de Computação

```
graph TD; C0((C0)) --- C1((C1)); C0 --- C2((C2)); C1 --- C3((C3)); C1 --- C4((C4)); C2 --- C5((C5)); C2 --- C6((C6)); C5 --- dots[$\vdots$];
```

Diagram of a computation tree for a Non-deterministic Turing Machine. The root node is C0. It branches to C1 (left) and C2 (right). C1 branches to C3 (left, labeled 'rej') and C4 (right, labeled 'acc'). C2 branches to C5 (left) and C6 (right, labeled 'rej'). C5 has a vertical ellipsis below it, indicating further branching. Nodes C3, C4, and C6 are highlighted with colored circles: C3 and C6 are red, and C4 is green.

- Cada nó = configuração
- Ramificações = escolhas não-determinísticas
- **Aceita** se algum caminho leva a  $q_{acc}$
- **Rejeita** se todos os caminhos levam a  $q_{rej}$  ou loop

{10}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-29f586959675cafdf81cf934954908eb_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a Deterministic Finite Automaton (DFA) with three states: q0, q1, and q2.
<!-- /IMAGE_DESCRIPTION -->
### Exemplo de MTN
#### Verificar se $n$ é não-primó

Entrada:  $n$  em unário ( $1^n$ )

MTN “adivinha” fatores  $p, q > 1$  e verifica se  $p \times q = n$ .
### Algoritmo Não-Determinístico

- 1 Não-deterministicamente, escolha  $p$  e  $q$  (escrevendo em fitas auxiliares)
- 2 Verifique se  $p > 1$  e  $q > 1$
- 3 Compute  $p \times q$  (deterministicamente)
- 4 Se  $p \times q = n$ , aceite
- 5 Caso contrário, rejeite
### Observação

Se  $n$  é composto, existe escolha de  $p, q$  que aceita. Se  $n$  é primo, nenhuma escolha aceita.

{11}------------------------------------------------
### Equivalência: $MTN \equiv MTD$
### Teorema

Para toda MTN  $N$ , existe uma MT determinística  $D$  tal que  $L(N) = L(D)$ .
### Ideia da Prova

$D$  simula todas as possíveis computações de  $N$  usando **busca em largura** (BFS) na árvore de computação.

- 1 Enumere todos os caminhos de comprimento 1, 2, 3, ...
- 2 Para cada caminho, simule  $N$  seguindo essas escolhas
- 3 Se alguma simulação aceita, aceite
- 4 Se todas rejeitam (e a árvore é finita), rejeite
#### Por que BFS e não DFS?

DFS poderia seguir um ramo infinito e nunca explorar um ramo que aceita.

{12}------------------------------------------------
### Custo da Simulação
### Teorema

Se MTN  $N$  aceita em tempo  $t(n)$ , então a MTD equivalente aceita em tempo  $2^{O(t(n))}$ .
### Análise

- $N$  faz no máximo  $t(n)$  passos para aceitar
- A árvore tem profundidade  $\leq t(n)$
- Com  $b$  escolhas por nó, há  $\leq b^{t(n)}$  folhas
- $D$  explora todos os caminhos até profundidade  $t(n)$
### Consequência para Complexidade

- Para computabilidade:  $\text{MTN} \equiv \text{MTD}$
- Para complexidade: MTN pode ser **exponencialmente** mais rápida

{13}------------------------------------------------
### Não-Determinismo e Classes de Complexidade

<!-- IMAGE_DESCRIPTION: datalab-875c6f4f441fdd3ca7e1908fd1582983_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da Hierarquia de Chomsky mostrando a inclusão entre classes de linguagens.
<!-- /IMAGE_DESCRIPTION -->
### Classe P

Linguagens decidíveis por MTD em tempo polinomial.
### Classe NP

- Linguagens decidíveis por MTN em tempo polinomial.
- Verificação de certificados/gabaritos (certificate/witness) ocorre em tempo polinomial.
### Questão P vs NP

$P = NP?$

- Sabemos que  $P \subseteq NP$
- A simulação de MTN por MTD é exponencial **até então**, isto é, não sabemos se existe simulação polinomial
- É um **problema em aberto** (e famoso) na Ciência da Computação!

{14}------------------------------------------------
## MT com Fita Duplamente Infinita
### Modelo Padrão

Fita infinita apenas à direita; há uma extremidade esquerda.
### Variação

Fita infinita em **ambas** as direções. Não há extremidade esquerda.
### Demonstração de Equivalência

- Utilize duas fitas
  - Uma para posições  $\geq 0$
  - Outra para posições  $< 0$
- Versão alternativa: use uma fita "intercalada"
  - Células pares = direita
  - Células ímpares = esquerda

{15}------------------------------------------------
### MT com Fita Bidimensional
### Descrição

A fita é uma grade bidimensional infinita (ou um plano cartesiano discreto). Cabeçote pode mover:  $\uparrow$ ,  $\downarrow$ ,  $\leftarrow$ ,  $\rightarrow$ , ou  $\times$  (ficar parado).

cabeçote

A 6x4 grid representing a 2D tape. The head is positioned above the second row, fourth column cell, which contains the letter 'b'. The cell to its left (second row, third column) contains the letter 'a', and the cell directly below it (third row, fourth column) contains the letter 'c'. An arrow points from the word 'cabeçote' to the head's position.

|  |  |   |   |  |  |
|--|--|---|---|--|--|
|  |  |   |   |  |  |
|  |  | a | b |  |  |
|  |  |   | c |  |  |
|  |  |   |   |  |  |

Diagram of a 2D tape grid with a head pointing to a cell containing 'b'.
#### Equivalência

Equivale à MT padrão! Pode-se utilizar uma função de pareamento (ou conforme mostrado na enumeração de  $\mathcal{P}(\mathbb{R})$ ).

{16}------------------------------------------------
### MT com Múltiplos Cabeçotes
### Descrição

Uma única fita, mas múltiplos cabeçotes que podem estar em posições diferentes.

Transição depende de todos os símbolos lidos.
#### Equivalência

Equivalente à MT padrão (e à MT multifita).

Simulação: marque as posições dos cabeçotes com símbolos especiais.
### Utilidade

Pode simplificar certos algoritmos, como verificar palíndromos (um cabeçote no início, outro no fim).

{17}------------------------------------------------
### MT com Alfabeto Restrito
#### Pergunta

MTs com alfabeto binário  $\{0, 1, \sqcup\}$  são mais ou menos poderosas se comparadas à MTs com alfabetos maiores?
#### Prova: O tamanho do alfabeto “não importa”

Codifique cada símbolo de  $\Gamma$  como sequência binária de comprimento fixo  $\lceil \log_2 |\Gamma| \rceil$ .

- Cada transição original vira várias transições
- O cabeçote processa blocos de bits
- Tempo aumenta por fator constante (não representa ordem de crescimento)
### Mínimo

Precisamos de pelo menos 2 símbolos além do branco (para ter entrada não-trivial), i.e. MTs com 2 símbolos são universais

{18}------------------------------------------------
### MT com Estados Restritos
#### Pergunta

Qual o número mínimo de estados para universalidade?
#### Resultados

- Existem MTs universais pequenas
- Minsky (1967): MT universal com 7 estados e 4 símbolos
- Rogozhin (1996): várias combinações pequenas
- Neary & Woods (2009): 2 estados e 18 símbolos
#### Trade-off

Menos estados  $\Rightarrow$  mais símbolos necessários (e vice-versa).  
O produto (estados  $\times$  símbolos) tem limite inferior.

{19}------------------------------------------------
### MT Probabilística
### Descrição

Em vez de não-determinismo, as escolhas são feitas com **probabilidades**.

$\delta(q, a)$  retorna uma distribuição de probabilidade sobre transições.
#### Aceitação

- MT aceita  $w$  com probabilidade  $p$
- Linguagem =  $\{w : \Pr[M \text{ aceita } w] > 1/2\}$
- Ou com margem de erro:  $\Pr[\text{aceita}] \geq 2/3$  vs  $\Pr[\text{aceita}] \leq 1/3$
### Classes de Complexidade

- BPP: tempo polinomial com erro bilateral
- RP: tempo polinomial com erro unilateral
- ZPP: tempo esperado polinomial, sem erro

{20}------------------------------------------------
### MT Quântica
### Descrição

Estados são **superposições** de configurações clássicas.  
Transições são operadores unitários (reversíveis).  
Medição ao final colapsa para resultado clássico.
### Poder Computacional

- Mesma classe de linguagens computáveis (Tese de Church-Turing estendida)
- Possivelmente mais **eficiente** para certos problemas
  - Algoritmo de Shor: fatoração em tempo polinomial quântico
  - Algoritmo de Grover: busca com speedup quadrático
### Classe BQP

Linguagens decidíveis por MT quântica em tempo polinomial com erro limitado.

{21}------------------------------------------------
## Resumo: Equivalências
## Variações Equivalentes à MT Padrão

- MT com  $k$  fitas
- MT não-determinística
- MT com fita duplamente infinita
- MT com fita bidimensional
- MT com múltiplos cabeçotes
- MT com alfabeto/estados mínimos
### Para Computabilidade

Todas estas variações reconhecem a mesma classe de linguagens (r.e.) e decidem a mesma classe (recursivas).
### Para Complexidade

- Multifita:  $O(t^2)$  slowdown
- Não-determinismo:  $O(2^t)$  slowdown

{22}------------------------------------------------
### Exercício 1: MT Multifita

- 1 Projete uma MT com 2 fitas para reconhecer  $L = \{a^n b^n c^n : n \geq 0\}$ .
- 2 Projete uma MT com 2 fitas para verificar se uma cadeia é palíndromo. Qual a complexidade de tempo?
  - 
  - Compare com uma solução de 1 fita para palíndromos. Qual a diferença de complexidade?
- 3 Mostre que  $k + 1$  fitas não são mais poderosas que  $k$  fitas (para  $k \geq 1$ ).

Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and the motto 'AD VERVM DVCT'.

{23}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-fb15f15a7d964c8490c9317e43e40c1a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Simulação de Multifita

- 1 Descreva detalhadamente como uma MT de 1 fita simula uma MT de 2 fitas. Inclua:
  - Como o conteúdo das 2 fitas é representado
  - Como os cabeçotes são simulados
  - Como uma transição é simulada

- 2 Se a MT de 2 fitas usa no máximo  $s(n)$  células em cada fita, quanto espaço a MT de 1 fita usa?

- 3 Se a MT de 2 fitas faz  $t(n)$  passos, quantos passos a MT de 1 fita faz?

The image shows a faded watermark of the coat of arms of the University of São Paulo (USP) in the background. It features a central shield with a cross pattern, topped by a crown, and surrounded by decorative elements including keys and a banner with the text 'AD VERVM DVCIT'.

Coat of arms of the University of São Paulo (USP)

{24}------------------------------------------------
### Exercício 3: Não-Determinismo

- 1 Projete uma MTN para reconhecer  $L = \{w\#w : w \in \{a, b\}^*\}$ . Onde o não-determinismo ajuda?
- 2 Projete uma MTN que, dada uma fórmula booleana em CNF, aceita se ela é satisfatível.
- 3 Explique por que a busca em largura (BFS) é necessária na simulação de MTN por MTD, e por que busca em profundidade (DFS) não funciona.
- 4 Se uma MTN tem no máximo 3 escolhas por configuração e aceita em 10 passos, quantos caminhos a MTD simuladora pode precisar explorar?

Faint watermark of the University of Coimbra coat of arms in the background.

{25}------------------------------------------------
### Exercício 4: Equivalências

- 1** Mostre como simular uma MT com fita duplamente infinita usando uma MT com fita infinita apenas à direita.
- 2** Mostre como simular uma MT com fita bidimensional usando uma MT com fita unidimensional. Descreva a função que mapeia coordenadas  $(x, y)$  para posições na fita linear.
- 3** Prove que uma MT com 2 cabeçotes em uma fita é equivalente a uma MT padrão.

The image shows the coat of arms of the University of São Paulo (USP). It features a central shield with a white field containing a grid of green crosses. Above the shield is a crown. On either side of the shield are two supporters: a lion on the left and a bear on the right. Below the shield is a blue ribbon with the Latin motto 'AD VERVM DVCT' in white capital letters.

Coat of arms of the University of São Paulo (USP)

{26}------------------------------------------------
### Exercício 5: Alfabeto Mínimo

- 1 Mostre como codificar o alfabeto  $\{a, b, c, d, \sqcup\}$  usando apenas  $\{0, 1, \sqcup\}$ .
- 2 Se uma MT usa alfabeto de tamanho  $k$ , quantos bits são necessários para codificar cada símbolo?
- 3 Descreva como uma transição da MT original é simulada pela MT com alfabeto binário.
- 4 Qual o aumento no tempo de execução quando usamos a codificação binária?

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a white background and a large blue star in the center. The shield is flanked by two blue lions. Above the shield is a blue crown. A blue banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{27}------------------------------------------------
### Desafio: MT com Oráculo

Uma **MT com oráculo** para uma linguagem  $A$  é uma MT que pode, em um passo, “perguntar” se uma cadeia  $w$  pertence a  $A$  e receber a resposta.

- 1 Defina formalmente uma MT com oráculo (adicione uma fita de consulta e estados especiais).
- 2 Mostre que se  $A$  é decidível, uma MT com oráculo para  $A$  não é mais poderosa que uma MT comum.
- 3 Mostre que existe linguagem  $B$  que é decidível por MT com oráculo para HALT, mas não é decidível por MT comum.
- 4 Se  $A$  não é nem sequer reconhecível, pode uma MT com oráculo para  $A$  decidir linguagens “ainda mais difíceis”?

{28}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and the motto 'AD VERVM DVCT'.

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-86b4670fc1a5a694821ee92b99c1209a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a Pushdown Automaton (PDA) for the language {0^n 1^n : n ≥ 0}.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-fa6c61be003dfbb4ca5587e48a71de94_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

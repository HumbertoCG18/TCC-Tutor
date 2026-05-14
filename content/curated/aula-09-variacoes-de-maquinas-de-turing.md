<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Motivação**
- **Limitação Prática**
  - Solução Natural
  - Pergunta
  - Definição: MT Multifita
  - Visualização: MT com 3 Fitas
  - Teorema de Equivalência
  - Complexidade
  - Análise
  - Consequências
  - Não-Determinismo
  - Conceito
  - Definição Formal
  - Aceitação
  - Visualização: Árvore de Computação
  - Algoritmo Não-Determinístico
  - Equivalência: MTN $\equiv$ MTD
  - Teorema
  - Custo da Simulação
  - Análise
  - Consequência para Complexidade
  - Não-Determinismo e Classes de Complexidade
  - Classe P
  - Classe NP
  - Questão P vs NP
  - MT com Fita Duplamente Infinita
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
  - Trade-off
  - MT Probabilística
  - Classes de Complexidade
  - MT Quântica
  - Descrição
  - Poder Computacional
  - Classe BQP
- **Resumo: Equivalências**
  - Variações Equivalentes à MT Padrão
  - Para Computabilidade
  - Para Complexidade
  - Exercício 1: MT Multifita
  - Exercício 2: Simulação de Multifita
  - Exercício 3: Não-Determinismo
  - Exercício 4: Equivalências
  - Exercício 5: Alfabeto Mínimo
  - Desafio: MT com Oráculo
- **Referências I**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Variações de Máquinas de Turing

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 09  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

8 de abril de 2026

The logo of the PUCRS Escola Politécnica. It features a crest with a shield and a star, with the text "PUCRS" below it. To the right of the crest, the words "ESCOLA" and "POLITÉCNICA" are stacked vertically in a bold, blue, sans-serif font.

Logo of PUCRS Escola Politécnica

A large, faint, gray watermark of the PUCRS seal is positioned on the right side of the slide. The seal includes a shield with a star and the motto "AD VERVM DVOCIT" written in a banner at the bottom.

Faint background watermark of the PUCRS seal

{1}------------------------------------------------
## Sumário

- 1** Máquinas de Turing Multifita
- 2** Máquinas de Turing Não-Determinísticas
- 3** Outras Variações
- 4** Exercícios

A faint, stylized watermark of the coat of arms of the University of Coimbra. It features a shield with a central crest and two side panels decorated with pine-like trees. Above the shield is a crown and two crossed keys. A ribbon at the bottom bears the Latin motto 'AD VERVM DVCTIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8c378a184b5ae4d1605cb74d7b7a7e3f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A faint, stylized watermark of the coat of arms of the University of Coimbra.
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
#### Definição

Uma **MT com  $k$  fitas** é uma 7-tupla

$M = (Q, \Sigma, \Gamma, \delta, q_0, q_{acc}, q_{rej})$  onde:

$$\delta : Q \times \Gamma^k \rightarrow Q \times \Gamma^k \times \{L, R, S\}^k$$
#### Interpretação de $\delta(q, a_1, \dots, a_k) = (q', b_1, \dots, b_k, D_1, \dots, D_k)$

Se está no estado  $q$  lendo  $a_i$  na fita  $i$ :

- Escreve  $b_i$  na fita  $i$
- Move cabeçote da fita  $i$  na direção  $D_i$
- Vai para estado  $q'$

Onde  $D_i \in \{L, R, S\}$  ( $S = \text{ficar parado}$ ).

{4}------------------------------------------------
### Visualização: MT com 3 Fitas

Fita 1: 

|  |  |          |          |          |  |  |  |  |
|--|--|----------|----------|----------|--|--|--|--|
|  |  | <i>a</i> | <i>b</i> | <i>b</i> |  |  |  |  |
|--|--|----------|----------|----------|--|--|--|--|

 $\downarrow$

Fita 2: 

|  |          |          |  |  |  |  |  |  |
|--|----------|----------|--|--|--|--|--|--|
|  | <i>X</i> | <i>Y</i> |  |  |  |  |  |  |
|--|----------|----------|--|--|--|--|--|--|

 $\downarrow$

Fita 3: 

|  |  |  |  |  |          |          |  |  |
|--|--|--|--|--|----------|----------|--|--|
|  |  |  |  |  | <i>1</i> | <i>0</i> |  |  |
|--|--|--|--|--|----------|----------|--|--|

 $\downarrow$

Controle  
(*q*)

Diagram of a 3-tape Turing machine. Fita 1 contains 'a b b' with the head on the second 'b'. Fita 2 contains 'X Y' with the head on 'Y'. Fita 3 contains '1 0' with the head on '1'. A control state 'q' is shown on the right.

- Cada fita tem seu cabeçote independente
- Fita 1 geralmente contém a entrada
- Outras fitas são usadas como “memória de trabalho”

{5}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-ca5566458a134032dd860e88fdaa0d2b_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a 3-tape Turing machine. Fita 1 contains 'a b b' with the head on the second 'b'. Fita 2 contains 'X Y' with the head on 'Y'. Fita 3 contains '1 0' with the head on '1'. A control state 'q' is shown on the...
<!-- /IMAGE_DESCRIPTION -->
### Teorema de Equivalência
#### Teorema

Para toda MT  $M$  com  $k$  fitas, existe uma MT  $M'$  com 1 fita tal que  $L(M) = L(M')$ .
#### Idea da Simulação

A fita única de  $M'$  simula as  $k$  fitas de  $M$ :

|     |           |     |   |           |     |   |   |           |   |  |  |  |  |
|-----|-----------|-----|---|-----------|-----|---|---|-----------|---|--|--|--|--|
| $a$ | $\dot{b}$ | $b$ | # | $\dot{X}$ | $Y$ | # | 1 | $\dot{0}$ | # |  |  |  |  |
|-----|-----------|-----|---|-----------|-----|---|---|-----------|---|--|--|--|--|

- # separa o conteúdo das fitas
- Símbolos com ponto ( $\dot{a}$ ) marcam posição do cabeçote
- Alfabeto expandido:  $\Gamma' = \Gamma \cup \dot{\Gamma} \cup \{\#\}$

{6}------------------------------------------------
#### Passo de Simulação

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
#### Custo da Simulação
#### Teorema

Se uma MT com  $k$  fitas executa em tempo  $t(n)$ , a MT equivalente de 1 fita executa em tempo  $O(t(n)^2)$ .
### Análise

- Após  $t$  passos, as fitas de  $M$  usam no máximo  $O(t)$  células
- Cada passo de  $M$  requer  $O(t)$  passos de  $M'$
- Total:  $t \times O(t) = O(t^2)$  passos
### Consequências

- Para fins de **complexidade**, MTs multifita são no máximo quadraticamente mais eficientes que MTs de uma fita.
- Para questões de **computabilidade**, isso não importa.

{8}------------------------------------------------
### Não-Determinismo
### Conceito

Em cada passo de computação, a MT pode ter **múltiplas** transições possíveis. Nesse caso, a função de transição é modificada para mapear um conjunto de possíveis transições.
### Definição Formal

Uma **MT não-determinística (MTN)** possui função de transição:

$$\delta : Q \times \Gamma \rightarrow \mathcal{P}(Q \times \Gamma \times \{L, R\})$$

$\delta(q, a)$  retorna um **conjunto** de possíveis transições.
### Aceitação

Uma MTN  $M$  aceita  $w$  se **existe** alguma sequência de escolhas que leva a  $q_{acc}$ . Não precisa que **todas** as sequências levem a  $q_{acc}$ , apenas uma.

{9}------------------------------------------------
### Visualização: Árvore de Computação

Diagram of a computation tree for a non-deterministic Turing machine. The root node is C0. It branches into C1 and C2. C1 branches into C3 (labeled 'rej') and C4 (labeled 'acc'). C2 branches into C5 and C6 (labeled 'rej'). C5 has a vertical ellipsis below it. The background features a faint watermark of the University of Coimbra crest.

- Cada nó = configuração
- Ramificações = escolhas não-determinísticas
- Aceita se algum caminho leva a  $q_{acc}$
- Rejeita se todos os caminhos levam a  $q_{rej}$  ou loop

{10}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-d3294dc879b451b369c0b06f42e9b39f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the PUCRS seal
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-053f1077d592e6622cd21dc4bb4cb366_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a computation tree for a non-deterministic Turing machine.
<!-- /IMAGE_DESCRIPTION -->
#### Exemplo de MTN
#### Verificar se $n$ é não-primo

Entrada:  $n$  em unário ( $1^n$ )

MTN “adivinha” fatores  $p, q > 1$  e verifica se  $p \times q = n$ .
### Algoritmo Não-Determinístico

- 1 Não-deterministicamente, escolha  $p$  e  $q$  (escrevendo em fitas auxiliares)
- 2 Verifique se  $p > 1$  e  $q > 1$
- 3 Compute  $p \times q$  (deterministicamente)
- 4 Se  $p \times q = n$ , aceite
- 5 Caso contrário, rejeite
#### Observação

Se  $n$  é composto, existe escolha de  $p, q$  que aceita. Se  $n$  é primo, nenhuma escolha aceita.

{11}------------------------------------------------
### Equivalência: MTN $\equiv$ MTD
### Teorema

Para toda MTN  $N$ , existe uma MT determinística  $D$  tal que  $L(N) = L(D)$ .
#### Idea da Prova

$D$  simula todas as possíveis computações de  $N$  usando **busca em largura** (BFS) na árvore de computação.

- 1 Enumere todos os caminhos de comprimento 1, 2, 3, ...
- 2 Para cada caminho, simule  $N$  seguindo essas escolhas
- 3 Se alguma simulação aceita, aceite
- 4 Se todas rejeitam (e a árvore é finita), rejeite
#### Por que BFS e não DFS?

DFS poderia seguir um ramo infinito e nunca explorar um ramo que aceita.

{12}------------------------------------------------
### Custo da Simulação
#### Teorema

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
### Classe P

Linguagens decidíveis por MTD em tempo polinomial.
### Classe NP

- Linguagens decidíveis por MTN em tempo polinomial.
- Verificação de certificados/gabaritos (certificate/witness) ocorre em tempo polinomial.
### Questão P vs NP

$P = NP$ ?

- Sabemos que  $P \subseteq NP$
- A simulação de MTN por MTD é exponencial **até então**, isto é, não sabemos se existe simulação polinomial
- É um **problema em aberto** (e famoso) na Ciência da Computação!

{14}------------------------------------------------
### MT com Fita Duplamente Infinita
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

Diagrama de uma máquina de Turing com fita bidimensional. Uma seta rotulada "cabeçote" aponta para a célula contendo "b" em uma grade de 4x6. As células adjacentes "a" (à esquerda), "b" (abaixo) e "c" (abaixo de b) estão destacadas em azul.

Diagrama de uma máquina de Turing com fita bidimensional. Uma seta rotulada 'cabeçote' aponta para a célula contendo 'b' em uma grade de 4x6. As células adjacentes 'a' (à esquerda), 'b' (abaixo) e 'c' (abaixo de b) estão destacadas em azul.

<!-- IMAGE_DESCRIPTION: datalab-b90144cfbb81a2d610d920240fda689d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de uma máquina de Turing com fita bidimensional.
<!-- /IMAGE_DESCRIPTION -->
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
### Trade-off

Menos estados  $\Rightarrow$  mais símbolos necessários (e vice-versa).  
O produto (estados  $\times$  símbolos) tem limite inferior.

{19}------------------------------------------------
### MT Probabilística
#### Descrição

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
### Variações Equivalentes à MT Padrão

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

The image is a watermark of the University of Coimbra seal. It features a central shield with a cross and a star, flanked by two figures. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT". The entire seal is rendered in a light gray, semi-transparent style.

Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

{23}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-0ab720844e454afef91e5d68f4ab8ad9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-66e8a5ee8999de53e962b143d5cf86ad_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Simulação de Multifita

- 1 Descreva detalhadamente como uma MT de 1 fita simula uma MT de 2 fitas. Inclua:
  - Como o conteúdo das 2 fitas é representado
  - Como os cabeçotes são simulados
  - Como uma transição é simulada
- 2 Se a MT de 2 fitas usa no máximo  $s(n)$  células em cada fita, quanto espaço a MT de 1 fita usa?
- 3 Se a MT de 2 fitas faz  $t(n)$  passos, quantos passos a MT de 1 fita faz?

The image is a watermark of the University of Coimbra's seal. It features a central shield with a cross and a star, flanked by two figures holding a banner that reads "AD VERVM DVICIT". The entire seal is rendered in a light gray, semi-transparent style.

Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVICIT'.

{24}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8b7d06054b5d46b891858673c714c794_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 3: Não-Determinismo

- 1 Projete uma MTN para reconhecer  $L = \{w\#w : w \in \{a,b\}^*\}$ . Onde o não-determinismo ajuda?
- 2 Projete uma MTN que, dada uma fórmula booleana em CNF, aceita se ela é satisfatível.
- 3 Explique por que a busca em largura (BFS) é necessária na simulação de MTN por MTD, e por que busca em profundidade (DFS) não funciona.
- 4 Se uma MTN tem no máximo 3 escolhas por configuração e aceita em 10 passos, quantos caminhos a MTD simuladora pode precisar explorar?

{25}------------------------------------------------
### Exercício 4: Equivalências

- 1 Mostre como simular uma MT com fita duplamente infinita usando uma MT com fita infinita apenas à direita.
- 2 Mostre como simular uma MT com fita bidimensional usando uma MT com fita unidimensional. Descreva a função que mapeia coordenadas  $(x, y)$  para posições na fita linear.
- 3 Prove que uma MT com 2 cabeçotes em uma fita é equivalente a uma MT padrão.

The image is a watermark of the University of Coimbra seal. It features a shield with a star in the center, surrounded by four quadrants containing various heraldic symbols. Above the shield is a crown, and below it is a ribbon with the Latin motto "AD VERVM DVCT". The entire seal is rendered in a light gray, semi-transparent style.

Watermark of the University of Coimbra seal, featuring a shield with a star and the motto 'AD VERVM DVCT'.

{26}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-513b2f88e0edcd2ffb6b7cf54f465d06_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a star and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 5: Alfabeto Mínimo

- 1 Mostre como codificar o alfabeto  $\{a, b, c, d, \sqcup\}$  usando apenas  $\{0, 1, \sqcup\}$ .
- 2 Se uma MT usa alfabeto de tamanho  $k$ , quantos bits são necessários para codificar cada símbolo?
- 3 Descreva como uma transição da MT original é simulada pela MT com alfabeto binário.
- 4 Qual o aumento no tempo de execução quando usamos a codificação binária?

The image is a watermark of the University of Coimbra seal. It features a shield with a cross and a star, flanked by two figures. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT".

Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

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

Faint watermark of the University of Cambridge crest, featuring a shield with four lions and a central book, surrounded by the Latin motto 'AD VERVM DVOCIT'.

<!-- IMAGE_DESCRIPTION: datalab-b82dcf86cd51c5066a9abaa9c8f6c0f9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Cambridge crest, featuring a shield with four lions and a central book, surrounded by the Latin motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-1d7527f4316cfe2d342b08d1653d1592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS Escola Politécnica
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Motivação**
  - Questão Fundamental
  - Importância para Computação
- **Comparando Conjuntos Infinitos**
  - Ideia Central
  - Observação Surpreendente
- **Definições Formais**
  - Definição: Conjunto Enumerável (Contável)
  - Definição: Conjunto Infinito Contável
  - Definição: Conjunto Não-Enumerável (Incontável)
- **O Conjunto dos Números Inteiros é Enumerável**
  - $\mathbb{N} \times \mathbb{N}$ é Enumerável
  - Função de Pareamento de Cantor
  - O Conjunto dos Números Racionais é Enumerável
- **Propriedades de Conjuntos Enumeráveis**
  - Teorema: União de Enumeráveis
  - Teorema: União Contável de Enumeráveis
  - Teorema: Produto de Enumeráveis
  - Teorema: Subconjunto de Enumerável
  - Strings Finitas são Enumeráveis
  - Consequência: Programas são Enumeráveis
  - Corolário
  - Justificativa
  - Implicação Importante
- **O Conjunto dos Números Reais é Incontável**
  - Teorema (Cantor, 1891)
  - Corolário
- **O Conjunto Potência**
  - Teorema (Cantor)
  - Prova
- **Hierarquia de Cardinalidades**
  - Cardinalidades Infinitas
  - Hipótese do Contínuo
- **Funções: Enumeráveis vs. Não-Enumeráveis**
  - Consequência Fundamental
  - Linguagens Enumeráveis vs. Não-Enumeráveis
  - Definição
  - Contagem
  - Consequência para Teoria da Computação
- **Resumo: A Técnica de Diagonalização**
- **Estrutura do Argumento**
- **Aplicações**
  - Exercício 1: Enumerabilidade
  - Exercício 2: Diagonalização
  - Exercício 3: Cardinalidades
  - Exercício 4: Linguagens
  - Desafio: Hotel de Hilbert
- **Moral**
- **Referências I**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Conjuntos Enumeráveis e Não-Enumeráveis; Argumento da Diagonalização de Cantor

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 02

Teoria da Computabilidade e Complexidade  
Ciência da Computação

23 de fevereiro de 2026

The logo consists of the PUCRS crest on the left, which is a shield with a star and a banner. To the right of the crest, the text "ESCOLA POLITÉCNICA" is written in blue capital letters.

Logo of PUCRS and Escola Politécnica

{1}------------------------------------------------
## Sumário

- 1 Conjuntos Enumeráveis
- 2 Argumento da Diagonalização de Cantor
- 3 Exercícios

The image is a faint, light gray watermark of the Brazilian coat of arms. It features a central shield with a green field containing a white five-pointed star and a gold field containing a white cross. The shield is surmounted by a crown and flanked by two crossed keys. A ribbon at the bottom contains the motto 'AD VERVM DVCIT'.

Coat of arms of Brazil

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-cb00037bd3b3af9720d5551ad2f818dd_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of Brazil
<!-- /IMAGE_DESCRIPTION -->
## Motivação
### Questão Fundamental

Existem “tamanhos” diferentes de infinito?

- Georg Cantor (1845–1918) demonstrou que **sim**
- Desenvolveu a teoria dos conjuntos infinitos
- Introduziu o conceito de **cardinalidade** para conjuntos infinitos
- Provou que existem infinitos “maiores” que outros
### Importância para Computação

A existência de diferentes “tamanhos” (**densidade!**) de infinito tem consequências profundas:

- Existem funções que não podem ser computadas
- Existem linguagens que não podem ser decididas

{3}------------------------------------------------
## Comparando Conjuntos Infinitos
### Ideia Central

Dois conjuntos têm o mesmo “tamanho” se podemos estabelecer uma **correspondência um-para-um** (bijeção) entre eles.

Exemplo:  $\mathbb{N}$  e  $\mathbb{N}^+$

$\mathbb{N} = \{0, 1, 2, 3, \dots\}$  e  $\mathbb{N}^+ = \{1, 2, 3, 4, \dots\}$

Bijeção  $f : \mathbb{N} \rightarrow \mathbb{N}^+$ ,  $f(n) = n + 1$

| $n$    | 0 | 1 | 2 | 3 | ... |
|--------|---|---|---|---|-----|
| $f(n)$ | 1 | 2 | 3 | 4 | ... |
### Observação Surpreendente

$\mathbb{N}^+ \subset \mathbb{N}$  (subconjunto próprio), mas  $|\mathbb{N}^+| = |\mathbb{N}|$ !

Em conjuntos infinitos, “a parte pode ser igual ao todo”.

{4}------------------------------------------------
## Definições Formais
### Definição: Conjunto Enumerável (Contável)

Um conjunto  $A$  é **enumerável** (ou contável) se:

- $A$  é finito, ou
- Existe uma bijeção  $f : \mathbb{N} \rightarrow A$

Equivalentemente: os elementos de  $A$  podem ser listados como uma sequência  $a_0, a_1, a_2, \dots$
### Definição: Conjunto Infinito Contável

Um conjunto  $A$  é **infinito contável** se existe uma bijeção  $f : \mathbb{N} \rightarrow A$ .

Sua cardinalidade é denotada  $\aleph_0$  (“alef-zero”).
### Definição: Conjunto Não-Enumerável (Incontável)

Um conjunto é **não-enumerável** (ou incontável) se não é enumerável.

{5}------------------------------------------------
## O Conjunto dos Números Inteiros é Enumerável
#### Teorema

$\mathbb{Z}$  é enumerável.
#### Prova

Construímos uma bijeção  $f : \mathbb{N} \rightarrow \mathbb{Z}$ :

$$f(n) = \begin{cases} n/2 & \text{se } n \text{ é par} \\ -(n+1)/2 & \text{se } n \text{ é ímpar} \end{cases}$$

|        |   |    |   |    |   |    |   |     |
|--------|---|----|---|----|---|----|---|-----|
| $n$    | 0 | 1  | 2 | 3  | 4 | 5  | 6 | ... |
| $f(n)$ | 0 | -1 | 1 | -2 | 2 | -3 | 3 | ... |

Enumeração:  $0, -1, 1, -2, 2, -3, 3, -4, 4, \dots$

{6}------------------------------------------------
### $\mathbb{N} \times \mathbb{N}$ é Enumerável
#### **Teorema**

O produto cartesiano  $\mathbb{N} \times \mathbb{N}$  é enumerável.
### Função de Pareamento de Cantor

$$\pi : \mathbb{N} \times \mathbb{N} \rightarrow \mathbb{N}$$

$$\pi(x, y) = \frac{(x + y)(x + y + 1)}{2} + y$$

Esta função é uma bijeção!

Diagram showing the diagonal enumeration of the set N x N. A grid of points is shown with x and y axes labeled 0, 1, 2, 3. Arrows indicate the path: (0,0) to (1,0), then (1,0) to (0,1), then (0,1) to (2,0), then (2,0) to (1,1), then (1,1) to (0,2), and so on, following diagonals from bottom-right to top-left.

Enumeração diagonal

Ordem:  $(0, 0), (1, 0), (0, 1), (2, 0), (1, 1), (0, 2), (3, 0), \dots$

{7}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-ab9eb65dcbc2696ec77b66f70f9e0e91_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram showing the diagonal enumeration of the set N x N.
<!-- /IMAGE_DESCRIPTION -->
### O Conjunto dos Números Racionais é Enumerável
#### Teorema

$\mathbb{Q}$  é enumerável.
#### Prova (Esboço)

- 1  $\mathbb{Q}^+ = \{p/q : p, q \in \mathbb{N}^+\}$  pode ser visto como subconjunto de  $\mathbb{N}^+ \times \mathbb{N}^+$
- 2  $\mathbb{N}^+ \times \mathbb{N}^+$  é enumerável (similar a  $\mathbb{N} \times \mathbb{N}$ )
- 3 Logo  $\mathbb{Q}^+$  é enumerável
- 4  $\mathbb{Q} = \mathbb{Q}^- \cup \{0\} \cup \mathbb{Q}^+$  é união de enumeráveis

The diagram shows a grid of positive rational numbers arranged in rows and columns. Blue arrows indicate a zigzag path that visits every cell in the grid, demonstrating that the set of positive rationals is countable.

|               |               |               |               |         |
|---------------|---------------|---------------|---------------|---------|
| $\frac{1}{1}$ | $\frac{2}{1}$ | $\frac{3}{1}$ | $\frac{4}{1}$ |         |
| $\frac{1}{2}$ | $\frac{1}{1}$ | $\frac{3}{2}$ | $\frac{4}{2}$ |         |
| $\frac{1}{3}$ | $\frac{2}{2}$ | $\frac{3}{3}$ | $\frac{4}{3}$ | $\dots$ |
| $\frac{2}{3}$ | $\frac{2}{2}$ | $\frac{3}{3}$ | $\frac{4}{3}$ |         |
| $\frac{3}{3}$ | $\frac{2}{3}$ | $\frac{3}{4}$ | $\frac{4}{4}$ |         |
| $\frac{1}{4}$ | $\frac{2}{4}$ | $\frac{3}{4}$ | $\frac{4}{4}$ |         |

Diagram illustrating the enumeration of positive rational numbers using a zigzag path through a grid of fractions.

{8}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-731f533b0599c8e42a063f06e4332045_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram illustrating the enumeration of positive rational numbers using a zigzag path through a grid of fractions.
<!-- /IMAGE_DESCRIPTION -->
## Propriedades de Conjuntos Enumeráveis
### Teorema: União de Enumeráveis

Se  $A$  e  $B$  são enumeráveis, então  $A \cup B$  é enumerável.
### Teorema: União Contável de Enumeráveis

Se  $A_0, A_1, A_2, \dots$  é uma sequência enumerável de conjuntos enumeráveis, então  $\bigcup_{i=0}^{\infty} A_i$  é enumerável.
### Teorema: Produto de Enumeráveis

Se  $A$  e  $B$  são enumeráveis, então  $A \times B$  é enumerável.
### Teorema: Subconjunto de Enumerável

Todo subconjunto de um conjunto enumerável é enumerável.

{9}------------------------------------------------
### Strings Finitas são Enumeráveis
#### Teorema

Seja  $\Sigma$  um alfabeto finito. O conjunto  $\Sigma^*$  de todas as strings finitas sobre  $\Sigma$  é enumerável.
#### Prova

Ordene  $\Sigma^*$  por:

- 1 Primeiro por comprimento
- 2 Strings de mesmo comprimento em ordem lexicográfica

Esta é uma enumeração bem definida de  $\Sigma^*$ .

Exemplo:  $\Sigma = \{0, 1\}$

$\Sigma^* = \{\varepsilon, 0, 1, 00, 01, 10, 11, 000, 001, 010, 011, 100, \dots\}$

Cada string corresponde a um número natural único (ordem canônica).

{10}------------------------------------------------
### Consequência: Programas são Enumeráveis
### Corolário

O conjunto de todos os programas (em qualquer linguagem de programação com sintaxe finita) é enumerável.
### Justificativa

- Um programa é uma string finita sobre um alfabeto finito
- O conjunto de todas as strings finitas é enumerável
- O conjunto de programas válidos é um subconjunto
- Subconjuntos de enumeráveis são enumeráveis
### Implicação Importante

Existem no máximo  $\aleph_0$  algoritmos/programas possíveis.  
Se existirem mais que  $\aleph_0$  funções ou problemas, então alguns não podem ter algoritmos!

{11}------------------------------------------------
## O Conjunto dos Números Reais é Incontável
### Teorema (Cantor, 1891)

O conjunto  $\mathbb{R}$  dos números reais é **não-enumerável** (incontável).
#### Significado

- Não existe bijeção entre  $\mathbb{N}$  e  $\mathbb{R}$
- $\mathbb{R}$  é “maior” que  $\mathbb{N}$
- Existem diferentes “tamanhos” de infinito!
#### Método da Prova

**Argumento da Diagonalização:** técnica de prova por contradição que constrói um elemento não listado a partir de qualquer suposta enumeração.

{12}------------------------------------------------
#### Prova: $[0, 1)$ é Incontável
#### Teorema

O intervalo  $[0, 1) = \{x \in \mathbb{R} : 0 \leq x < 1\}$  é incontável.
#### Prova por contradição:

Suponha que  $[0, 1)$  seja enumerável. Então existe uma lista:

$$r_0 = 0.d_{0,0}d_{0,1}d_{0,2}d_{0,3} \dots$$

$$r_1 = 0.d_{1,0}d_{1,1}d_{1,2}d_{1,3} \dots$$

$$r_2 = 0.d_{2,0}d_{2,1}d_{2,2}d_{2,3} \dots$$

$$r_3 = 0.d_{3,0}d_{3,1}d_{3,2}d_{3,3} \dots$$

$$\vdots$$

onde  $d_{i,j} \in \{0, 1, 2, \dots, 9\}$  é o  $j$ -ésimo dígito decimal de  $r_i$ .

{13}------------------------------------------------
#### Prova: Construção do Número Diagonal

Construímos um número  $r^* = 0.d_0^*d_1^*d_2^*d_3^*\dots$  onde:

$$d_i^* = \begin{cases} 5 & \text{se } d_{i,i} \neq 5 \\ 6 & \text{se } d_{i,i} = 5 \end{cases}$$

$$r_0 = 0. \color{red}{3} 1 4 1 \dots$$

$$r_1 = 0. 5 \color{red}{5} 5 5 \dots$$

$$r_2 = 0. 7 0 \color{red}{7} 1 \dots$$

$$r_3 = 0. 2 3 5 \color{red}{8} \dots$$

$$r^* = 0. 5 6 5 5 \dots$$

$r^* \neq r_i$  para todo  $i$ , pois diferem no  $i$ -ésimo dígito!

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a large five-pointed star in the center. The shield is flanked by two crossed flags. Above the shield is a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{14}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-55c729bcda4ea78f553b681b7359c733_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-0ab720844e454afef91e5d68f4ab8ad9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->
#### Prova: Conclusão
#### Contradição

- $r^* \in [0, 1)$  (é um número real válido entre 0 e 1)
- $r^* \neq r_i$  para todo  $i \in \mathbb{N}$
- Mas a lista deveria conter **todos** os números em  $[0, 1)$ !

Contradição! Logo,  $[0, 1)$  não pode ser enumerável.  $\square$
### Corolário

$\mathbb{R}$  é incontável.
#### Prova do Corolário

$[0, 1) \subset \mathbb{R}$ . Se  $\mathbb{R}$  fosse enumerável, todo subconjunto seria enumerável. Como  $[0, 1)$  é incontável,  $\mathbb{R}$  também é.  $\square$

{15}------------------------------------------------
## O Conjunto Potência
### Teorema (Cantor)

Para qualquer conjunto  $A$ , vale  $|A| < |\mathcal{P}(A)|$ .

Ou seja, não existe bijeção entre  $A$  e seu conjunto potência.
### Prova

Claramente  $|A| \leq |\mathcal{P}(A)|$  via  $f(a) = \{a\}$ .

Suponha que exista bijeção  $g : A \rightarrow \mathcal{P}(A)$ .

Defina  $B = \{a \in A : a \notin g(a)\}$  (**diagonal!**).

Como  $g$  é sobrejetora, existe  $b \in A$  com  $g(b) = B$ .

**Pergunta:**  $b \in B$ ?

- Se  $b \in B$ , então  $b \notin g(b) = B$ . Contradição!
- Se  $b \notin B$ , então  $b \in g(b) = B$ . Contradição!

Logo, tal bijeção não existe.  $\square$

{16}------------------------------------------------
## Hierarquia de Cardinalidades
### Cardinalidades Infinitas

- $\aleph_0 = |\mathbb{N}|$  — menor cardinalidade infinita
- $|\mathbb{R}| = 2^{\aleph_0} = \mathfrak{c}$  — cardinalidade do **contínuo**
- $|\mathcal{P}(\mathbb{R})| = 2^{\mathfrak{c}}$  — ainda maior!

$$\begin{array}{ccccc} |\mathbb{N}| & < & |\mathbb{R}| = |\mathcal{P}(\mathbb{N})| & < & |\mathcal{P}(\mathbb{R})| \\ \aleph_0 & & 2^{\aleph_0} = \mathfrak{c} & & 2^{\mathfrak{c}} \end{array}$$
### Hipótese do Contínuo

Existe algum conjunto  $S$  com  $|\mathbb{N}| < |S| < |\mathbb{R}|$ ?

Gödel (1940) e Cohen (1963) provaram que o cardinal do contínuo é o próximo cardinal depois de  $\aleph_0$  (ou seja,  $2^{\aleph_0} = \aleph_1$ ).

**Obs.: Consistente com ZFC!**

{17}------------------------------------------------
## Funções: Enumeráveis vs. Não-Enumeráveis

O Conjunto de Todas as Funções  $f : \mathbb{N} \rightarrow \{0, 1\}$

Cada função  $f : \mathbb{N} \rightarrow \{0, 1\}$  corresponde a uma sequência infinita de bits, que representa um número real em  $[0, 1]$  em binário.

$$|\{f : \mathbb{N} \rightarrow \{0, 1\}\}| = 2^{|\mathbb{N}|} = 2^{\aleph_0} = |\mathbb{R}|$$
### Consequência Fundamental

- Existem  $2^{\aleph_0}$  funções  $f : \mathbb{N} \rightarrow \{0, 1\}$
- Existem apenas  $\aleph_0$  programas (strings finitas)
- $\aleph_0 < 2^{\aleph_0}$
- **Logo:** Existem funções que não podem ser computadas por nenhum programa!

{18}------------------------------------------------
### Linguagens Enumeráveis vs. Não-Enumeráveis
### Definição

Uma **linguagem** sobre um alfabeto  $\Sigma$  é um subconjunto de  $\Sigma^*$ .
### Contagem

- $\Sigma^*$  é enumerável (strings finitas)
- O conjunto de todas as linguagens é  $\mathcal{P}(\Sigma^*)$
- $|\mathcal{P}(\Sigma^*)| = 2^{|\Sigma^*|} = 2^{\aleph_0}$  — incontável!
### Consequência para Teoria da Computação

- Existem  $2^{\aleph_0}$  linguagens sobre  $\{0, 1\}$
- Existem apenas  $\aleph_0$  Máquinas de Turing
- **Logo**: Existem linguagens que não são reconhecidas por nenhuma Máquina de Turing!

{19}------------------------------------------------
## Resumo: A Técnica de Diagonalização
## Estrutura do Argumento

- 1 Suponha (por contradição) que o conjunto seja enumerável
- 2 Considere uma enumeração arbitrária dos elementos
- 3 Construa um novo elemento que difere de cada elemento listado em pelo menos uma “casa”
- 4 Mostre que este elemento deveria estar na lista, mas não está
- 5 Conclua que o conjunto é incontável
## Aplicações

- A existência de linguagens não-decidíveis
- A existência de funções não-computáveis
- Teoremas de hierarquia em complexidade
- O problema da parada (Halting Problem)

{20}------------------------------------------------
### Exercício 1: Enumerabilidade

Prove que os seguintes conjuntos são enumeráveis:

- 1 O conjunto dos números naturais pares
- 2 O conjunto dos números primos
- 3  $\mathbb{Z} \times \mathbb{Z}$
- 4 O conjunto de todos os polinômios com coeficientes inteiros
- 5 O conjunto de todas as matrizes  $2 \times 2$  com entradas em  $\mathbb{Q}$

**Dica:** Para cada item, construa explicitamente uma bijeção com  $\mathbb{N}$  ou mostre que é subconjunto/produto de conjuntos enumeráveis.

Faint watermark of the coat of arms of the University of São Paulo (USP) on the right side of the slide.

{21}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8c88a2b2e156c28098d47bdd093e67e0_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of São Paulo (USP) on the right side of the slide.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Diagonalização

- 1 Por que a prova de diagonalização não funciona para mostrar que  $\mathbb{Q}$  é incontável? Onde o argumento falha?
- 2 Adapte o argumento de diagonalização para provar diretamente (sem usar que  $[0, 1)$  é incontável) que o conjunto de todas as sequências infinitas de 0s e 1s é incontável.
- 3 Prove que o conjunto  $\{f : \mathbb{N} \rightarrow \mathbb{N}\}$  de todas as funções de  $\mathbb{N}$  em  $\mathbb{N}$  é incontável.

Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and a banner below reading 'AD VERVM DVCIT'.

{22}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-6f78ea3343d75a12a76a4c51af28da87_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and a banner below reading 'AD VERVM DVCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 3: Cardinalidades

Determine se os seguintes conjuntos têm cardinalidade  $\aleph_0$  ou  $2^{\aleph_0}$ :

- 1** O conjunto dos números irracionais
- 2** O conjunto das funções  $f : \{0, 1\} \rightarrow \mathbb{N}$
- 3** O conjunto das funções  $f : \mathbb{N} \rightarrow \{0, 1\}$
- 4** O conjunto dos subconjuntos finitos de  $\mathbb{N}$
- 5** O conjunto dos subconjuntos infinitos de  $\mathbb{N}$
- 6** O intervalo  $(0, 0.001)$

The image is a faint, light gray watermark of the coat of arms of the University of São Paulo (USP). It features a central shield with a large five-pointed star at the bottom. The shield is flanked by two crossed keys (the keys of St. Peter) and topped by a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{23}------------------------------------------------
### Exercício 4: Linguagens

Seja  $\Sigma = \{a, b\}$ .

- 1 Mostre que o conjunto de todas as linguagens **finitas** sobre  $\Sigma$  é enumerável.
- 2 Mostre que o conjunto de todas as linguagens **regulares** sobre  $\Sigma$  é enumerável.  
**Dica:** Quantas expressões regulares existem?
- 3 Conclua que existem linguagens que não são regulares.
- 4 Sabendo que cada Máquina de Turing pode ser codificada como uma string finita, conclua que existem linguagens que não são reconhecidas por nenhuma Máquina de Turing.

{24}------------------------------------------------
### Desafio: Hotel de Hilbert

- 1** O **Hotel de Hilbert**<sup>1</sup> possui infinitos quartos, numerados  $0, 1, 2, 3, \dots$ , e todos estão ocupados. Um novo hóspede chega. Como acomodá-lo sem expulsar ninguém?
- 2** Um ônibus com infinitos (contáveis) novos hóspedes chega. Como acomodar todos?
- 3** Infinitos ônibus, cada um com infinitos hóspedes, chegam. Os ônibus estão numerados  $0, 1, 2, \dots$  e os passageiros de cada ônibus também. Como acomodar todos?
- 4** Prove que se chegasse um número incontável de hóspedes, seria impossível acomodá-los.
## Moral

Estas situações ilustram propriedades surpreendentes de conjuntos infinitos e a diferença entre infinitos contáveis e incontáveis.

<sup>1</sup><https://clubes.obmep.org.br/blog/desafio-hotel-de-hilbert/>

{25}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

A faint, light gray watermark of a university crest or seal is positioned on the right side of the slide. The crest features a shield with a cross pattern, topped by a crown and flanked by two lions. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Faint watermark of a university crest or seal on the right side of the slide.

<!-- IMAGE_DESCRIPTION: datalab-55fb58e14ec092ccc4fe111de0dc6278_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of a university crest or seal on the right side of the slide.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-1d7527f4316cfe2d342b08d1653d1592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS and Escola Politécnica
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

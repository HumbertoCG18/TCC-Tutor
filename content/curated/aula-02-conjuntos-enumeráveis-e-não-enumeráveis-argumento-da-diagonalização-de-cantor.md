Exercícios

# Conjuntos Enumeráveis e Não-Enumeráveis; Argumento da Diagonalização de Cantor

Prof. Anderson Roberto Pinheiro Domingues

anderson.domingues@pucrs.br

Aula 02

Teoria da Computabilidade e Complexidade Ciência da Computação

23 de fevereiro de 2026

![](content/images/aula-02-conjuntos-enumeráveis-e-não-enumeráveis-argumento-da-diagonalização-de-cantor-_page_0_Picture_10.png)

## Sumário

Conjuntos Enumeráveis

1 Conjuntos Enumeráveis

2 Argumento da Diagonalização de Cantor

3 Exercícios

![](content/images/aula-02-conjuntos-enumeráveis-e-não-enumeráveis-argumento-da-diagonalização-de-cantor-_page_1_Picture_8.png)

## Motivação

Conjuntos Enumeráveis

#### Questão Fundamental

Existem "tamanhos" diferentes de infinito?

- Georg Cantor (1845–1918) demonstrou que sim
- Desenvolveu a teoria dos conjuntos infinitos
- Introduziu o conceito de cardinalidade para conjuntos infinitos
- Provou que existem infinitos "maiores" que outros

### Importância para Computação

A existência de diferentes "tamanhos" (densidade!) de infinito tem consequências profundas:

- Existem funções que não podem ser computadas
- Existem linguagens que não podem ser decididas

# Comparando Conjuntos Infinitos

#### Ideia Central

Dois conjuntos têm o mesmo "tamanho" se podemos estabelecer uma correspondência um-para-um (bijeção) entre eles.

### Exemplo: $\mathbb{N}$ e $\mathbb{N}^+$

$$\mathbb{N} = \{0, 1, 2, 3, \ldots\}$$
 e  $\mathbb{N}^+ = \{1, 2, 3, 4, \ldots\}$   
Bijeção  $f : \mathbb{N} \to \mathbb{N}^+$ ,  $f(n) = n + 1$   
$$\frac{n \mid 0 \quad 1 \quad 2 \quad 3 \quad \cdots}{f(n) \mid 1 \quad 2 \quad 3 \quad 4 \quad \cdots}$$

### Observação Surpreendente

 $\mathbb{N}^+\subset\mathbb{N}$  (subconjunto próprio), mas  $|\mathbb{N}^+|=|\mathbb{N}|!$  Em conjuntos infinitos, "a parte pode ser igual ao todo".

# Definições Formais

### Definição: Conjunto Enumerável (Contável)

Um conjunto A é **enumerável** (ou contável) se:

- *A* é finito, ou
- $\blacksquare$  Existe uma bijeção  $f:\mathbb{N}\to A$

Equivalentemente: os elementos de A podem ser listados como uma sequência  $a_0, a_1, a_2, \dots$ 

### Definição: Conjunto Infinito Contável

Um conjunto A é **infinito contável** se existe uma bijeção  $f: \mathbb{N} \to A$ .

Sua cardinalidade é denotada  $\aleph_0$  ("alef-zero").

## Definição: Conjunto Não-Enumerável (Incontável)

Um conjunto é **não-enumerável** (ou incontável) se não é enumerável.

## O Conjunto dos Números Inteiros é Enumerável

#### Teorema

 $\mathbb{Z}$  é enumerável.

#### Prova

Construímos uma bijeção  $f: \mathbb{N} \to \mathbb{Z}$ :

$$f(n) = \begin{cases} n/2 & \text{se } n \text{ \'e par} \\ -(n+1)/2 & \text{se } n \text{ \'e impar} \end{cases}$$

$$\begin{array}{c|ccccccccccccccccccccccccccccccccccc$$

Enumeração:  $0, -1, 1, -2, 2, -3, 3, -4, 4, \dots$ 

## $\mathbb{N} \times \mathbb{N}$ é Enumerável

#### Teorema

O produto cartesiano  $\mathbb{N} \times \mathbb{N}$  é enumerável.

### Função de Pareamento de Cantor

$$\pi: \mathbb{N} \times \mathbb{N} \to \mathbb{N}$$

$$\pi(x,y) = \frac{(x+y)(x+y+1)}{2} + y$$

Esta função é uma bijeção!

![](content/images/aula-02-conjuntos-enumeráveis-e-não-enumeráveis-argumento-da-diagonalização-de-cantor-_page_6_Figure_11.png)

Enumeração diagonal

Ordem: (0,0),(1,0),(0,1),(2,0),(1,1),(0,2),(3,0),...

Exercícios

## O Conjunto dos Números Racionais é Enumerável

#### Teorema

Q é enumerável.

## Prova (Esboço)

- $\mathbb{1} \ \mathbb{Q}^+ = \{p/q: p,q \in \mathbb{N}^+\} \ \text{pode ser visto como subconjunto de} \\ \mathbb{N}^+ \times \mathbb{N}^+$
- $\mathbb{Z}$   $\mathbb{N}^+ \times \mathbb{N}^+$  é enumerável (similar a  $\mathbb{N} \times \mathbb{N}$ )
- **3** Logo  $\mathbb{Q}^+$  é enumerável
- 4  $\mathbb{Q} = \mathbb{Q}^- \cup \{0\} \cup \mathbb{Q}^+$  é união de enumeráveis

![](content/images/aula-02-conjuntos-enumeráveis-e-não-enumeráveis-argumento-da-diagonalização-de-cantor-_page_7_Figure_12.png)

## Propriedades de Conjuntos Enumeráveis

#### Teorema: União de Enumeráveis

Se A e B são enumeráveis, então  $A \cup B$  é enumerável.

#### Teorema: União Contável de Enumeráveis

Se  $A_0,A_1,A_2,\ldots$  é uma sequência enumerável de conjuntos enumeráveis, então  $\bigcup_{i=0}^{\infty}A_i$  é enumerável.

#### Teorema: Produto de Enumeráveis

Se A e B são enumeráveis, então  $A \times B$  é enumerável.

### Teorema: Subconjunto de Enumerável

Todo subconjunto de um conjunto enumerável é enumerável.

# Strings Finitas são Enumeráveis

#### Teorema

Seja  $\Sigma$  um alfabeto finito. O conjunto  $\Sigma^*$  de todas as strings finitas sobre  $\Sigma$  é enumerável.

#### Prova

Ordene  $\Sigma^*$  por:

- Primeiro por comprimento
- 2 Strings de mesmo comprimento em ordem lexicográfica

Esta é uma enumeração bem definida de  $\Sigma^*$ .

## Exemplo: $\Sigma = \{0, 1\}$

 $\Sigma^* = \{\varepsilon,0,1,00,01,10,11,000,001,010,011,100,\ldots\}$  Cada string corresponde a um número natural único (ordem canônica).

# Consequência: Programas são Enumeráveis

#### Corolário

O conjunto de todos os programas (em qualquer linguagem de programação com sintaxe finita) é enumerável.

#### Justificativa

- Um programa é uma string finita sobre um alfabeto finito
- O conjunto de todas as strings finitas é enumerável
- O conjunto de programas válidos é um subconjunto
- Subconjuntos de enumeráveis são enumeráveis

### Implicação Importante

Existem no máximo  $\aleph_0$  algoritmos/programas possíveis. Se existirem mais que  $\aleph_0$  funções ou problemas, então alguns não podem ter algoritmos!

## O Conjunto dos Números Reais é Incontável

## Teorema (Cantor, 1891)

O conjunto  $\mathbb R$  dos números reais é **não-enumerável** (incontável).

### Significado

- Não existe bijeção entre N e R
- $\blacksquare$   $\mathbb R$  é "maior" que  $\mathbb N$
- Existem diferentes "tamanhos" de infinito!

#### Método da Prova

**Argumento da Diagonalização**: técnica de prova por contradição que constrói um elemento não listado a partir de qualquer suposta enumeração.

# Prova: [0,1) é Incontável

#### Teorema

O intervalo  $[0,1)=\{x\in\mathbb{R}:0\leq x<1\}$  é incontável.

### Prova por contradição:

Suponha que [0,1) seja enumerável. Então existe uma lista:

$$r_0 = 0.d_{0,0}d_{0,1}d_{0,2}d_{0,3} \dots$$

$$r_1 = 0.d_{1,0}d_{1,1}d_{1,2}d_{1,3} \dots$$

$$r_2 = 0.d_{2,0}d_{2,1}d_{2,2}d_{2,3} \dots$$

$$r_3 = 0.d_{3,0}d_{3,1}d_{3,2}d_{3,3} \dots$$

$$\vdots$$

onde  $d_{i,j} \in \{0,1,2,\ldots,9\}$  é o *j*-ésimo dígito decimal de  $r_i$ .

# Prova: Construção do Número Diagonal

Construímos um número  $r^*=0.d_0^*d_1^*d_2^*d_3^*\dots$  onde:

$$d_{i}^{*} = \begin{cases} 5 & \text{se } d_{i,i} \neq 5 \\ 6 & \text{se } d_{i,i} = 5 \end{cases}$$

$$r_{0} = 0 \quad 3 \quad 4 \quad 1 \cdots$$

$$r_{1} = 0 \quad 5 \quad 5 \cdots$$

$$r_{2} = 0 \quad 7 \quad 7 \quad 1 \cdots$$

 $r_3 = 0.23 \frac{8}{8}$ 

 $r^* = 0.5655\cdots$ 

 $r^* \neq r_i$  para todo i, pois diferem no i-ésimo dígito!

## Prova: Conclusão

### Contradição

- $\blacksquare r^* \in [0,1)$  (é um número real válido entre 0 e 1)
- $\rightharpoonup r^* \neq r_i$  para todo  $i \in \mathbb{N}$
- Mas a lista deveria conter todos os números em [0,1)!

Contradição! Logo, [0,1) não pode ser enumerável. $\square$

#### Corolário

 $\mathbb{R}$  é incontável.

#### Prova do Corolário

 $[0,1)\subset\mathbb{R}$ . Se  $\mathbb{R}$  fosse enumerável, todo subconjunto seria enumerável. Como [0,1) é incontável,  $\mathbb{R}$  também é.  $\square$ 

## Teorema (Cantor)

Para qualquer conjunto A, vale  $|A| < |\mathcal{P}(A)|$ .

Ou seja, não existe bijeção entre A e seu conjunto potência.

#### Prova

Claramente  $|A| \leq |\mathcal{P}(A)|$  via  $f(a) = \{a\}$ .

Suponha que exista bijeção  $g:A\to \mathcal{P}(A)$ .

Defina  $B = \{a \in A : a \notin g(a)\}$  (diagonal!).

Como g é sobrejetora, existe  $b \in A$  com g(b) = B.

**Pergunta**:  $b \in B$ ?

- Se  $b \in B$ , então  $b \notin g(b) = B$ . Contradição!
- Se  $b \notin B$ , então  $b \in g(b) = B$ . Contradição!

Logo, tal bijeção não existe.

# Hierarquia de Cardinalidades

#### Cardinalidades Infinitas

- $\blacktriangleright$   $\alpha_0 = |\mathbb{N}|$  menor cardinalidade infinita
- $\blacksquare \ |\mathbb{R}| = 2^{\aleph_0} = \mathfrak{c}$  cardinalidade do **contínuo**
- $|\mathcal{P}(\mathbb{R})| = 2^{\mathfrak{c}}$  ainda maior!

$$|\mathbb{N}|$$
  $<$   $|\mathbb{R}|=|\mathcal{P}(\mathbb{N})|$   $<$   $|\mathcal{P}(\mathbb{R})|$   $2^{\aleph_0}=\mathfrak{c}$   $2^{\mathfrak{c}}$ 

### Hipótese do Contínuo

Existe algum conjunto S com  $|\mathbb{N}|<|S|<|\mathbb{R}|$ ? Gödel (1940) e Cohen (1963) provaram que o cardinal do contínuo é o próximo cardinal depois de  $\aleph_0$  (ou seja,  $2^{\aleph_0}=\aleph_1$ ).

**Obs.: Consistente com ZFC!** 

## Funções: Enumeráveis vs. Não-Enumeráveis

## $\overline{\mathsf{O} \; \mathsf{Conjunto} \; \mathsf{de} \; \mathsf{Todas} \; \mathsf{as} \; \mathsf{Funções} \; f : \mathbb{N} \to \{0,1\}$

Cada função  $f:\mathbb{N} \to \{0,1\}$  corresponde a uma sequência infinita de bits, que representa um número real em [0,1] em binário.

$$|\{f: \mathbb{N} \to \{0,1\}\}| = 2^{|\mathbb{N}|} = 2^{\aleph_0} = |\mathbb{R}|$$

## Consequência Fundamental

- $\blacksquare$  Existem  $2^{\aleph_0}$  funções  $f:\mathbb{N}\to\{0,1\}$
- Existem apenas  $\aleph_0$  programas (strings finitas)
- $\rightharpoonup$   $\alpha_0 < 2^{\aleph_0}$
- Logo: Existem funções que não podem ser computadas por nenhum programa!

# Linguagens Enumeráveis vs. Não-Enumeráveis

### Definição

Uma **linguagem** sobre um alfabeto  $\Sigma$  é um subconjunto de  $\Sigma^*$ .

## Contagem

- $\Sigma^*$  é enumerável (strings finitas)
- $\blacksquare$  O conjunto de todas as linguagens é  $\mathcal{P}(\Sigma^*)$
- $\blacksquare |\mathcal{P}(\Sigma^*)| = 2^{|\Sigma^*|} = 2^{\aleph_0}$  incontável!

## Consequência para Teoria da Computação

- Existem  $2^{\aleph_0}$  linguagens sobre  $\{0,1\}$
- Existem apenas № Máquinas de Turing
- Logo: Existem linguagens que não são reconhecidas por nenhuma Máquina de Turing!

## Resumo: A Técnica de Diagonalização

### Estrutura do Argumento

- 1 Suponha (por contradição) que o conjunto seja enumerável
- 2 Considere uma enumeração arbitrária dos elementos
- 3 Construa um novo elemento que difere de cada elemento listado em pelo menos uma "casa"
- 4 Mostre que este elemento deveria estar na lista, mas não está
- 5 Conclua que o conjunto é incontável

### Aplicações

- A existência de linguagens não-decidíveis
- A existência de funções não-computáveis
- Teoremas de hierarquia em complexidade
- O problema da parada (Halting Problem)

Evercícios

## Exercício 1: Enumerabilidade

Prove que os seguintes conjuntos são enumeráveis:

- 1 O conjunto dos números naturais pares
- O conjunto dos números primos
- $\mathbb{Z} \times \mathbb{Z}$
- 4 O conjunto de todos os polinômios com coeficientes inteiros
- $\bf 5$  O conjunto de todas as matrizes  $2\times 2$  com entradas em  $\Bbb Q$

**Dica**: Para cada item, construa explicitamente uma bijeção com  $\mathbb N$  ou mostre que é subconjunto/produto de conjuntos enumeráveis.

## Exercício 2: Diagonalização

- Por que a prova de diagonalização não funciona para mostrar que Q é incontável? Onde o argumento falha?
- 2 Adapte o argumento de diagonalização para provar diretamente (sem usar que [0,1) é incontável) que o conjunto de todas as sequências infinitas de 0s e 1s é incontável.
- 3 Prove que o conjunto  $\{f: \mathbb{N} \to \mathbb{N}\}$  de todas as funções de  $\mathbb{N}$  em  $\mathbb{N}$  é incontável.

## Exercício 3: Cardinalidades

Determine se os seguintes conjuntos têm cardinalidade  $\aleph_0$  ou  $2^{\aleph_0}$ :

- 1 O conjunto dos números irracionais
- **2** O conjunto das funções  $f: \{0,1\} \rightarrow \mathbb{N}$
- 3 O conjunto das funções  $f: \mathbb{N} \to \{0,1\}$
- O conjunto dos subconjuntos finitos de  $\mathbb N$
- **5** O conjunto dos subconjuntos infinitos de N
- 6 O intervalo (0, 0.001)

![](content/images/aula-02-conjuntos-enumeráveis-e-não-enumeráveis-argumento-da-diagonalização-de-cantor-_page_22_Picture_12.png)

# Exercício 4: Linguagens

Seja 
$$\Sigma = \{a, b\}$$
.

- I Mostre que o conjunto de todas as linguagens **finitas** sobre  $\Sigma$  é enumerável.
- 2 Mostre que o conjunto de todas as linguagens regulares sobre  $\Sigma$  é enumerável.

Dica: Quantas expressões regulares existem?

- 3 Conclua que existem linguagens que não são regulares.
- 4 Sabendo que cada Máquina de Turing pode ser codificada como uma string finita, conclua que existem linguagens que não são reconhecidas por nenhuma Máquina de Turing.

## Desafio: Hotel de Hilbert

- O Hotel de Hilbert<sup>1</sup> possui infinitos quartos, numerados 0, 1, 2, 3, . . . , e todos estão ocupados. Um novo hóspede chega. Como acomodá-lo sem expulsar ninguém?
- 2 Um ônibus com infinitos (contáveis) novos hóspedes chega. Como acomodar todos?
- Infinitos ônibus, cada um com infinitos hóspedes, chegam. Os ônibus estão numerados  $0,1,2,\ldots$  e os passageiros de cada ônibus também. Como acomodar todos?
- 4 Prove que se chegasse um número incontável de hóspedes, seria impossível acomodá-los.

#### Moral

Estas situações ilustram propriedades surpreendentes de conjuntos infinitos e a diferença entre infinitos contáveis e incontáveis.

<sup>&</sup>lt;sup>1</sup>https://clubes.obmep.org.br/blog/desafio-hotel-de-hilbert/

## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. Introduction to Automata Theory, Languages, and Computation. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

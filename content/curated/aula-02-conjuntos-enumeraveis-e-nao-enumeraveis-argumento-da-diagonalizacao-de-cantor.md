<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **1 Conjuntos Enumeráveis**
- **2 Argumento da Diagonalização de Cantor**
- **3 Exercícios**
  - Motivação
  - Questão Fundamental
  - Importância para Computação
  - Comparando Conjuntos Infinitos
  - Idea Central
  - Observação Surpreendente
  - Definições Formais
  - Definição: Conjunto Enumerável (Contável)
  - Definição: Conjunto Infinito Contável
  - Definição: Conjunto Não-Enumerável (Incontável)
  - O Conjunto dos Números Inteiros é Enumerável
  - $\mathbb{N} \times \mathbb{N}$ é Enumerável
  - Função de Pareamento de Cantor
  - O Conjunto dos Números Racionais é Enumerável
  - Propriedades de Conjuntos Enumeráveis
  - Teorema: União de Enumeráveis
  - Strings Finitas são Enumeráveis
  - Corolário
  - O Conjunto dos Números Reais é Incontável
  - Corolário
  - O Conjunto Potência
  - Hierarquia de Cardinalidades
  - Cardinalidades Infinitas
  - Hipótese do Contínuo
- **Funções: Enumeráveis vs. Não-Enumeráveis**
  - O Conjunto de Todas as Funções $f : \mathbb{N} \rightarrow \{0, 1\}$
  - Consequência Fundamental
  - Linguagens Enumeráveis vs. Não-Enumeráveis
  - Definição
  - Contagem
  - Consequência para Teoria da Computação
- **Resumo: A Técnica de Diagonalização**
  - Estrutura do Argumento
  - Aplicações
  - Exercício 1: Enumerabilidade
  - Exercício 2: Diagonalização
  - Exercício 3: Cardinalidades
  - Exercício 4: Linguagens
  - Desafio: Hotel de Hilbert
  - Moral
- **Referências I**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Conjuntos Enumeráveis e Não-Enumeráveis; Argumento da Diagonalização de Cantor

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 02  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

23 de fevereiro de 2026

Logo of PUCRS (Pontifical University of Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

Faint background watermark of the PUCRS seal featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

{1}------------------------------------------------
## Sumário
## 1 Conjuntos Enumeráveis
## 2 Argumento da Diagonalização de Cantor
## 3 Exercícios

A faint, gray watermark of the coat of arms of the University of Coimbra is visible on the right side of the slide. The shield features a central star and is flanked by two sections with a repeating pattern of stylized trees. Above the shield is a crown and two crossed keys. A ribbon at the bottom bears the Latin motto 'AD VERVM DVKIT'.

Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVKIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-b6cb8677b4ffb35c6468fa5c24091bff_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVKIT'.
<!-- /IMAGE_DESCRIPTION -->
### Motivação
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
### Comparando Conjuntos Infinitos
### Idea Central

Dois conjuntos têm o mesmo “tamanho” se podemos estabelecer uma **correspondência um-para-um** (bijecção) entre eles.
#### Exemplo: $\mathbb{N}$ e $\mathbb{N}^+$

$\mathbb{N} = \{0, 1, 2, 3, \dots\}$  e  $\mathbb{N}^+ = \{1, 2, 3, 4, \dots\}$   
Bijecção  $f : \mathbb{N} \rightarrow \mathbb{N}^+, f(n) = n + 1$

|        |   |   |   |   |     |
|--------|---|---|---|---|-----|
| $n$    | 0 | 1 | 2 | 3 | ... |
| $f(n)$ | 1 | 2 | 3 | 4 | ... |
### Observação Surpreendente

$\mathbb{N}^+ \subset \mathbb{N}$  (subconjunto próprio), mas  $|\mathbb{N}^+| = |\mathbb{N}|$ !  
Em conjuntos infinitos, “a parte pode ser igual ao todo”.

{4}------------------------------------------------
### Definições Formais
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
### O Conjunto dos Números Inteiros é Enumerável
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
#### Teorema

O produto cartesiano  $\mathbb{N} \times \mathbb{N}$  é enumerável.
### Função de Pareamento de Cantor

$$\pi : \mathbb{N} \times \mathbb{N} \rightarrow \mathbb{N}$$

$$\pi(x, y) = \frac{(x + y)(x + y + 1)}{2} + y$$

Esta função é uma bijeção!

Diagram illustrating the diagonal enumeration of N x N. A grid of points is shown with axes labeled 0, 1, 2, 3. Arrows indicate the enumeration path: (0,0) -> (1,0) -> (0,1) -> (2,0) -> (1,1) -> (0,2) -> (3,0) -> (2,1) -> (1,2) -> (0,3). The background features a faint watermark of a coat of arms with the text 'AD ERVM DVCTI'.

Enumeração diagonal

Ordem:  $(0, 0), (1, 0), (0, 1), (2, 0), (1, 1), (0, 2), (3, 0), \dots$

{7}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-ab9eb65dcbc2696ec77b66f70f9e0e91_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram illustrating the diagonal enumeration of N x N.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-731f533b0599c8e42a063f06e4332045_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A diagram illustrating the Cantor diagonal argument.
<!-- /IMAGE_DESCRIPTION -->
### O Conjunto dos Números Racionais é Enumerável
#### Teorema

$\mathbb{Q}$  é enumerável.
#### Prova (Esboço)

- 1  $\mathbb{Q}^+ = \{p/q : p, q \in \mathbb{N}^+\}$  pode ser visto como subconjunto de  $\mathbb{N}^+ \times \mathbb{N}^+$
  - 2  $\mathbb{N}^+ \times \mathbb{N}^+$  é enumerável (similar a  $\mathbb{N} \times \mathbb{N}$ )
  - 3 Logo  $\mathbb{Q}^+$  é enumerável
  - 4  $\mathbb{Q} = \mathbb{Q}^- \cup \{0\} \cup \mathbb{Q}^+$  é união de enumeráveis

A diagram illustrating the Cantor diagonal argument. It shows a grid of numbers with four columns. Column 1 contains 1/1, 1/2, 1/3, 1/4. Column 2 contains 1/1, 2/2, 3/3, 4/4. Column 3 contains 1/1, 2/1, 3/2, 4/3. Column 4 contains 4/1, 4/2, 4/3, 4/4. Blue arrows trace a path: from 1/1 in column 1 to 1/1 in column 2, then to 2/2 in column 2, then to 1/1 in column 3, then to 2/1 in column 3, then to 3/2 in column 3, and finally to 4/3 in column 3. The path zig-zags through the grid, highlighting the diagonal elements of each column.

{8}------------------------------------------------
### Propriedades de Conjuntos Enumeráveis
### Teorema: União de Enumeráveis

Se  $A$  e  $B$  são enumeráveis, então  $A \cup B$  é enumerável.
#### Teorema: União Contável de Enumeráveis

Se  $A_0, A_1, A_2, \dots$  é uma sequência enumerável de conjuntos enumeráveis, então  $\bigcup_{i=0}^{\infty} A_i$  é enumerável.
#### Teorema: Produto de Enumeráveis

Se  $A$  e  $B$  são enumeráveis, então  $A \times B$  é enumerável.
#### Teorema: Subconjunto de Enumerável

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
#### Consequência: Programas são Enumeráveis
### Corolário

O conjunto de todos os programas (em qualquer linguagem de programação com sintaxe finita) é enumerável.
#### Justificativa

- Um programa é uma string finita sobre um alfabeto finito
- O conjunto de todas as strings finitas é enumerável
- O conjunto de programas válidos é um subconjunto
- Subconjuntos de enumeráveis são enumeráveis
#### Implicação Importante

Existem no máximo  $\aleph_0$  algoritmos/programas possíveis.  
Se existirem mais que  $\aleph_0$  funções ou problemas, então alguns não podem ter algoritmos!

{11}------------------------------------------------
### O Conjunto dos Números Reais é Incontável
#### Teorema (Cantor, 1891)

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

$$r_0 = 0.d_{0,0}d_{0,1}d_{0,2}d_{0,3}\dots$$

$$r_1 = 0.d_{1,0}d_{1,1}d_{1,2}d_{1,3}\dots$$

$$r_2 = 0.d_{2,0}d_{2,1}d_{2,2}d_{2,3}\dots$$

$$r_3 = 0.d_{3,0}d_{3,1}d_{3,2}d_{3,3}\dots$$

$$\vdots$$

onde  $d_{i,j} \in \{0, 1, 2, \dots, 9\}$  é o  $j$ -ésimo dígito decimal de  $r_i$ .

The image is a watermark of the University of Coimbra seal. It features a shield with a star in the center, surrounded by four quadrants containing various heraldic symbols. Above the shield is a crown. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT". The entire seal is rendered in a light gray color.

Watermark of the University of Coimbra seal, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{13}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-b6eb6de2eec0bcedfced4208ba3862f2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-6f78ea3343d75a12a76a4c51af28da87_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a crown, a shield with a star, and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
#### Prova: Construção do Número Diagonal

Construímos um número  $r^* = 0.d_0^*d_1^*d_2^*d_3^* \dots$  onde:

$$d_i^* = \begin{cases} 5 & \text{se } d_{i,i} \neq 5 \\ 6 & \text{se } d_{i,i} = 5 \end{cases}$$

$$r_0 = 0. \textcircled{3} 1 4 1 \dots$$

$$r_1 = 0. 5 \textcircled{5} 5 5 \dots$$

$$r_2 = 0. 7 0 \textcircled{7} 1 \dots$$

$$r_3 = 0. 2 3 5 \textcircled{8} \dots$$

$$r^* = 0. 5 6 5 5 \dots$$

$r^* \neq r_i$  para todo  $i$ , pois diferem no  $i$ -ésimo dígito!

The image is a watermark of the coat of arms of the University of Coimbra. It features a shield with a star in the center, surrounded by four quadrants containing various heraldic symbols. Above the shield is a crown, and below it is a ribbon with the Latin motto "AD VERVM DVOCIT". The entire emblem is rendered in a light gray color.

Watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{14}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-55c729bcda4ea78f553b681b7359c733_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
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
### O Conjunto Potência
#### Teorema (Cantor)

Para qualquer conjunto  $A$ , vale  $|A| < |\mathcal{P}(A)|$ .  
Ou seja, não existe bijeção entre  $A$  e seu conjunto potência.
#### Prova

Claramente  $|A| \leq |\mathcal{P}(A)|$  via  $f(a) = \{a\}$ .  
Suponha que exista bijeção  $g : A \rightarrow \mathcal{P}(A)$ .  
Defina  $B = \{a \in A : a \notin g(a)\}$  (**diagonal!**).  
Como  $g$  é sobrejetora, existe  $b \in A$  com  $g(b) = B$ .  
**Pergunta:**  $b \in B$ ?

- Se  $b \in B$ , então  $b \notin g(b) = B$ . Contradição!
- Se  $b \notin B$ , então  $b \in g(b) = B$ . Contradição!

Logo, tal bijeção não existe.  $\square$

{16}------------------------------------------------
### Hierarquia de Cardinalidades
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
### O Conjunto de Todas as Funções $f : \mathbb{N} \rightarrow \{0, 1\}$

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
- **Logo:** Existem linguagens que não são reconhecidas por nenhuma Máquina de Turing!

{19}------------------------------------------------
## Resumo: A Técnica de Diagonalização
### Estrutura do Argumento

- 1 Suponha (por contradição) que o conjunto seja enumerável
- 2 Considere uma enumeração arbitrária dos elementos
- 3 Construa um novo elemento que difere de cada elemento listado em pelo menos uma “casa”
- 4 Mostre que este elemento deveria estar na lista, mas não está
- 5 Conclua que o conjunto é incontável
### Aplicações

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

The image is a watermark of the University of Coimbra seal. It features a shield with a crown on top, supported by two figures. The shield is divided into sections containing various heraldic symbols. Below the shield is a ribbon with the Latin motto 'AD VERVM DVKIT'.

Watermark of the University of Coimbra seal, featuring a shield with a crown and the motto 'AD VERVM DVKIT'.

{21}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8c88a2b2e156c28098d47bdd093e67e0_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a crown and the motto 'AD VERVM DVKIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Diagonalização

- 1 Por que a prova de diagonalização não funciona para mostrar que  $\mathbb{Q}$  é incontável? Onde o argumento falha?
- 2 Adapte o argumento de diagonalização para provar diretamente (sem usar que  $[0, 1)$  é incontável) que o conjunto de todas as sequências infinitas de 0s e 1s é incontável.
- 3 Prove que o conjunto  $\{f : \mathbb{N} \rightarrow \mathbb{N}\}$  de todas as funções de  $\mathbb{N}$  em  $\mathbb{N}$  é incontável.

The image is a faint, gray watermark of the University of Coimbra's coat of arms. It features a crown at the top, a shield with a star in the center and four smaller stars in the quadrants, and a ribbon at the bottom with the Latin motto "AD VERVM DVOCIT".

Watermark of the University of Coimbra seal, featuring a crown, a shield with a star, and the motto 'AD VERVM DVOCIT'.

{22}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-d3294dc879b451b369c0b06f42e9b39f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the PUCRS seal featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 3: Cardinalidades

Determine se os seguintes conjuntos têm cardinalidade  $\aleph_0$  ou  $2^{\aleph_0}$ :

- 1 O conjunto dos números irracionais
- 2 O conjunto das funções  $f : \{0, 1\} \rightarrow \mathbb{N}$
- 3 O conjunto das funções  $f : \mathbb{N} \rightarrow \{0, 1\}$
- 4 O conjunto dos subconjuntos finitos de  $\mathbb{N}$
- 5 O conjunto dos subconjuntos infinitos de  $\mathbb{N}$
- 6 O intervalo  $(0, 0.001)$

The image is a watermark of the coat of arms of the University of Coimbra. It features a shield with a star in the center, surrounded by a pattern of small crosses. The shield is supported by two figures, and a banner at the bottom reads "AD VERVM DVICIT".

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{23}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-0ab720844e454afef91e5d68f4ab8ad9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 4: Linguagens

Seja  $\Sigma = \{a, b\}$ .

- 1 Mostre que o conjunto de todas as linguagens **finitas** sobre  $\Sigma$  é enumerável.
- 2 Mostre que o conjunto de todas as linguagens **regulares** sobre  $\Sigma$  é enumerável.  
**Dica:** Quantas expressões regulares existem?
- 3 Conclua que existem linguagens que não são regulares.
- 4 Sabendo que cada Máquina de Turing pode ser codificada como uma string finita, conclua que existem linguagens que não são reconhecidas por nenhuma Máquina de Turing.

{24}------------------------------------------------
### Desafio: Hotel de Hilbert

- 1 O **Hotel de Hilbert**<sup>1</sup> possui infinitos quartos, numerados  $0, 1, 2, 3, \dots$ , e todos estão ocupados. Um novo hóspede chega. Como acomodá-lo sem expulsar ninguém?
- 2 Um ônibus com infinitos (contáveis) novos hóspedes chega. Como acomodar todos?
- 3 Infinitos ônibus, cada um com infinitos hóspedes, chegam. Os ônibus estão numerados  $0, 1, 2, \dots$  e os passageiros de cada ônibus também. Como acomodar todos?
- 4 Prove que se chegasse um número incontável de hóspedes, seria impossível acomodá-los.
### Moral

Estas situações ilustram propriedades surpreendentes de conjuntos infinitos e a diferença entre infinitos contáveis e incontáveis.

<sup>1</sup><https://clubes.obmep.org.br/blog/desafio-hotel-de-hilbert/>

{25}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

Faint background watermark of the University of Cambridge crest, featuring a shield with four lions and a closed book, with the motto 'AD VERVM DVCTIT' on a ribbon below.

<!-- IMAGE_DESCRIPTION: datalab-55fb58e14ec092ccc4fe111de0dc6278_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the University of Cambridge crest, featuring a shield with four lions and a closed book, with the motto 'AD VERVM DVCTIT' on a ribbon below.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-84a1d09fb489061482111515543b60dc_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifical University of Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

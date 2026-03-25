Prof. Anderson Roberto Pinheiro Domingues

anderson.domingues@pucrs.br

Aula 01

Teoria da Computabilidade e Complexidade Ciência da Computação

23 de fevereiro de 2026

![](content/images/aula-01-apresentação-da-disciplina-revisão-de-teoria-de-conjuntos-e-enumerabilidade-_page_0_Picture_10.png)

![](_page_0_Picture_11.jpeg)

## Sumário

- 1 Professor
- 2 Disciplina
- 3 Teoria de Conjuntos
- 4 Exercícios

![](content/images/aula-01-apresentação-da-disciplina-revisão-de-teoria-de-conjuntos-e-enumerabilidade-_page_1_Picture_9.png)

- Lattes: http://lattes.cnpq.br/5879502837295804
- Professor Adjunto. PUCRS
  - Pesquisador

- LSA Laboratório de Sistemas Autônomos, Robótica: https://lsa-pucrs.github.io/
- GAPH Grupo de Apoio ao Projeto de Hardware, SESD¹: https://gaph-pucrs.github.io/
- Comissão Coordenadora de Curso (CCC-ECo)
- Disciplinas (2026-1):
  - Introdução à Programação ECo
  - Algoritmos e Estruturas de Dados I ECo
  - Sistemas Digitais
  - Confiabilidade e Segurança de Hardware
  - Teoria da Computabilidade e Complexidade
  - Trabalho de Conclusão de Curso I e II (CC)
- Contato: anderson.domingues@pucrs.br ou via Moodle

<sup>&</sup>lt;sup>1</sup>Sistemas Embarcados e Sistemas Digitais

# ■ Pontualidade: a chamada será realizada a cada início de período. Não comparecer em ao menos 75% das aulas acarretará em reprovação imediata;

- Conduta: Seja respeituoso e cortês, não produza ruídos desnecessários durante as aulas; peça a palavra antes de falar;
- Ambiente Moodle<sup>2</sup>:
  - Cronograma, plano de ensino e material;
  - SARC: https://sarc.pucrs.br
  - Todos os trabalhos serão entregues via Moodle; trabalhos enviados por e-mail serão solenemente ignorados
  - Não há tolerância para atrasos nas entregas de trabalhos;
  - É dever do aluno consultar o moodle periodicamente;
- Honestidade acadêmica: Plágio é crime<sup>3</sup>!

<sup>&</sup>lt;sup>2</sup>https://moodle.pucrs.br/

https://www.planalto.gov.br/ccivil\_03/leis/2003/110.695.htm

- **Objetivo**: Estudar os limites fundamentais da computação
- O que pode ser computado? (Computabilidade)
- Quão eficientemente pode ser computado? (Complexidade)

#### Questões Fundamentais

- Existem problemas que **nenhum** computador pode resolver?
- Por que alguns problemas são mais difíceis que outros?
- Como classificar problemas por *dificuldade*?

#### **Ementa**

Professor

- Parte I: Fundamentos
  - Teoria de Conjuntos e Cardinalidade
  - Funções Recursivas e Computabilidade
- Parte II: Computabilidade
  - Máquinas de Turing
  - Linguagens Decidíveis e Reconhecíveis
  - Problemas Indecidíveis (Halting Problem, etc.)
- Parte III: Complexidade
  - Classes P e NP
  - NP-Completude e Reduções
  - PSPACE e além

![](content/images/aula-01-apresentação-da-disciplina-revisão-de-teoria-de-conjuntos-e-enumerabilidade-_page_5_Picture_17.png)

## Bibliografia

Professor

#### Bibliografia da Disciplina, livros principais

- SIPSER, M. *Introduction to the Theory of Computation*. 2rd ed. Cengage, 2012.
- PAPADIMITRIOU, C. *Computational Complexity*. Addison-Wesley, 1994.

#### Recomendação

- ROSEN, KENNETH H., *Discrete Mathematics Applications*. 8th ed. McGraw-Hill, 2019.
- <sup>4</sup>HOPCROFT, J.; MOTWANI, R.; ULLMAN, J. *Introduction to Automata Theory, Languages, and Computation*. 3rd ed. Pearson, 2006.

<sup>&</sup>lt;sup>4</sup>Disciplina de Ling. Formais e Autônomatos

- Entender os **limites fundamentais** da computação
- Reconhecer problemas intratáveis antes de tentar resolvê-los
- Base teórica para:
  - Criptografia (problemas difíceis $\Rightarrow$ seguranca)
  - Otimização (saber quando usar heurísticas)
  - Inteligência Artificial (limites do que pode ser aprendido)
  - Verificação de Software (decidibilidade de propriedades)

#### **Importante**

Professor

Esta disciplina é **teórica** e **matemática**. Requer familiaridade com provas formais, indução, e raciocínio abstrato.

## Conjuntos: Definições Básicas

#### Conjunto

Professor

Coleção de objetos distintos, chamados elementos ou membros.

- Notação:  $a \in A$  significa "a pertence ao conjunto A"
- $a \notin A$  significa "a não pertence a A"
- Conjuntos podem ser definidos por:
  - Enumeração:  $A = \{1, 2, 3, 4, 5\}$
  - **Compreensão**:  $A = \{x \in \mathbb{Z} \mid x > 0 \land x \le 5\}$

#### Conjuntos Importantes

- $\blacksquare$   $\mathbb{N} = \{0, 1, 2, 3, \ldots\}$  Números naturais
- $\blacksquare$   $\mathbb{Z} = \{\ldots, -2, -1, 0, 1, 2, \ldots\}$  Números inteiros
- $\mathbb{Q}$ Números racionais
- $\mathbb{R}$ Números reais

#### Subconjunto

Professor

 $A \subseteq B$  se todo elemento de A também está em B:

$$A \subseteq B \iff \forall x (x \in A \Rightarrow x \in B)$$

#### Igualdade

$$A = B$$
 se  $A \subseteq B$  e  $B \subseteq A$ 

#### Subconjunto Próprio

 $A \subset B$  se  $A \subseteq B$  e  $A \neq B$ 

#### Exemplos

- $\{1,2\} \subseteq \{1,2,3\}$  ✓
- $\blacksquare \ \mathbb{N} \subset \mathbb{Z} \subset \mathbb{Q} \subset \mathbb{R}$
- $lack \emptyset \subseteq A$  para qualquer conjunto A

## Operações com Conjuntos

#### União

Professor

$$A \cup B = \{x \mid x \in A \lor x \in B\}$$

#### Interseção

$$A \cap B = \{x \mid x \in A \land x \in B\}$$

#### Diferenca

$$A - B = \{ x \mid x \in A \land x \notin B \}$$

#### Complemento

 $\overline{A} = U - A$  (em relação ao universo U)

#### Produto Cartesiano

$$A \times B = \{(a, b) \mid a \in A \land b \in B\}$$

#### Conjunto Potência

$$\mathcal{P}(A) = \{B \mid B \subseteq A\}$$

## Cardinalidade

Professor

#### Definição

A **cardinalidade** de um conjunto A, denotada |A|, é o "número de elementos" de A.

- $|\{a,b,c\}|=3$
- $\blacksquare$   $|\emptyset| = 0$
- $|\mathcal{P}(A)| = 2^{|A|}$  para conjuntos finitos

#### Para Conjuntos Infinitos

A cardinalidade é definida via bijeções:

$$|A| = |B| \iff \exists f : A \to B \text{ bijetora}$$

#### Questão Central

Todos os conjuntos infinitos têm o "mesmo tamanho"?

## Funções

Professor

#### Definição

Uma **função**  $f: A \rightarrow B$  associa cada elemento de A (domínio) a exatamente um elemento de B (contradomínio).

Cuidado: contradomínio é diferente de imagem!

#### Tipos de Funções

■ Injetora:  $f(a_1) = f(a_2) \Rightarrow a_1 = a_2$ 

■ Sobrejetora:  $\forall b \in B, \exists a \in A : f(a) = b$ 

■ **Bijetora**: Injetora e sobrejetora; **admite inversa**  $f^{-1}: B \to A$ 

![](content/images/aula-01-apresentação-da-disciplina-revisão-de-teoria-de-conjuntos-e-enumerabilidade-_page_12_Picture_12.png)

#### Definição

Uma **relação** R sobre A é um subconjunto de  $A \times A$ . Escrevemos aRb ou  $(a,b) \in R$ .

#### Propriedades de Relações

- Reflexiva:  $\forall a \in A : aRa$ , exemplo: =
- Simétrica:  $aRb \Rightarrow bRa$ , exemplo:  $\neq$
- Transitiva:  $aRb \wedge bRc \Rightarrow aRc$ , exemplo: <
- Antissimétrica:  $aRb \wedge bRa \Rightarrow a = b$ , exemplo: <

#### Relação de Equivalência

- É uma relação que é reflexiva, simétrica e transitiva
- Particiona o conjunto em classes de equivalência.

#### Relação de Ordem

- É uma relação que é reflexiva, antissimétrica e transitiva
- Particiona o conjunto em classes de ordem.
- Pode ser parcial (ex.  $\subseteq$ ) ou total (ex.  $\le$ ), ou total (ex.  $\le$ ) se para todo a, b, a < b ou b < a.

## Princípio da Inducão

Professor

#### Inducão Matemática

Para provar P(n) para todo  $n > n_0$ :

**1 Base**: Provar  $P(n_0)$ 

**2 Passo Indutivo**: Provar que  $P(k) \Rightarrow P(k+1)$ 

#### Indução Forte vs. Fraca

■ Indução Fraca:  $P(k) \Rightarrow P(k+1)$ 

■ Indução Forte:  $(P(n_0) \land P(n_0+1) \land ... \land P(k)) \Rightarrow P(k+1)$ 

#### Exemplo: Soma dos primeiros n naturais

Provar:  $\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$ 

**Base**: n = 1:  $1 = \frac{1 \cdot 2}{2} = 1$ 

**Passo**: Assumindo para k, provar para k + 1:  $\sum_{i=1}^{k+1} i = \frac{k(k+1)}{2} + (k+1) = \frac{(k+1)(k+2)}{2} \checkmark$ 

#### Conjunto Contável

Professor

Um conjunto A é **contável** (ou enumerável) se existe uma bijeção  $f: \mathbb{N} \to A$ , ou seja, seus elementos podem ser "listados":  $a_0, a_1, a_2, \ldots$ 

#### Exemplos de Conjuntos Contáveis

- N por definição
- $\mathbb{Z}$  enumere: 0, 1, -1, 2, -2, 3, -3, ...
- Q argumento diagonal (próxima aula)
- Conjunto de todas as strings finitas sobre alfabeto finito

#### Pergunta

 $E \mathbb{R}$ ? É contável?

#### Conceitos Fundamentais

- Conjuntos, elementos, subconjuntos
- Operações:  $\cup$ ,  $\cap$ , -,  $\times$ ,  $\mathcal{P}$
- Cardinalidade e bijeções
- Funções: injetora, sobrejetora, bijetora
- Relações e equivalência
- Princípio da indução
- Conjuntos contáveis

#### Próxima Aula

Argumento da Diagonalização de Cantor: provando que  $\mathbb R$  é incontável

## Exercício 1: Operações com Conjuntos

Dados  $A = \{1, 2, 3, 4\}$  e  $B = \{3, 4, 5, 6\}$ , determine:

- **1** *A* $\cup$ *B*
- $2 A \cap B$
- 3 A B
- $\mathbf{a} B A$
- **5**  $A \times B$  (apenas os pares onde ambos são ímpares)
- 6  $|\mathcal{P}(A \cap B)|$

![](_page_18_Picture_12.jpeg)

## Exercício 2: Funções

Para cada função abaixo, determine se é injetora, sobrejetora, ou bijetora:

**1** 
$$f: \mathbb{N} \to \mathbb{N}$$
,  $f(n) = n+1$ 

2 
$$g: \mathbb{Z} \to \mathbb{Z}$$
,  $g(n) = n+1$ 

$$h: \mathbb{N} \to \mathbb{N}, \ h(n) = n^2$$

$$g: \mathbb{N} \to \mathbb{N}, \ q(n) = \lfloor n/2 \rfloor$$

![](content/images/aula-01-apresentação-da-disciplina-revisão-de-teoria-de-conjuntos-e-enumerabilidade-_page_19_Picture_12.png)

Prove por indução matemática:

- $\sum_{i=1}^{n} i^2 = \frac{n(n+1)(2n+1)}{6}$
- $\sum_{i=0}^{n} 2^{i} = 2^{n+1} 1$
- Para todo n > 1:  $n^3 n$  é divisível por 3
- Para todo n > 4:  $2^n > n^2$

![](content/images/aula-01-apresentação-da-disciplina-revisão-de-teoria-de-conjuntos-e-enumerabilidade-_page_20_Picture_11.png)

## Exercício 4: Cardinalidade

Professor

- Mostre que  $|\mathbb{N}| = |\mathbb{N} \{0\}|$  (dica: encontre uma bijeção)
- 2 Mostre que  $|\mathbb{N}| = |\{n \in \mathbb{N} \mid n \text{ é par}\}|$
- 3 Se |A| = n, quantos subconjuntos de A têm exatamente k elementos?
- **Desafio**: Mostre que  $|\mathbb{N} \times \mathbb{N}| = |\mathbb{N}|$  (dica: use a função de pareamento de Cantor)

## Exercício 5: Relações

Professor

Seja R uma relação sobre  $\mathbb{Z}$  definida por:  $aRb \iff a-b$  é par.

- 11 Prove que R é uma relação de equivalência
- 2 Quais são as classes de equivalência de R?
- 3 Quantas classes de equivalência existem?

Seja S uma relação sobre  $\mathbb{N}$  definida por:  $aSb \iff a \mid b$  (a divide b).

- 4 S é reflexiva? Simétrica? Transitiva? Antissimétrica?
- S é uma relação de equivalência? É uma ordem parcial?

## Reflexão

#### Paradoxo de Russell

Considere o conjunto  $R = \{x \mid x \notin x\}$ , ou seja, o conjunto de todos os conjuntos que não pertencem a si mesmos.

**Pergunta**:  $R \in R$ ?

- Se  $R \in R$ , então pela definição,  $R \notin R$ . Contradição!
- Se  $R \notin R$ , então pela definição,  $R \in R$ . Contradição!

#### Limitações da Teoria de Conjuntos Ingênua

Este paradoxo mostra que "o conjunto de todos os conjuntos" não pode existir na teoria de conjuntos ingênua. A teoria axiomática de Zermelo-Fraenkel (ZF) resolve isso restringindo quais conjuntos podem ser construídos. **Não confundir com ZFC, que inclui o axioma da escolha.**<sup>5</sup>

<sup>&</sup>lt;sup>5</sup>https://plato.stanford.edu/entries/axiom-choice/

## [1] Sanjeev Arora e Boaz Barak. Computational Complexity: A

- Modern Approach. Cambridge University Press, 2009.[2] Ralph P. Grimaldi. Discrete and Combinatorial Mathematics:
- [3] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. Introduction to Automata Theory, Languages, and Computation. 3rd. Pearson, 2006.

An Applied Introduction. 5th. Pearson, 2004.

- [4] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [5] Kenneth H. Rosen. Discrete Mathematics and Its Applications. 8th. McGraw-Hill, 2019.

## Referências II

- [6] Michael Sipser. Introduction to the Theory of Computation.3rd. Cengage Learning, 2012.
- [7] Daniel J. Velleman. *How to Prove It: A Structured Approach*. 2nd. Cambridge University Press, 2006.

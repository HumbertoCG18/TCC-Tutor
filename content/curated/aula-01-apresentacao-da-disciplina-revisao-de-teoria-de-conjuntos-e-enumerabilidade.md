<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
  - Prof. Anderson R. P. Domingues
- **Regras de Convivência**
- **Teoria da Computabilidade e Complexidade**
- **Questões Fundamentais**
- **Ementa**
- **Bibliografia**
  - Bibliografia da Disciplina, livros principais
- **Recomendação**
- **Por que estudar Teoria da Computação?**
  - Importante
- **Conjuntos: Definições Básicas**
  - Conjunto
  - Conjuntos Importantes
- **Relações entre Conjuntos**
  - Subconjunto
  - Igualdade
  - Subconjunto Próprio
- **Operações com Conjuntos**
  - União
  - Interseção
  - Diferença
  - Complemento
  - Produto Cartesiano
  - Conjunto Potência
  - Cardinalidade
  - Definição
  - Para Conjuntos Infinitos
  - Questão Central
- **Funções**
  - Definição
  - Tipos de Funções
- **Relações**
  - Definição
  - Propriedades de Relações
  - Relações de Equivalência e Ordem
  - Princípio da Indução
  - Indução Matemática
  - Indução Forte vs. Fraca
- **Conjuntos Contáveis e Incontáveis**
  - Conjunto Contável
  - Pergunta
- **Resumo**
- **Conceitos Fundamentais**
- **Próxima Aula**
  - Exercício 1: Operações com Conjuntos
  - Exercício 2: Funções
  - Exercício 3: Indução
  - Exercício 4: Cardinalidade
  - Exercício 5: Relações
  - Reflexão
  - Paradoxo de Russell
- **Limitações da Teoria de Conjuntos Ingênua**
- **Referências I**
- **Referências II**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Apresentação da Disciplina e Revisão de Teoria de Conjuntos

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 01

Teoria da Computabilidade e Complexidade  
Ciência da Computação

23 de fevereiro de 2026

The logo of PUCRS, featuring a shield with a cross and a star, and the text 'PUCRS' below it.

Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

{1}------------------------------------------------
## Sumário

**1** Professor

**2** Disciplina

**3** Teoria de Conjuntos

**4** Exercícios

The image is a large, light gray watermark of the Coat of Arms of the University of São Paulo (USP). It features a central shield with a vertical band containing a monogram, flanked by two vertical panels with a pine tree pattern. Above the shield is a crown and two crossed keys. A banner at the bottom reads 'AD VERVM DVCIT'.

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
### Prof. Anderson R. P. Domingues

- Lattes: <http://lattes.cnpq.br/5879502837295804>
- Professor Adjunto, PUCRS
  - Pesquisador
    - LSA - Laboratório de Sistemas Autônomos, Robótica:  
<https://lsa-pucrs.github.io/>
    - GAPH - Grupo de Apoio ao Projeto de Hardware, SESD<sup>1</sup>:  
<https://gaph-pucrs.github.io/>
  - Comissão Coordenadora de Curso (CCC-ECó)
  - Disciplinas (2026-1):
    - Introdução à Programação — ECó
    - Algoritmos e Estruturas de Dados I — ECó
    - Sistemas Digitais
    - Confiabilidade e Segurança de Hardware
    - Teoria da Computabilidade e Complexidade
    - Trabalho de Conclusão de Curso I e II (CC)
- Contato: [anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br) ou via Moodle

<sup>1</sup>Sistemas Embarcados e Sistemas Digitais

{3}------------------------------------------------
## Regras de Convivência

- Pontualidade: a chamada será realizada a cada início de período. Não comparecer em ao menos 75% das aulas acarretará em **reprovação imediata**;
- Conduta: Seja respeitoso e cortês, não produza ruídos desnecessários durante as aulas; peça a palavra antes de falar;
- Ambiente Moodle<sup>2</sup>:
  - Cronograma, plano de ensino e material;
  - SARC: <https://sarc.pucrs.br>
  - Todos os trabalhos serão entregues via Moodle; trabalhos enviados por e-mail serão solenemente ignorados
  - Não há tolerância para atrasos nas entregas de trabalhos;
  - É dever do aluno consultar o moodle periodicamente;
- Honestidade acadêmica: Plágio é **crime**<sup>3</sup>!

---

<sup>2</sup><https://moodle.pucrs.br/>

<sup>3</sup>[https://www.planalto.gov.br/ccivil\\_03/leis/2003/l110.695.htm](https://www.planalto.gov.br/ccivil_03/leis/2003/l110.695.htm)

{4}------------------------------------------------
## Teoria da Computabilidade e Complexidade

- **Objetivo:** Estudar os limites fundamentais da computação
- O que pode ser computado? (Computabilidade)
- Quão eficientemente pode ser computado? (Complexidade)

<!-- IMAGE_DESCRIPTION: datalab-c036e2540a94b31357ceb0002f0cacab_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da hierarquia das linguagens de Chomsky, mostrando cinco níveis concêntricos de complexidade crescente.
<!-- /IMAGE_DESCRIPTION -->
## Questões Fundamentais

- Existem problemas que **nenhum** computador pode resolver?
- Por que alguns problemas são mais difíceis que outros?
- Como classificar problemas por *dificuldade*?

{5}------------------------------------------------
## Ementa

- **Parte I: Fundamentos**
  - Teoria de Conjuntos e Cardinalidade
  - Funções Recursivas e Computabilidade
- **Parte II: Computabilidade**
  - Máquinas de Turing
  - Linguagens Decidíveis e Reconhecíveis
  - Problemas Indecidíveis (Halting Problem, etc.)
- **Parte III: Complexidade**
  - Classes P e NP
  - NP-Completeness e Reduções
  - PSPACE e além

The image is a large, light gray watermark of the coat of arms of the University of São Paulo (USP). It features a central shield with a large five-pointed star at the bottom. The shield is flanked by two crossed keys (the keys of St. Peter) and topped by a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{6}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-875c6f4f441fdd3ca7e1908fd1582983_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da Hierarquia de Chomsky mostrando a inclusão entre classes de linguagens.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-fb15f15a7d964c8490c9317e43e40c1a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
## Bibliografia
### Bibliografia da Disciplina, livros principais

- SIPSER, M. *Introduction to the Theory of Computation*. 2nd ed. Cengage, 2012.
- PAPADIMITRIOU, C. *Computational Complexity*. Addison-Wesley, 1994.
## Recomendação

- ROSEN, KENNETH H., *Discrete Mathematics Applications*. 8th ed. McGraw-Hill, 2019.
- <sup>4</sup>HOPCROFT, J.; MOTWANI, R.; ULLMAN, J. *Introduction to Automata Theory, Languages, and Computation*. 3rd ed. Pearson, 2006.

<sup>4</sup>Disciplina de Ling. Formais e Autônomatos

{7}------------------------------------------------
## Por que estudar Teoria da Computação?

- Entender os **limites fundamentais** da computação
- Reconhecer problemas **intratáveis** antes de tentar resolvê-los
- Base teórica para:
  - Criptografia (problemas difíceis  $\Rightarrow$  segurança)
  - Otimização (saber quando usar heurísticas)
  - Inteligência Artificial (limites do que pode ser aprendido)
  - Verificação de Software (decidibilidade de propriedades)
### Importante

Esta disciplina é **teórica** e **matemática**. Requer familiaridade com provas formais, indução, e raciocínio abstrato.

{8}------------------------------------------------
## Conjuntos: Definições Básicas
### Conjunto

Coleção de objetos distintos, chamados **elementos** ou **membros**.

- Notação:  $a \in A$  significa “ $a$  pertence ao conjunto  $A$ ”
- $a \notin A$  significa “ $a$  não pertence a  $A$ ”
- Conjuntos podem ser definidos por:
  - **Enumeração:**  $A = \{1, 2, 3, 4, 5\}$
  - **Compreensão:**  $A = \{x \in \mathbb{Z} \mid x > 0 \wedge x \leq 5\}$
### Conjuntos Importantes

- $\mathbb{N} = \{0, 1, 2, 3, \dots\}$  — Números naturais
- $\mathbb{Z} = \{\dots, -2, -1, 0, 1, 2, \dots\}$  — Números inteiros
- $\mathbb{Q}$  — Números racionais
- $\mathbb{R}$  — Números reais

{9}------------------------------------------------
## Relações entre Conjuntos
### Subconjunto

$A \subseteq B$  se todo elemento de  $A$  também está em  $B$ :

$$A \subseteq B \iff \forall x(x \in A \Rightarrow x \in B)$$
### Igualdade

$A = B$  se  $A \subseteq B$  e  $B \subseteq A$
### Subconjunto Próprio

$A \subset B$  se  $A \subseteq B$  e  $A \neq B$
#### Exemplos

- $\{1, 2\} \subseteq \{1, 2, 3\}$  ✓
- $\mathbb{N} \subset \mathbb{Z} \subset \mathbb{Q} \subset \mathbb{R}$
- $\emptyset \subseteq A$  para qualquer conjunto  $A$

{10}------------------------------------------------
## Operações com Conjuntos
### União

$$A \cup B = \{x \mid x \in A \vee x \in B\}$$
### Interseção

$$A \cap B = \{x \mid x \in A \wedge x \in B\}$$
### Diferença

$$A - B = \{x \mid x \in A \wedge x \notin B\}$$
### Complemento

$\bar{A} = U - A$  (em relação ao universo  $U$ )
### Produto Cartesiano

$$A \times B = \{(a, b) \mid a \in A \wedge b \in B\}$$
### Conjunto Potência

$$\mathcal{P}(A) = \{B \mid B \subseteq A\}$$

{11}------------------------------------------------
### Cardinalidade
### Definição

A **cardinalidade** de um conjunto  $A$ , denotada  $|A|$ , é o “número de elementos” de  $A$ .

- $|\{a, b, c\}| = 3$
- $|\emptyset| = 0$
- $|\mathcal{P}(A)| = 2^{|A|}$  para conjuntos finitos
### Para Conjuntos Infinitos

A cardinalidade é definida via **bijeções**:

$$|A| = |B| \iff \exists f : A \rightarrow B \text{ bijetora}$$
### Questão Central

Todos os conjuntos infinitos têm o “mesmo tamanho”?

{12}------------------------------------------------
## Funções
### Definição

Uma **função**  $f : A \rightarrow B$  associa cada elemento de  $A$  (domínio) a exatamente um elemento de  $B$  (contradomínio).

**Cuidado: contradomínio é diferente de imagem!**
### Tipos de Funções

- **Injetora:**  $f(a_1) = f(a_2) \Rightarrow a_1 = a_2$
- **Sobrejetora:**  $\forall b \in B, \exists a \in A : f(a) = b$
- **Bijetora:** Injetora e sobrejetora; **admite inversa**  $f^{-1} : B \rightarrow A$

Injetora

Diagram of an injective function (one-to-one). Set A has 3 elements and set B has 4 elements. Each element in A is mapped to a unique element in B, but one element in B is not mapped to by any element in A.

Sobrejetora

Diagram of a surjective function (onto). Set A has 5 elements and set B has 4 elements. Every element in B is mapped to by at least one element in A. One element in A is not mapped to any element in B.

Bijetora

Diagram of a bijective function (one-to-one and onto). Set A has 4 elements and set B has 4 elements. Every element in A is mapped to a unique element in B, and every element in B is mapped to by exactly one element in A.

{13}------------------------------------------------
## Relações
### Definição

Uma **relação**  $R$  sobre  $A$  é um subconjunto de  $A \times A$ . Escrevemos  $aRb$  ou  $(a, b) \in R$ .
### Propriedades de Relações

- **Reflexiva:**  $\forall a \in A : aRa$ , **exemplo:**  $=$
- **Simétrica:**  $aRb \Rightarrow bRa$ , **exemplo:**  $\neq$
- **Transitiva:**  $aRb \wedge bRc \Rightarrow aRc$ , **exemplo:**  $\leq$
- **Antissimétrica:**  $aRb \wedge bRa \Rightarrow a = b$ , **exemplo:**  $\leq$

{14}------------------------------------------------
### Relações de Equivalência e Ordem
#### Relação de Equivalência

- É uma relação que é reflexiva, simétrica e transitiva
- Particiona o conjunto em **classes de equivalência**.
#### Relação de Ordem

- É uma relação que é reflexiva, antissimétrica e transitiva
- Particiona o conjunto em **classes de ordem**.
- Pode ser parcial (ex.  $\subseteq$ ) ou total (ex.  $\leq$ ), ou total (ex.  $\leq$ ) se para todo  $a, b$ ,  $a \leq b$  ou  $b \leq a$ .

{15}------------------------------------------------
### Princípio da Indução
### Indução Matemática

Para provar  $P(n)$  para todo  $n \geq n_0$ :

- 1 Base:** Provar  $P(n_0)$
- 2 Passo Indutivo:** Provar que  $P(k) \Rightarrow P(k + 1)$
### Indução Forte vs. Fraca

- **Indução Fraca:**  $P(k) \Rightarrow P(k + 1)$
- **Indução Forte:**  $(P(n_0) \wedge P(n_0 + 1) \wedge \dots \wedge P(k)) \Rightarrow P(k + 1)$
#### Exemplo: Soma dos primeiros $n$ naturais

**Provar:**  $\sum_{i=1}^n i = \frac{n(n+1)}{2}$

**Base:**  $n = 1$ :  $1 = \frac{1 \cdot 2}{2} = 1 \checkmark$

**Passo:** Assumindo para  $k$ , provar para  $k + 1$ :

$$\sum_{i=1}^{k+1} i = \frac{k(k+1)}{2} + (k + 1) = \frac{(k+1)(k+2)}{2} \checkmark$$

{16}------------------------------------------------
## Conjuntos Contáveis e Incontáveis
### Conjunto Contável

Um conjunto  $A$  é **contável** (ou enumerável) se existe uma bijeção  $f : \mathbb{N} \rightarrow A$ , ou seja, seus elementos podem ser “listados”:

$a_0, a_1, a_2, \dots$
#### Exemplos de Conjuntos Contáveis

- $\mathbb{N}$  — por definição
- $\mathbb{Z}$  — enumere:  $0, 1, -1, 2, -2, 3, -3, \dots$
- $\mathbb{Q}$  — **argumento diagonal** (próxima aula)
- Conjunto de todas as strings finitas sobre alfabeto finito
### Pergunta

E  $\mathbb{R}$ ? É contável?

{17}------------------------------------------------
## Resumo
## Conceitos Fundamentais

- Conjuntos, elementos, subconjuntos
- Operações:  $\cup$ ,  $\cap$ ,  $-$ ,  $\times$ ,  $\mathcal{P}$
- Cardinalidade e bijeções
- Funções: injetora, sobrejetora, bijetora
- Relações e equivalência
- Princípio da indução
- Conjuntos contáveis
## Próxima Aula

Argumento da Diagonalização de Cantor: provando que  $\mathbb{R}$  é **incontável**.

{18}------------------------------------------------
### Exercício 1: Operações com Conjuntos

Dados  $A = \{1, 2, 3, 4\}$  e  $B = \{3, 4, 5, 6\}$ , determine:

**1**  $A \cup B$

**2**  $A \cap B$

**3**  $A - B$

**4**  $B - A$

**5**  $A \times B$  (apenas os pares onde ambos são ímpares)

**6**  $|\mathcal{P}(A \cap B)|$

The image is a large, faint watermark of the coat of arms of the University of São Paulo (USP) on the right side of the slide. It features a shield with a central vertical band containing a stylized 'M' and 'U' monogram, flanked by two vertical bands with a repeating cross pattern. Above the shield is a crown, and below it is a ribbon with the motto 'AD VERVM DVCIT'.

Coat of arms of the University of São Paulo (USP)

{19}------------------------------------------------
### Exercício 2: Funções

Para cada função abaixo, determine se é injetora, sobrejetora, ou bijetora:

**1**  $f : \mathbb{N} \rightarrow \mathbb{N}, f(n) = n + 1$

**2**  $g : \mathbb{Z} \rightarrow \mathbb{Z}, g(n) = n + 1$

**3**  $h : \mathbb{N} \rightarrow \mathbb{N}, h(n) = n^2$

**4**  $p : \mathbb{Z} \rightarrow \mathbb{N}, p(n) = |n|$

**5**  $q : \mathbb{N} \rightarrow \mathbb{N}, q(n) = \lfloor n/2 \rfloor$

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central vertical band containing a stylized 'M' and 'U' monogram. The shield is flanked by two crossed keys (the keys of St. Peter) and topped by a crown. A banner at the bottom of the shield reads 'AD VERVM DVCIT'.

Coat of arms of the University of São Paulo (USP)

{20}------------------------------------------------
### Exercício 3: Indução

Prove por indução matemática:

1  $\sum_{i=1}^n i^2 = \frac{n(n+1)(2n+1)}{6}$

2  $\sum_{i=0}^n 2^i = 2^{n+1} - 1$

3 Para todo  $n \geq 1$ :  $n^3 - n$  é divisível por 3

4 Para todo  $n \geq 4$ :  $2^n > n^2$

The image is a large, light gray watermark of the coat of arms of the University of São Paulo (USP). It features a central shield with a large five-pointed star at the bottom. The shield is flanked by two crossed keys (the keys of St. Peter) and topped by a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{21}------------------------------------------------
### Exercício 4: Cardinalidade

- 1 Mostre que  $|\mathbb{N}| = |\mathbb{N} - \{0\}|$  (dica: encontre uma bijeção)
- 2 Mostre que  $|\mathbb{N}| = |\{n \in \mathbb{N} \mid n \text{ é par}\}|$
- 3 Se  $|A| = n$ , quantos subconjuntos de  $A$  têm exatamente  $k$  elementos?
- 4 **Desafio:** Mostre que  $|\mathbb{N} \times \mathbb{N}| = |\mathbb{N}|$  (dica: use a função de pareamento de Cantor)

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a large five-pointed star in the center. The shield is flanked by two crossed flags. Above the shield is a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{22}------------------------------------------------
### Exercício 5: Relações

Seja  $R$  uma relação sobre  $\mathbb{Z}$  definida por:  $aRb \iff a - b$  é par.

- 1** Prove que  $R$  é uma relação de equivalência
- 2** Quais são as classes de equivalência de  $R$ ?
- 3** Quantas classes de equivalência existem?

Seja  $S$  uma relação sobre  $\mathbb{N}$  definida por:  $aSb \iff a \mid b$  ( $a$  divide  $b$ ).

- 4**  $S$  é reflexiva? Simétrica? Transitiva? Antissimétrica?
- 5**  $S$  é uma relação de equivalência? É uma ordem parcial?

{23}------------------------------------------------
### Reflexão
### Paradoxo de Russell

Considere o conjunto  $R = \{x \mid x \notin x\}$ , ou seja, o conjunto de todos os conjuntos que não pertencem a si mesmos.

**Pergunta:**  $R \in R$ ?

- Se  $R \in R$ , então pela definição,  $R \notin R$ . Contradição!
- Se  $R \notin R$ , então pela definição,  $R \in R$ . Contradição!
## Limitações da Teoria de Conjuntos Ingênua

Este paradoxo mostra que “o conjunto de todos os conjuntos” não pode existir na teoria de conjuntos ingênua. A teoria axiomática de Zermelo-Fraenkel (ZF) resolve isso restringindo quais conjuntos podem ser construídos. **Não confundir com ZFC, que inclui o axioma da escolha.**<sup>5</sup>

<sup>5</sup><https://plato.stanford.edu/entries/axiom-choice/>

{24}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] Ralph P. Grimaldi. *Discrete and Combinatorial Mathematics: An Applied Introduction*. 5th. Pearson, 2004.
- [3] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [4] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [5] Kenneth H. Rosen. *Discrete Mathematics and Its Applications*. 8th. McGraw-Hill, 2019.

{25}------------------------------------------------
## Referências II

- [6] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.
- [7] Daniel J. Velleman. *How to Prove It: A Structured Approach*. 2nd. Cambridge University Press, 2006.

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central vertical band containing a stylized 'M' and 'U' monogram. The shield is flanked by two crossed keys (the keys of St. Peter) and topped by a crown. A banner at the bottom of the shield contains the Latin motto 'AD VERVM DVCT'.

Coat of arms of the University of São Paulo (USP)

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-29f586959675cafdf81cf934954908eb_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a Deterministic Finite Automaton (DFA) with three states: q0, q1, and q2.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-86b4670fc1a5a694821ee92b99c1209a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a Pushdown Automaton (PDA) for the language {0^n 1^n : n ≥ 0}.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-fa6c61be003dfbb4ca5587e48a71de94_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
  - Prof. Anderson R. P. Domingues
- **Regras de Convivência**
- **Teoria da Computabilidade e Complexidade**
- **Questões Fundamentais**
  - Ementa
  - ■ Parte I: Fundamentos
  - ■ Parte II: Computabilidade
  - ■ Parte III: Complexidade
- **Bibliografia**
  - Bibliografia da Disciplina, livros principais
- **Recomendação**
  - Por que estudar Teoria da Computação?
  - Importante
- **Conjuntos: Definições Básicas**
  - Conjunto
  - Conjuntos Importantes
  - Relações entre Conjuntos
  - Operações com Conjuntos
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
  - Funções
  - Definição
  - Tipos de Funções
  - Relações
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

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Apresentação da Disciplina e Revisão de Teoria de Conjuntos

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 01  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

23 de fevereiro de 2026

The logo of the PUCRS Escola Politécnica. It features a crest with a shield, a cross, and a sun, with the text "PUCRS" below it. To the right of the crest, the words "ESCOLA" and "POLITÉCNICA" are stacked vertically in a bold, blue, sans-serif font.

Logo of PUCRS Escola Politécnica

{1}------------------------------------------------
## Sumário

**1** Professor

**2** Disciplina

**3** Teoria de Conjuntos

**4** Exercícios

A faint, gray watermark of the coat of arms of the University of Coimbra is visible on the right side of the slide. The shield features a central star and is flanked by two sections with a repeating pattern of stylized trees. Above the shield is a crown and two crossed keys. A ribbon at the bottom bears the Latin motto 'AD VERVM DVKIT'.

Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVKIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-1211e36d120f0d2912a745437f4c8f19_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVKIT'.
<!-- /IMAGE_DESCRIPTION -->
### Prof. Anderson R. P. Domingues

- Lattes: <http://lattes.cnpq.br/5879502837295804>
- Professor Adjunto, PUCRS
  - Pesquisador
    - LSA - Laboratório de Sistemas Autônomos, Robótica:  
<https://lsa-pucrs.github.io/>
    - GAPH - Grupo de Apoio ao Projeto de Hardware, SESD<sup>1</sup>:  
<https://gaph-pucrs.github.io/>
  - Comissão Coordenadora de Curso (CCC-ECo)
  - Disciplinas (2026-1):
    - Introdução à Programação — ECo
    - Algoritmos e Estruturas de Dados I — ECo
    - Sistemas Digitais
    - Confiabilidade e Segurança de Hardware
    - Teoria da Computabilidade e Complexidade
    - Trabalho de Conclusão de Curso I e II (CC)
- Contato: [anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br) ou via Moodle

<sup>1</sup>Sistemas Embarcados e Sistemas Digitais

{3}------------------------------------------------
## Regras de Convivência

- Pontualidade: a chamada será realizada a cada início de período. Não comparecer em ao menos 75% das aulas acarretará em **reprovação imediata**;
- Conduta: Seja respeituoso e cortês, não produza ruídos desnecessários durante as aulas; peça a palavra antes de falar;
- Ambiente Moodle<sup>2</sup>:
  - Cronograma, plano de ensino e material;
  - SARC: <https://sarc.pucrs.br>
  - Todos os trabalhos serão entregues via Moodle; trabalhos enviados por e-mail serão solenemente ignorados
  - Não há tolerância para atrasos nas entregas de trabalhos;
  - É dever do aluno consultar o moodle periodicamente;
- Honestidade acadêmica: Plágio é **crime**<sup>3</sup>!

---

<sup>2</sup><https://moodle.pucrs.br/>

<sup>3</sup>[https://www.planalto.gov.br/ccivil\\_03/leis/2003/110.695.htm](https://www.planalto.gov.br/ccivil_03/leis/2003/110.695.htm)

{4}------------------------------------------------
## Teoria da Computabilidade e Complexidade

- **Objetivo:** Estudar os limites fundamentais da computação
- O que pode ser computado? (Computabilidade)
- Quão eficientemente pode ser computado? (Complexidade)
## Questões Fundamentais

- Existem problemas que **nenhum** computador pode resolver?
- Por que alguns problemas são mais difíceis que outros?
- Como classificar problemas por *dificuldade*?

{5}------------------------------------------------
### Ementa
### ■ Parte I: Fundamentos

- Teoria de Conjuntos e Cardinalidade
- Funções Recursivas e Computabilidade
### ■ Parte II: Computabilidade

- Máquinas de Turing
- Linguagens Decidíveis e Reconhecíveis
- Problemas Indecidíveis (Halting Problem, etc.)
### ■ Parte III: Complexidade

- Classes P e NP
- NP-Complete e Reduções
- PSPACE e além

A faint, stylized illustration of a coat of arms featuring a crown, a shield with a star and the initials 'MAC', and a banner with the Latin motto 'AD VERVM DVCT'.

{6}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-aa541b61e0c277c9c5b40e0936168cec_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A faint, stylized illustration of a coat of arms featuring a crown, a shield with a star and the initials 'MAC', and a banner with the Latin motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
## Bibliografia
### Bibliografia da Disciplina, livros principais

- SIPSER, M. *Introduction to the Theory of Computation*. 2nd ed. Cengage, 2012.
- PAPADIMITRIOU, C. *Computational Complexity*. Addison-Wesley, 1994.
## Recomendação

- ROSEN, KENNETH H., *Discrete Mathematics Applications*. 8th ed. McGraw-Hill, 2019.
- <sup>4</sup>HOPCROFT, J.; MOTWANI, R.; ULLMAN, J. *Introduction to Automata Theory, Languages, and Computation*. 3rd ed. Pearson, 2006.

<sup>4</sup>Disciplina de Ling. Formais e Autômatos

{7}------------------------------------------------
### Por que estudar Teoria da Computação?

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
### Relações entre Conjuntos
#### Subconjunto

$A \subseteq B$  se todo elemento de  $A$  também está em  $B$ :

$$A \subseteq B \iff \forall x(x \in A \Rightarrow x \in B)$$
#### Igualdade

$A = B$  se  $A \subseteq B$  e  $B \subseteq A$
#### Subconjunto Próprio

$A \subset B$  se  $A \subseteq B$  e  $A \neq B$
#### Exemplos

- $\{1, 2\} \subseteq \{1, 2, 3\}$  ✓
- $\mathbb{N} \subset \mathbb{Z} \subset \mathbb{Q} \subset \mathbb{R}$
- $\emptyset \subseteq A$  para qualquer conjunto  $A$

{10}------------------------------------------------
### Operações com Conjuntos
### União

$$A \cup B = \{x \mid x \in A \vee x \in B\}$$
### Interseção

$$A \cap B = \{x \mid x \in A \wedge x \in B\}$$
### Diferença

$$A - B = \{x \mid x \in A \wedge x \notin B\}$$
### Complemento

$$\bar{A} = U - A \text{ (em relação ao universo } U\text{)}$$
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
### Funções
### Definição

Uma **função**  $f : A \rightarrow B$  associa cada elemento de  $A$  (domínio) a exatamente um elemento de  $B$  (contradomínio).

**Cuidado: contradomínio é diferente de imagem!**
### Tipos de Funções

- **Injetora:**  $f(a_1) = f(a_2) \Rightarrow a_1 = a_2$
- **Sobrejetora:**  $\forall b \in B, \exists a \in A : f(a) = b$
- **Bijetora:** Injetora e sobrejetora; **admite inversa**  $f^{-1} : B \rightarrow A$

Injetora

Diagrama de uma função injetora. O domínio A tem 4 elementos e o contradomínio B tem 5 elementos. Cada elemento de A é mapeado para um elemento único de B, deixando um elemento de B sem imagem.

Sobrejetora

Diagrama de uma função sobrejetora. O domínio A tem 4 elementos e o contradomínio B tem 3 elementos. Cada elemento de B tem pelo menos um elemento de A mapeado para ele, mas alguns elementos de B têm mais de um elemento de A mapeado para eles.

Bijetora

Diagrama de uma função bijetora. O domínio A tem 3 elementos e o contradomínio B tem 3 elementos. Cada elemento de A é mapeado para um elemento único de B, e cada elemento de B tem exatamente um elemento de A mapeado para ele.

{13}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-5dfc130b129ace4df375839020a5700d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de uma função injetora. O domínio A tem 4 elementos e o contradomínio B tem 5 elementos. Cada elemento de A é mapeado para um elemento único de B, deixando um elemento de B sem imagem.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-3376375fe7236a570fd0ee9448d9c4ee_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de uma função sobrejetora. O domínio A tem 4 elementos e o contradomínio B tem 3 elementos. Cada elemento de B tem pelo menos um elemento de A mapeado para ele, mas alguns elementos de B têm mais de um...
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-ea37ab05b033e59cfdf7b074161aaf5a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de uma função bijetora. O domínio A tem 3 elementos e o contradomínio B tem 3 elementos. Cada elemento de A é mapeado para um elemento único de B, e cada elemento de B tem exatamente um elemento de A mapeado...
<!-- /IMAGE_DESCRIPTION -->
### Relações
#### Definição

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

- 1 **Base:** Provar  $P(n_0)$
- 2 **Passo Indutivo:** Provar que  $P(k) \Rightarrow P(k+1)$
### Indução Forte vs. Fraca

- **Indução Fraca:**  $P(k) \Rightarrow P(k+1)$
- **Indução Forte:**  $(P(n_0) \wedge P(n_0+1) \wedge \dots \wedge P(k)) \Rightarrow P(k+1)$
#### Exemplo: Soma dos primeiros $n$ naturais

**Provar:**  $\sum_{i=1}^n i = \frac{n(n+1)}{2}$

**Base:**  $n = 1$ :  $1 = \frac{1 \cdot 2}{2} = 1$  ✓

**Passo:** Assumindo para  $k$ , provar para  $k+1$ :

$\sum_{i=1}^{k+1} i = \frac{k(k+1)}{2} + (k+1) = \frac{(k+1)(k+2)}{2}$  ✓

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
- Operações:  $\cup, \cap, -, \times, \mathcal{P}$
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

- 1  $A \cup B$
- 2  $A \cap B$
- 3  $A - B$
- 4  $B - A$
- 5  $A \times B$  (apenas os pares onde ambos são ímpares)
- 6  $|\mathcal{P}(A \cap B)|$

The image is a watermark of the coat of arms of the University of Coimbra. It features a shield with a star and the motto 'AD VERVM DVICIT' (To truth, it leads). The shield is flanked by two figures, and the entire emblem is rendered in a light gray color.

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{19}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-0adfe2c1a73ed4d130777d83dd16321d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Funções

Para cada função abaixo, determine se é injetora, sobrejetora, ou bijetora:

1  $f : \mathbb{N} \rightarrow \mathbb{N}, f(n) = n + 1$

2  $g : \mathbb{Z} \rightarrow \mathbb{Z}, g(n) = n + 1$

3  $h : \mathbb{N} \rightarrow \mathbb{N}, h(n) = n^2$

4  $p : \mathbb{Z} \rightarrow \mathbb{N}, p(n) = |n|$

5  $q : \mathbb{N} \rightarrow \mathbb{N}, q(n) = \lfloor n/2 \rfloor$

A faint, stylized illustration of the coat of arms of the University of Coimbra. It features a shield with a central crest and two side panels decorated with small tree-like motifs. Above the shield is a crown and two crossed keys. A ribbon at the bottom bears the Latin motto 'AD VERVM DVICIT'.

{20}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-4cfefefc761d19fccc2f5ee84a57a895_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A faint, stylized illustration of the coat of arms of the University of Coimbra.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 3: Indução

Prove por indução matemática:

- 1  $\sum_{i=1}^n i^2 = \frac{n(n+1)(2n+1)}{6}$
- 2  $\sum_{i=0}^n 2^i = 2^{n+1} - 1$
- 3 Para todo  $n \geq 1$ :  $n^3 - n$  é divisível por 3
- 4 Para todo  $n \geq 4$ :  $2^n > n^2$

A large, faint watermark of the coat of arms of the University of Coimbra. It features a shield with a central crest and two side panels decorated with pine-like trees. Above the shield is a crown and two crossed keys. A ribbon at the bottom bears the Latin motto 'AD VERVM DVICIT'.

{21}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8c88a2b2e156c28098d47bdd093e67e0_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A large, faint watermark of the coat of arms of the University of Coimbra.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 4: Cardinalidade

- 1 Mostre que  $|\mathbb{N}| = |\mathbb{N} - \{0\}|$  (dica: encontre uma bijeção)
- 2 Mostre que  $|\mathbb{N}| = |\{n \in \mathbb{N} \mid n \text{ é par}\}|$
- 3 Se  $|A| = n$ , quantos subconjuntos de  $A$  têm exatamente  $k$  elementos?
- 4 **Desafio:** Mostre que  $|\mathbb{N} \times \mathbb{N}| = |\mathbb{N}|$  (dica: use a função de pareamento de Cantor)

A faint, stylized illustration of a coat of arms featuring a shield with a cross and a star, topped with a crown and flanked by two figures. Below the shield is a banner with the Latin motto 'AD VERVM DVICIT'.

{22}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-5756508641ee599941f6d1e85de7e84b_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A faint, stylized illustration of a coat of arms featuring a shield with a cross and a star, topped with a crown and flanked by two figures.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 5: Relações

Seja  $R$  uma relação sobre  $\mathbb{Z}$  definida por:  $aRb \iff a - b$  é par.

- 1 Prove que  $R$  é uma relação de equivalência
- 2 Quais são as classes de equivalência de  $R$ ?
- 3 Quantas classes de equivalência existem?

Seja  $S$  uma relação sobre  $\mathbb{N}$  definida por:  $aSb \iff a \mid b$  ( $a$  divide  $b$ ).

- 4  $S$  é reflexiva? Simétrica? Transitiva? Antissimétrica?
- 5  $S$  é uma relação de equivalência? É uma ordem parcial?

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

A faint, gray watermark of the University of Coimbra's coat of arms is visible on the right side of the slide. The shield features a central star and is flanked by two smaller shields with cross-like symbols. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT".

Faint watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

<!-- IMAGE_DESCRIPTION: datalab-513b2f88e0edcd2ffb6b7cf54f465d06_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-1d7527f4316cfe2d342b08d1653d1592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS Escola Politécnica
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

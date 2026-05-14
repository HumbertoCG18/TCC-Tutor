<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Contexto Histórico**
- **A Busca pelos Limites da Computação**
  - Importância
- **Sobre a Computabilidade**
  - Pergunta “Natural”
  - Importância
- **Recap: Máquinas de Turing**
  - Definição Formal
  - Comportamento
  - Linguagens e Decidibilidade
  - Linguagem de uma MT
  - Tipos de Linguagens
  - Codificação de Máquinas de Turing
  - Definição Formal
- **O Problema da Parada (Halting Problem)**
  - Linguagem Associada
  - Teorema (Turing, 1936)
  - Prova: Estrutura do Argumento
  - Método: Prova por Contradição + Diagonalização
  - Prova: Construção da Máquina $D$
  - Visualização: Argumento Diagonal
  - Analogia ao Paradoxo de Russell
  - Problema do Barbeiro
  - Conexão
- **HALT é Reconhecível, mas não Decidível**
  - HALT é Turing-Reconhecível
  - Problema
  - Hierarquia
  - O Complemento de *HALT*
  - Definição
  - Variações do Problema da Parada
  - Redução: Ferramenta para Provar Indecidibilidade
  - Exemplo: Problema da Aceitação
  - Exemplo: Problema da Linguagem Vazia
- **Implicações Práticas**
  - Verificação de Software
- **Exemplos Reais**
  - O Problema da Parada em Linguagens Reais
  - Programas Equivalentes a MTs
  - Exemplo em Python
  - Casos Especiais Decidíveis
  - Quando Podemos Decidir Terminação?
- **Exemplos**
- **Na Prática**
  - Exercício 1: Compreensão da Prova
  - Exercício 2: Variações do Problema da Parada
  - Exercício 3: Reconhecibilidade
  - Exercício 4: Reduções
  - Exercício 5: Aplicações Práticas
  - Exercício 6: Questões Conceituais
- **Desafio**
  - Teorema da Recursão
- **Reflexão**
- **Referências I**
- **Referências II**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Halting Problem - O Problema da Parada

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 11  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

15 de abril de 2026

The logo of the PUCRS Escola Politécnica. It features a crest with a shield and a star, with the text "PUCRS" below it. To the right of the crest, the words "ESCOLA" and "POLITÉCNICA" are stacked vertically in a blue sans-serif font.

Logo of PUCRS Escola Politécnica

A large, faint, gray watermark of the PUCRS seal is positioned on the right side of the slide. The seal is a circular emblem with a central shield and a banner at the bottom that reads "AD VERVM DVOCIT".

Faint background watermark of the PUCRS seal

{1}------------------------------------------------
## Sumário

**1** Introdução

**2** O Problema da Parada

**3** Consequências e Aplicações

**4** Exercícios

A faint, gray watermark of the coat of arms of the University of Coimbra is visible on the right side of the slide. The shield features a central star and is flanked by two sections with a repeating pattern of stylized trees. Above the shield is a crown and two crossed keys. A ribbon at the bottom bears the Latin motto 'AD VERVM DVKIT'.

Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVKIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-1211e36d120f0d2912a745437f4c8f19_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVKIT'.
<!-- /IMAGE_DESCRIPTION -->
## Contexto Histórico
## A Busca pelos Limites da Computação

No início do século XX, alguns matemáticos buscavam entender os **limites fundamentais** do que pode ou não ser computado.

- **1900:** David Hilbert propõe 23 problemas fundamentais
- **1928:** Hilbert e Ackermann formalizam o *Entscheidungsproblem*
- **1936:** Alan Turing publica “On Computable Numbers”
- **1936:** Turing demonstra que o Problema da Parada é **indecidível**
### Importância

O Problema da Parada é o primeiro e exemplo de problema **computacionalmente impossível**<sup>1</sup> de resolver.

<sup>1</sup>MTs

{3}------------------------------------------------
## Sobre a Computabilidade
### Pergunta “Natural”

Dado um programa  $P$  e uma entrada  $w$ , podemos determinar **algoritmicamente** se  $P$  irá:

- Eventualmente **parar** (terminar)?
- Ou executar **infinitamente\*** (entrar em loop)?
### Importância

- Verificação de software: garantir que programas terminam
- Compiladores: otimizações dependem de análise de terminação
- Depuração: detectar loops infinitos automaticamente (*linting*)

{4}------------------------------------------------
## Recap: Máquinas de Turing
### Definição Formal

Uma Máquina de Turing  $M$  é uma tupla  $(Q, \Sigma, \Gamma, \delta, q_0, q_{accept}, q_{reject})$ :

- $Q$ : conjunto finito de estados
- $\Sigma$ : alfabeto de entrada (não contém  $\sqcup$ )
- $\Gamma$ : alfabeto da fita ( $\Sigma \subseteq \Gamma$ ,  $\sqcup \in \Gamma$ )
- $\delta : Q \times \Gamma \rightarrow Q \times \Gamma \times \{L, R\}$
- $q_0, q_{accept}, q_{reject} \in Q$ : estados inicial, de aceitação e rejeição
### Comportamento

Para entrada  $w$ , a MT  $M$  pode:

- 1 **Aceitar:** entrar em  $q_{accept}$
- 2 **Rejeitar:** entrar em  $q_{reject}$
- 3 **Looping:** nunca parar

{5}------------------------------------------------
### Linguagens e Decidibilidade
### Linguagem de uma MT

$$L(M) = \{w \mid M \text{ aceita } w\}$$
### Tipos de Linguagens

Decidível (Recursiva): Existe MT  $M$  que **sempre para** e:

- Aceita se  $w \in L$
- Rejeita se  $w \notin L$

Reconhecível (Recursivamente Enumerável): Existe MT  $M$  que:

- Aceita se  $w \in L$
- Rejeita ou **loop** se  $w \notin L$
#### Pergunta

Existirá algum formalismo (máquina computante) que decide linguagens reconhecíveis?

{6}------------------------------------------------
### Codificação de Máquinas de Turing
#### Representação como String

Qualquer MT  $M$  pode ser codificada como uma string  $\langle M \rangle$  sobre um alfabeto fixo (ex:  $\{0, 1\}$ ).

- Estados: codificados como números binários
- Transições: lista de tuplas codificadas
- Símbolos: mapeados para sequências binárias
#### Consequência Importante

O conjunto de todas as MTs é **contável**:

$$|\{\text{todas as MTs}\}| = |\mathbb{N}|$$
#### Notação

Usaremos  $\langle M, w \rangle$  para denotar a codificação da MT  $M$  junto com a entrada  $w$ .

{7}------------------------------------------------
### Definição Formal
## O Problema da Parada (Halting Problem)

**Entrada:** Uma codificação  $\langle M, w \rangle$  de uma MT  $M$  e uma string  $w$ .  
**Pergunta:**  $M$  para quando executada com entrada  $w$ ?
### Linguagem Associada

$$HALT = \{ \langle M, w \rangle \mid M \text{ é uma MT que para com entrada } w \}$$
### Teorema (Turing, 1936)

$HALT$  é **indecidível**.

Não existe Máquina de Turing que sempre para e decide corretamente se uma MT arbitrária para com uma entrada arbitrária.

{8}------------------------------------------------
### Prova: Estrutura do Argumento
### Método: Prova por Contradição + Diagonalização

- 1 Assumir que existe uma MT  $H$  que decide *HALT*
- 2 Construir uma nova MT  $D$  usando  $H$
- 3 Mostrar que  $D$  leva a uma contradição
- 4 Concluir que  $H$  não pode existir

A diagram illustrating the hypothetical Turing machine  $H$ . On the left, the input  $\langle M, w \rangle$  is shown with an arrow pointing to a rectangular box labeled  $H$ . From the right side of the box, two arrows point to different outputs: the top arrow points to the text "aceita se  $M$  para em  $w$ ", and the bottom arrow points to the text "rejeita se  $M$  não para em  $w$ ".

Diagram showing the input and outputs of a hypothetical Turing machine H.

A MT hipotética  $H$  **sempre para** e responde corretamente.

{9}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-a234352dfaccdc24745c88eef7724cc6_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram showing the input and outputs of a hypothetical Turing machine H.
<!-- /IMAGE_DESCRIPTION -->
### Prova: Construção da Máquina $D$

<!-- IMAGE_DESCRIPTION: datalab-1eadbbe42cfcac5c0023577110aec5e3_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da máquina D
<!-- /IMAGE_DESCRIPTION -->
#### Definição de $D$

Usando  $H$ , construímos  $D$  que recebe  $\langle M \rangle$  como entrada:

- 1 Execute  $H$  com entrada  $\langle M, \langle M \rangle \rangle$
- 2 Se  $H$  aceita (i.e.,  $M$  para em  $\langle M \rangle$ ): entre em loop infinito
- 3 Se  $H$  rejeita (i.e.,  $M$  não para em  $\langle M \rangle$ ): aceite e pare

Diagrama da máquina  $D$ . Uma seta rotulada  $\langle M \rangle$  entra em um retângulo tracejado rotulado  $D$ . Dentro de  $D$  há um retângulo rotulado  $H$ . De  $H$ , duas setas saem para fora de  $D$ : uma rotulada "se aceita" apontando para "loop  $\infty$ ", e outra rotulada "se rejeita" apontando para "para".

Diagrama da máquina D
#### Comportamento de $D$

$D(\langle M \rangle)$  faz o **oposto** do que  $M$  faz quando recebe sua própria descrição.

{10}------------------------------------------------
#### Prova por Contradição
#### Onde está a contradição?

O que acontece quando executamos  $D$  com sua própria descrição?

$$D(\langle D \rangle) = ?$$
#### Possibilidades

**Caso 1:** Suponha que  $D(\langle D \rangle)$  **para**.

- Então  $H(\langle D, \langle D \rangle \rangle)$  rejeitou
- Isso significa que  $D$  **não para** em  $\langle D \rangle$
- **Contradição!**

**Caso 2:** Suponha que  $D(\langle D \rangle)$  **não para** (loop).

- Então  $H(\langle D, \langle D \rangle \rangle)$  aceitou
- Isso significa que  $D$  **para** em  $\langle D \rangle$
- **Contradição!**

{11}------------------------------------------------
### Visualização: Argumento Diagonal

|          | $\langle M_1 \rangle$ | $\langle M_2 \rangle$ | $\langle M_3 \rangle$ | $\langle M_4 \rangle$ | $\dots$  | $\langle D \rangle$ |
|----------|-----------------------|-----------------------|-----------------------|-----------------------|----------|---------------------|
| $M_1$    | P                     | N                     | P                     | P                     | $\dots$  | ?                   |
| $M_2$    | P                     | N                     | N                     | P                     | $\dots$  | ?                   |
| $M_3$    | N                     | P                     | P                     | N                     | $\dots$  | ?                   |
| $M_4$    | P                     | P                     | N                     | N                     | $\dots$  | ?                   |
| $\vdots$ | $\vdots$              | $\vdots$              | $\vdots$              | $\vdots$              | $\ddots$ | $\vdots$            |
| $D$      | N                     | P                     | N                     | P                     | $\dots$  | ?                   |

- P = Para, N = Não para
- $D$  é construída para **inverter a diagonal**
- Se  $M_i$  para em  $\langle M_i \rangle$ , então  $D$  não para em  $\langle M_i \rangle$
- A entrada  $\langle D \rangle$  para  $D$  gera a contradição

Faint watermark of the University of Coimbra crest featuring a crown, a shield with a star and the letters 'M', and the motto 'ALVERVM DVCTI'.

{12}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-a8a65eb4968947846b288d693535f03a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra crest featuring a crown, a shield with a star and the letters 'M', and the motto 'ALVERVM DVCTI'.
<!-- /IMAGE_DESCRIPTION -->
### Analogia ao Paradoxo de Russell
### Problema do Barbeiro

Em uma vila, o barbeiro barbeia todas as pessoas que não barbeiam a si mesmas, e apenas essas pessoas.

**Pergunta:** O barbeiro barbeia a si mesmo?

- Se ele barbeia a si mesmo  $\Rightarrow$  não deveria (pois só barbeia quem não se barbeia)
- Se ele não barbeia a si mesmo  $\Rightarrow$  deveria (pois barbeia todos que não se barbeiam)
### Conexão

A máquina  $D$  é como o “barbeiro”: ela é definida para fazer o oposto do que “deveria” fazer quando aplicada a si mesma.

{13}------------------------------------------------
## HALT é Reconhecível, mas não Decidível
### HALT é Turing-Reconhecível

Podemos construir uma MT  $R$  que **reconhece** *HALT*:

- 1 Entrada:  $\langle M, w \rangle$
- 2 Simule  $M$  em  $w$
- 3 Se  $M$  parar, aceite
### Problema

$R$  não **decide** *HALT*.
### Hierarquia

Diagrama de Venn illustrating the hierarchy of computational problems. A larger oval labeled "Reconhecíveis" (Recognizable) contains a smaller oval labeled "Decidíveis" (Decidable). The label "HALT" is placed within the larger oval but outside the smaller one, indicating that HALT is recognizable but not decidable.

Diagrama de Venn mostrando a hierarquia de problemas computacionais. Um oval maior rotulado 'Reconhecíveis' contém um oval menor rotulado 'Decidíveis'. A palavra 'HALT' está escrita dentro do oval maior, mas fora do oval menor, indicando que HALT é reconhecível mas não decidível.

{14}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-66c2bf11a8f117cddf67eff92d4c736c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de Venn mostrando a hierarquia de problemas computacionais.
<!-- /IMAGE_DESCRIPTION -->
### O Complemento de *HALT*
### Definição

$$\overline{HALT} = \{\langle M, w \rangle \mid M \text{ não para em } w\}$$
#### Teorema

$\overline{HALT}$  **não é** Turing-reconhecível.
#### Prova

Se tanto *HALT* quanto  $\overline{HALT}$  fossem reconhecíveis, então *HALT* seria decidível:

- Execute reconhecedores *HALT* e  $\overline{HALT}$  em paralelo
- Um deles eventualmente aceita; isso daria um decisor para *HALT*

Mas *HALT* não é decidível, então  $\overline{HALT}$  não pode ser reconhecível.

{15}------------------------------------------------
### Variações do Problema da Parada
#### Todas são Indecidíveis

- **Parada na entrada vazia:**

$$HALT_{\epsilon} = \{\langle M \rangle \mid M \text{ para em } \epsilon\}$$

- **Parada em todas as entradas:**

$$HALT_{all} = \{\langle M \rangle \mid M \text{ para em toda entrada}\}$$

- **Parada em alguma entrada:**

$$HALT_{some} = \{\langle M \rangle \mid \exists w : M \text{ para em } w\}$$
#### Trivialidade

Qualquer propriedade não-trivial sobre MTs tende a ser indecidível (Teorema de Rice).

{16}------------------------------------------------
### Redução: Ferramenta para Provar Indecidibilidade
#### Ideia de Redução

Para provar que um problema  $B$  é indecidível:

- 1 Escolher um problema  $A$  que sabemos ser indecidível (ex: *HALT*)
- 2 Mostrar que se pudéssemos decidir  $B$ , poderíamos decidir  $A$
- 3 Como  $A$  é indecidível,  $B$  também deve ser
#### Notação

$A \leq_m B$  significa “ $A$  é redutível a  $B$ ” (ou “ $A$  reduz para  $B$ ”).  
Se  $A \leq_m B$  e  $A$  é indecidível, então  $B$  é indecidível.

A diagram illustrating the reduction process. It consists of two rectangular boxes. The left box contains the text "Problema A". Below this box is the word "indecidível". An arrow points from the right side of the left box to the left side of the right box. Above the arrow is the word "redução". The right box contains the text "Problema B". Below this box is the expression "$\Rightarrow$ indecidível".

Diagram showing the reduction from Problem A to Problem B. Problem A is labeled 'indecidível' and Problem B is labeled '$\Rightarrow$ indecidível'.

{17}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-b0d4609bc46c2d88a8318706bb5321f7_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram showing the reduction from Problem A to Problem B.
<!-- /IMAGE_DESCRIPTION -->
### Exemplo: Problema da Aceitação
#### Definição

$$A_{TM} = \{\langle M, w \rangle \mid M \text{ aceita } w\}$$
#### Teorema

$A_{TM}$  é indecidível.
#### Prova (Redução de *HALT*)

Mostraremos que  $HALT \leq_m A_{TM}$ .

Dada instância  $\langle M, w \rangle$  de *HALT*, construa  $M'$ :

- 1  $M'$  simula  $M$  em  $w$
- 2 Se  $M$  para (aceita ou rejeita),  $M'$  aceita

Então:  $M$  para em  $w \iff M'$  aceita  $w \iff \langle M', w \rangle \in A_{TM}$   
Se pudéssemos decidir  $A_{TM}$ , decidiríamos *HALT*. Contradição!

{18}------------------------------------------------
### Exemplo: Problema da Linguagem Vazia
#### Definição

$$E_{TM} = \{\langle M \rangle \mid L(M) = \emptyset\}$$

O problema de decidir se uma MT não aceita nenhuma string.
#### Teorema

$E_{TM}$  é indecidível.
#### Prova (Redução de $A_{TM}$ )

Dada instância  $\langle M, w \rangle$  de  $A_{TM}$ , construa  $M_w$ :

- $M_w$  ignora sua entrada
- Simula  $M$  em  $w$
- Se  $M$  aceita  $w$ ,  $M_w$  aceita

Então:  $M$  aceita  $w \iff L(M_w) \neq \emptyset \iff \langle M_w \rangle \notin E_{TM}$

{19}------------------------------------------------
## Implicações Práticas
### Verificação de Software

Não existe ferramenta que possa verificar automaticamente se **qualquer** programa irá terminar.

- Verificadores podem funcionar para **classes restritas** de programas
- Podem usar heurísticas que funcionam “na maioria dos casos”
- Podem requerer **anotações** do programador (invariantes, variantes)
## Exemplos Reais

- **Compiladores:** não podem otimizar perfeitamente (ex: eliminar código morto)
- **Antivírus:** não podem detectar todos os malwares
- **Analisaadores estáticos:** falsos positivos/negativos

{20}------------------------------------------------
### O Problema da Parada em Linguagens Reais
### Programas Equivalentes a MTs

Linguagens como C, Python, Java são Turing-completas:

- Podem simular qualquer MT
- O Problema da Parada se aplica a elas
### Exemplo em Python

```
1 def will_halt(programa, entrada):  
2     # Este algoritmo não pode existir!  
3     # Retornaria True se programa(entrada) para  
4     # Retornaria False se programa(entrada) não para  
5     pass
```
#### Consequência

Nenhuma IDE ou ferramenta pode sempre detectar loops infinitos em código arbitrário.

{21}------------------------------------------------
### Casos Especiais Decidíveis
### Quando Podemos Decidir Terminação?

Existem **subclasses** de programas para as quais a terminação é decidível:
## Exemplos

- **Autômatos Finitos:** sempre terminam (passos finitos)
- **Autômatos de Pilha:** decidíveis por análise da gramática
- **Funções primitivas recursivas:** sempre terminam
- **Loops limitados:** 'for i in range(n)' sempre termina
- **Programas com medidas de terminação:** funções que decrescem a cada iteração
## Na Prática

A maioria dos programas úteis **podem** ter sua terminação verificada, mas não **todos**.

{22}------------------------------------------------
### Exercício 1: Compreensão da Prova

- 1 Explique por que a máquina  $D$  na prova do Problema da Parada deve receber sua **própria descrição** como entrada para gerar a contradição.
- 2 Na prova, o que aconteceria se  $D$  fizesse o **mesmo** que  $H$  indica (ao invés do oposto)? Ainda teríamos contradição?
- 3 Por que não podemos simplesmente “executar  $M$  em  $w$  por um tempo limitado” e declarar que  $M$  não para se não terminar nesse tempo?

A faint, grayscale watermark of the University of Coimbra seal is visible in the background. It features a shield with a cross and other heraldic elements, topped with a crown. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT".

Faint background watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

{23}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-d3294dc879b451b369c0b06f42e9b39f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the PUCRS seal
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-0ab720844e454afef91e5d68f4ab8ad9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-e954015e19aabf163663a8fa54b8b48c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Variações do Problema da Parada

Prove que os seguintes problemas são indecidíveis (usando redução de *HALT*):

1  $HALT_{\epsilon} = \{\langle M \rangle \mid M \text{ para na entrada vazia } \epsilon\}$

*Dica:* Dada  $\langle M, w \rangle$ , construa  $M'$  que ignora sua entrada e simula  $M$  em  $w$ .

2  $HALT_{101} = \{\langle M \rangle \mid M \text{ para na entrada } 101\}$

3 O problema de decidir se uma MT para em **exatamente 100 passos** para alguma entrada.

The image is a watermark of the University of Coimbra seal. It features a shield with a cross and the motto 'AD VERVM DVOCIT' (To the truth it calls) written in a banner below. The shield is flanked by two figures, and the entire emblem is rendered in a light gray color.

Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

{24}------------------------------------------------
### Exercício 3: Reconhecibilidade

- 1 Mostre que o conjunto  $\{\langle M \rangle \mid M \text{ aceita pelo menos uma string}\}$  é Turing-reconhecível.  
*Dica:* Use dovetailing (intercalação) para testar todas as strings possíveis.
- 2 Por que  $\overline{HALT}$  não é Turing-reconhecível?
- 3 Existe uma linguagem que não é Turing-reconhecível nem co-Turing-reconhecível? Justifique.

A faint, stylized illustration of a coat of arms featuring a crown, a shield with a cross, and a banner with the Latin motto 'AD VERVM DVOCIT'.

{25}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-f770ac8927cbf6aa997de6e0307c9783_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A faint, stylized illustration of a coat of arms featuring a crown, a shield with a cross, and a banner with the Latin motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 4: Reduções

Para cada par  $(A, B)$ , determine se  $A \leq_m B$ ,  $B \leq_m A$ , ambos, ou nenhum:

- 1  $A = HALT$ ,  $B = A_{TM}$
- 2  $A = \{\langle M \rangle \mid M \text{ aceita } \langle M \rangle\}$ ,  $B = HALT$
- 3  $A = E_{TM}$ ,  $B = \overline{E_{TM}}$

Lembre-se:  $A \leq_m B$  significa que existe uma função computável  $f$  tal que  $x \in A \iff f(x) \in B$ .

The image is a watermark of the coat of arms of the University of Coimbra. It features a shield with a star in the center, surrounded by a pattern of small crosses. Above the shield is a crown, and below it is a ribbon with the Latin motto "AD VERVM DVICIT". The entire emblem is rendered in a light gray color.

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{26}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-9887cf85c05205c57271d28ecc108b32_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 5: Aplicações Práticas

- 1 Um colega afirma ter criado um programa que detecta loops infinitos em código Python. Critique esta afirmação considerando o Problema da Parada.
- 2 Considere o seguinte código:

```
1     def mystery(n):  
2         while n != 1:  
3             if n % 2 == 0:  
4                 n = n // 2  
5             else:  
6                 n = 3*n + 1  
7     return n
```

Este é o problema de Collatz. Por que não podemos usar um computador para provar que este programa sempre termina para todo  $n > 0$ ?

{27}------------------------------------------------
### Exercício 6: Questões Conceituais

- 1 Se o Problema da Parada fosse decidível, quais seriam as consequências para a computação?
- 2 Existe algum modelo de computação **mais poderoso** que Máquinas de Turing que poderia decidir o Problema da Parada? Justifique com base na Tese de Church-Turing.
- 3 A indecidibilidade do Problema da Parada implica que existem programas cuja terminação **nunca** poderá ser determinada por nenhum meio (incluindo prova matemática humana)?

A faint, grayscale watermark of the University of Coimbra's coat of arms is visible in the background. It features a shield with a cross and four smaller crosses in the quadrants, topped by a crown. The shield is flanked by two figures. Below the shield is a ribbon with the Latin motto 'AD VERVM DVOCIT'.

Faint watermark of the University of Coimbra crest, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

{28}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-e3c1d325b828c44049a7ac37e5b34603_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra crest, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-c80dd550f724de455f5efebaed25198d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the University of Coimbra crest.
<!-- /IMAGE_DESCRIPTION -->
## Desafio
### Teorema da Recursão

O **Teorema da Recursão** de Kleene afirma que qualquer MT pode obter sua própria descrição.

Use este fato para dar uma prova alternativa da indecidibilidade de *HALT*:

- 1 Assuma que existe um decisor  $H$  para *HALT*
- 2 Construa uma MT  $M$  que:
  - Obtém sua própria descrição  $\langle M \rangle$
  - Executa  $H(\langle M, w \rangle)$  onde  $w$  é a entrada
  - Faz o oposto do que  $H$  indica
- 3 Derive a contradição
## Reflexão

Como esta prova se relaciona com a autoreferência no Paradoxo de Russell e nos Teoremas de Gödel?

{29}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] Alonzo Church. “An Unsolvable Problem of Elementary Number Theory”. Em: *American Journal of Mathematics* 58.2 (1936), pp. 345–363.
- [3] Martin D. Davis. *Computability and Unsolvability*. Dover Publications, 1982.
- [4] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [5] Marvin L. Minsky. *Computation: Finite and Infinite Machines*. Prentice-Hall, 1967.

A faint, semi-transparent watermark of the University of Coimbra crest is visible in the background. The crest features a shield with a cross and other heraldic elements, topped with a crown and surrounded by decorative flourishes. The text "UNIVERSITAS COIMBRENSIS" is partially visible around the shield.

Faint background watermark of the University of Coimbra crest.

{30}------------------------------------------------
## Referências II

- [6] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [7] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.
- [8] Alan M. Turing. “On Computable Numbers, with an Application to the Entscheidungsproblem”. Em: *Proceedings of the London Mathematical Society* 42.1 (1936), pp. 230–265.

A faint, semi-transparent watermark of the University of Coimbra's coat of arms is visible in the background. It features a shield with a star and the motto 'AD VERVM DVOCIT' (To the truth it calls) on a ribbon below. The shield is flanked by two figures, and the entire emblem is rendered in a light gray color.

Faint watermark of the University of Coimbra crest, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

<!-- IMAGE_DESCRIPTION: datalab-8a919c7e46849292573775081d1b3d66_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra crest, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-1d7527f4316cfe2d342b08d1653d1592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS Escola Politécnica
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

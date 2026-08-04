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
  - Pergunta
  - Codificação de Máquinas de Turing
  - Definição Formal
- **O Problema da Parada (Halting Problem)**
  - Linguagem Associada
  - Teorema (Turing, 1936)
  - Prova: Estrutura do Argumento
  - Método: Prova por Contradição + Diagonalização
  - Visualização: Argumento Diagonal
  - Analogia ao Paradoxo de Russell
  - Problema do Barbeiro
  - Conexão
- ***HALT* é Reconhecível, mas não Decidível**
  - *HALT* é Turing-Reconhecível
  - Problema
  - Hierarquia
  - O Complemento de $HALT$
  - Definição
  - Prova
  - Variações do Problema da Parada
  - Todas são Indecidíveis
  - Trivialidade
  - Redução: Ferramenta para Provar Indecidibilidade
  - Exemplo: Problema da Aceitação
  - Prova (Redução de $HALT$ )
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
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Halting Problem - O Problema da Parada

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 11

Teoria da Computabilidade e Complexidade  
Ciência da Computação

15 de abril de 2026

The logo of PUCRS, featuring a shield with a cross and a star, and the text 'PUCRS' below it.

Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

{1}------------------------------------------------
## Sumário

- 1 Introdução
- 2 O Problema da Parada
- 3 Consequências e Aplicações
- 4 Exercícios

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central vertical band containing a monogram, flanked by two vertical bands with a repeating cross pattern. Above the shield is a crown and two crossed keys. Below the shield is a banner with the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8c378a184b5ae4d1605cb74d7b7a7e3f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-082ba09313df59d76a7bfbdde8ec877d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-f770ac8927cbf6aa997de6e0307c9783_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9887cf85c05205c57271d28ecc108b32_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->
## Contexto Histórico
## A Busca pelos Limites da Computação

No início do século XX, alguns matemáticos buscavam entender os **limites fundamentais** do que pode ou não ser computado.

- **1900**: David Hilbert propõe 23 problemas fundamentais
- **1928**: Hilbert e Ackermann formalizam o *Entscheidungsproblem*
- **1936**: Alan Turing publica “On Computable Numbers”
- **1936**: Turing demonstra que o Problema da Parada é **indecidível**
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
- $\Gamma$ : alfabeto da fita ( $\Sigma \subseteq \Gamma, \sqcup \in \Gamma$ )
- $\delta : Q \times \Gamma \rightarrow Q \times \Gamma \times \{L, R\}$
- $q_0, q_{accept}, q_{reject} \in Q$ : estados inicial, de aceitação e rejeição
### Comportamento

Para entrada  $w$ , a MT  $M$  pode:

- 1 **Aceitar**: entrar em  $q_{accept}$
- 2 **Rejeitar**: entrar em  $q_{reject}$
- 3 **Looping**: nunca parar

{5}------------------------------------------------
### Linguagens e Decidibilidade
### Linguagem de uma MT

$$L(M) = \{w \mid M \text{ aceita } w\}$$
### Tipos de Linguagens

Decidível (Recursiva): Existe MT  $M$  que **sempre para e**:

- Aceita se  $w \in L$
- Rejeita se  $w \notin L$

Reconhecível (Recursivamente Enumerável): Existe MT  $M$  que:

- Aceita se  $w \in L$
- Rejeita ou **loop** se  $w \notin L$
### Pergunta

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

- 1 Assumir que existe uma MT  $H$  que decide  $HALT$
- 2 Construir uma nova MT  $D$  usando  $H$
- 3 Mostrar que  $D$  leva a uma contradição
- 4 Concluir que  $H$  não pode existir

```
graph LR; Input["<M, w>"] --> H[H]; H --> Accept["aceita se M para em w"]; H --> Reject["rejeita se M não para em w"];
```

Diagram of a hypothetical Turing machine H. An input  enters a box labeled H. Two arrows exit the box: one pointing to 'aceita se M para em w' and another pointing to 'rejeita se M não para em w'.

A MT hipotética  $H$  **sempre para** e responde corretamente.

{9}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-a234352dfaccdc24745c88eef7724cc6_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a hypothetical Turing machine H.
<!-- /IMAGE_DESCRIPTION -->
#### Prova: Construção da Máquina $D$
#### Definição de $D$

Usando  $H$ , construímos  $D$  que recebe  $\langle M \rangle$  como entrada:

- 1 Execute  $H$  com entrada  $\langle M, \langle M \rangle \rangle$
- 2 Se  $H$  aceita (i.e.,  $M$  para em  $\langle M \rangle$ ): entre em loop infinito
- 3 Se  $H$  rejeita (i.e.,  $M$  não para em  $\langle M \rangle$ ): aceite e pare

```
graph LR; Input("<M>") --> D; subgraph D [D]; H[H]; end; H -- "se aceita" --> Loop("loop $\infty$"); H -- "se rejeita" --> Para("para");
```

Diagram illustrating the construction of machine D. An input  enters a dashed box labeled D. Inside D is a box labeled H. From the output of H, two paths emerge: 'se aceita' leading to 'loop $\infty$' and 'se rejeita' leading to 'para'.

<!-- IMAGE_DESCRIPTION: datalab-1eadbbe42cfcac5c0023577110aec5e3_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram illustrating the construction of machine D.
<!-- /IMAGE_DESCRIPTION -->
#### Comportamento de $D$

$D(\langle M \rangle)$  faz o **oposto** do que  $M$  faz quando recebe sua própria descrição.

{10}------------------------------------------------
#### Prova por Contradição

Onde está a contradição?

O que acontece quando executamos  $D$  com sua própria descrição?

$$D(\langle D \rangle) = ?$$

Possibilidades

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

{12}------------------------------------------------
### Analogia ao Paradoxo de Russell
### Problema do Barbeiro

Em uma vila, o barbeiro barbeia todas as pessoas que não barbeiam a si mesmas, e apenas essas pessoas.

**Pergunta:** O barbeiro barbeia a si mesmo?

- Se ele barbeia a si mesmo  $\Rightarrow$  não deveria (pois só barbeia quem não se barbeia)
- Se ele não barbeia a si mesmo  $\Rightarrow$  deveria (pois barbeia todos que não se barbeiam)
### Conexão

A máquina  $D$  é como o “barbeiro”: ela é definida para fazer o oposto do que “deveria” fazer quando aplicada a si mesma.

{13}------------------------------------------------
## *HALT* é Reconhecível, mas não Decidível
### *HALT* é Turing-Reconhecível

Podemos construir uma MT  $R$  que **reconhece** *HALT*:

- 1 Entrada:  $\langle M, w \rangle$
- 2 Simule  $M$  em  $w$
- 3 Se  $M$  parar, aceite
### Problema

$R$  não **decide** *HALT*.
### Hierarquia

O diagrama ilustra a hierarquia dos problemas de decisão. Consiste em dois ovais concêntricos. O oval interno, menor, é rotulado 'Decidíveis'. O oval externo, maior, é rotulado 'Reconhecíveis'. A região entre os dois ovais, representando problemas que são reconhecíveis mas não decidíveis, contém o rótulo '*HALT*'.

Diagrama de hierarquia de problemas de decisão

{14}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-66c2bf11a8f117cddf67eff92d4c736c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de hierarquia de problemas de decisão
<!-- /IMAGE_DESCRIPTION -->
### O Complemento de $HALT$
### Definição

$$\overline{HALT} = \{\langle M, w \rangle \mid M \text{ não para em } w\}$$
#### Teorema

$\overline{HALT}$  **não** é Turing-reconhecível.
### Prova

Se tanto  $HALT$  quanto  $\overline{HALT}$  fossem reconhecíveis, então  $HALT$  seria decidível:

- Execute reconhecedores  $HALT$  e  $\overline{HALT}$  em paralelo
- Um deles eventualmente aceita; isso daria um decisor para  $HALT$

Mas  $HALT$  não é decidível, então  $\overline{HALT}$  não pode ser reconhecível.

{15}------------------------------------------------
### Variações do Problema da Parada
### Todas são Indecidíveis
#### - Parada na entrada vazia:

$$HALT_{\epsilon} = \{\langle M \rangle \mid M \text{ para em } \epsilon\}$$
#### - Parada em todas as entradas:

$$HALT_{all} = \{\langle M \rangle \mid M \text{ para em toda entrada}\}$$
#### - Parada em alguma entrada:

$$HALT_{some} = \{\langle M \rangle \mid \exists w : M \text{ para em } w\}$$
### Trivialidade

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

```
graph LR; A[Problema A] -- redução --> B[Problema B]; A --- A_label[indecidível]; B --- B_label["$\Rightarrow$ indecidível"];
```

Diagram illustrating a reduction from Problema A to Problema B. A box labeled 'Problema A' is connected by an arrow labeled 'redução' to a box labeled 'Problema B'. Below 'Problema A' is the word 'indecidível', and below 'Problema B' is '$\Rightarrow$ indecidível'.

{17}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-9b62a616c7a1097c5da57f001ab6dd64_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram illustrating a reduction from Problema A to Problema B.
<!-- /IMAGE_DESCRIPTION -->
### Exemplo: Problema da Aceitação
#### Definição

$$A_{TM} = \{ \langle M, w \rangle \mid M \text{ aceita } w \}$$
#### Teorema

$A_{TM}$  é indecidível.
### Prova (Redução de $HALT$ )

Mostraremos que  $HALT \leq_m A_{TM}$ .

Dada instância  $\langle M, w \rangle$  de  $HALT$ , construa  $M'$ :

- 1  $M'$  simula  $M$  em  $w$
- 2 Se  $M$  para (aceita ou rejeita),  $M'$  aceita

Então:  $M$  para em  $w \iff M'$  aceita  $w \iff \langle M', w \rangle \in A_{TM}$

Se pudéssemos decidir  $A_{TM}$ , decidiríamos  $HALT$ . Contradição!

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
- **Analisadores estáticos:** falsos positivos/negativos

{20}------------------------------------------------
### O Problema da Parada em Linguagens Reais
### Programas Equivalentes a MTs

Linguagens como C, Python, Java são Turing-completas:

- Podem simular qualquer MT
- O Problema da Parada se aplica a elas
### Exemplo em Python

```
1  def will_halt(programa, entrada):  
2      # Este algoritmo não pode existir!  
3      # Retornaria True se programa(entrada) para  
4      # Retornaria False se programa(entrada) não para  
5      pass
```
#### Consequência

Nenhuma IDE ou ferramenta pode sempre detectar loops infinitos em código arbitrário.

{21}------------------------------------------------
### Casos Especiais Decidíveis
### Quando Podemos Decidir Terminação?

Existem **subclasses** de programas para as quais a terminação é decidível:
## Exemplos

- **Autômatos Finitos**: sempre terminam (passos finitos)
- **Autômatos de Pilha**: decidíveis por análise da gramática
- **Funções primitivas recursivas**: sempre terminam
- **Loops limitados**: 'for i in range(n)' sempre termina
- **Programas com medidas de terminação**: funções que decrescem a cada iteração
## Na Prática

A maioria dos programas úteis **podem** ter sua terminação verificada, mas não **todos**.

{22}------------------------------------------------
### Exercício 1: Compreensão da Prova

- 1 Explique por que a máquina  $D$  na prova do Problema da Parada deve receber sua **própria descrição** como entrada para gerar a contradição.
- 2 Na prova, o que aconteceria se  $D$  fizesse o **mesmo** que  $H$  indica (ao invés do oposto)? Ainda teríamos contradição?
- 3 Por que não podemos simplesmente “executar  $M$  em  $w$  por um tempo limitado” e declarar que  $M$  não para se não terminar nesse tempo?

Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and a banner below reading 'AD VERVM DVCIT'.

{23}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-0ab720844e454afef91e5d68f4ab8ad9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and a banner below reading 'AD VERVM DVCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Variações do Problema da Parada

Prove que os seguintes problemas são indecidíveis (usando redução de *HALT*):

- 1  $HALT_{\epsilon} = \{\langle M \rangle \mid M \text{ para na entrada vazia } \epsilon\}$   
*Dica:* Dada  $\langle M, w \rangle$ , construa  $M'$  que ignora sua entrada e simula  $M$  em  $w$ .
- 2  $HALT_{101} = \{\langle M \rangle \mid M \text{ para na entrada } 101\}$
- 3 O problema de decidir se uma MT para em **exatamente 100 passos** para alguma entrada.

The image shows the coat of arms of the University of São Paulo (USP). It features a central shield with a white background and a large blue star. The shield is flanked by two blue lions. Above the shield is a blue crown. A blue banner at the bottom of the shield contains the Latin motto 'AD VERVM DVCT'.

Coat of arms of the University of São Paulo (USP)

{24}------------------------------------------------
### Exercício 3: Reconhecibilidade

- 1 Mostre que o conjunto  $\{\langle M \rangle \mid M \text{ aceita pelo menos uma string}\}$  é Turing-reconhecível.  
*Dica:* Use dovetailing (intercalação) para testar todas as strings possíveis.
- 2 Por que  $\overline{HALT}$  não é Turing-reconhecível?
- 3 Existe uma linguagem que não é Turing-reconhecível nem co-Turing-reconhecível? Justifique.

The image shows the coat of arms of the University of São Paulo (USP). It features a central shield with a white background and a large blue star at the bottom. The shield is flanked by two golden lions. Above the shield is a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{25}------------------------------------------------
### Exercício 4: Reduções

Para cada par  $(A, B)$ , determine se  $A \leq_m B$ ,  $B \leq_m A$ , ambos, ou nenhum:

- 1  $A = HALT$ ,  $B = A_{TM}$
- 2  $A = \{\langle M \rangle \mid M \text{ aceita } \langle M \rangle\}$ ,  $B = HALT$
- 3  $A = E_{TM}$ ,  $B = \overline{E_{TM}}$

Lembre-se:  $A \leq_m B$  significa que existe uma função computável  $f$  tal que  $x \in A \iff f(x) \in B$ .

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a white field containing a grid of green crosses. A central vertical band (fess) is black with a white star and a white monogram. Above the shield is a crown. The shield is flanked by two crossed keys (the keys of St. Peter). Below the shield is a blue ribbon with the Latin motto 'AD VERVM DVCT' in white capital letters.

Coat of arms of the University of São Paulo (USP)

{26}------------------------------------------------
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

Faint watermark of the University of São Paulo (USP) coat of arms, featuring a central shield with a star, flanked by two figures, and a banner below reading 'AD VERVM DVCT'.

{28}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-e3c1d325b828c44049a7ac37e5b34603_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a central shield with a star, flanked by two figures, and a banner below reading 'AD VERVM DVCT'.
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

- ![Faint watermark of the University of Brasília seal in the background.](b4fd951633a5d21f350c61bae231fccd_img.jpg)
- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
  - [2] Alonzo Church. “An Unsolvable Problem of Elementary Number Theory”. Em: *American Journal of Mathematics* 58:2 (1936), pp. 345–363.
  - [3] Martin D. Davis. *Computability and Unsolvability*. Dover Publications, 1982.
  - [4] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
  - [5] Marvin L. Minsky. *Computation: Finite and Infinite Machines*. Prentice-Hall, 1967.

{30}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-b4fd951633a5d21f350c61bae231fccd_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Brasília seal in the background.
<!-- /IMAGE_DESCRIPTION -->
## Referências II

- [6] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [7] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.
- [8] Alan M. Turing. “On Computable Numbers, with an Application to the Entscheidungsproblem”. Em: *Proceedings of the London Mathematical Society* 42.1 (1936), pp. 230–265.

Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star, a banner reading 'AD VERVM DVCIT', and a crown above.

<!-- IMAGE_DESCRIPTION: datalab-8a919c7e46849292573775081d1b3d66_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star, a banner reading 'AD VERVM DVCIT', and a crown above.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-d3294dc879b451b369c0b06f42e9b39f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

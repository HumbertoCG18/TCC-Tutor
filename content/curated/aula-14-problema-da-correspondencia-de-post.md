<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Introdução ao PCP**
- **Problema da Correspondência de Post (PCP)**
  - No contexto de Teoria da Computação
  - Definição do PCP
  - Problema da Correspondência de Post (PCP)
  - Em Outras Palavras
  - Exemplo de Instância de PCP
  - Exemplo de Instância de PCP sem Solução
  - Análise
  - Indecidibilidade do PCP
  - Teorema (Post, 1946)
  - Estratégia da Prova
  - Como a Construção Funciona
  - Famílias de Dominós na Prova (cont.)
  - Dominós de Aceitação
  - Do MPCP para o PCP
  - Moral da Construção
  - Exemplo Completo: Máquina e Computação
  - Exemplo Completo: Montando a História
  - Exemplo Completo: Montando a História (cont.)
  - Padrão
  - Exemplo Completo: Fechando a Solução
  - Aceitação
- **PCP Modificado (MPCP)**
  - MPCP
  - Relação entre MPCP e PCP
  - Redução MPCP $\rightarrow$ PCP
  - Variantes do PCP
  - Fronteira
  - Usando PCP para Provar Indecidibilidade
  - Por que PCP é Útil?
  - Problemas Indecidíveis via Redução de PCP
  - Ambiguidade de GLCs
  - Definição
  - Teorema
  - Esboço da Prova (Redução de PCP)
  - Equivalência de GLCs
  - Teorema
  - Prova (Esboço)
  - Contraste
- **Resumo: PCP**
- **O Que Sabemos**
  - Exercício 1: PCP - Encontrando Soluções
  - Exercício 2: PCP - Análise
  - Exercício 3: Reduções
- **Referências I**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Problema da Correspondência de Post

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 14

Teoria da Computabilidade e Complexidade  
Ciência da Computação

24 de abril de 2026

The logo of the Escola Politécnica of PUCRS, featuring a shield with a star and the text "PUCRS" and "ESCOLA POLITÉCNICA".

Logo of ESCOLA POLITÉCNICA PUCRS

{1}------------------------------------------------
## Sumário

**1** Problema da Correspondência de Post

**2** Aplicações e Consequências

**3** Exercícios

The image is a large, light gray watermark of the Brazilian coat of arms. It features a central shield with a green field containing a white five-pointed star and a gold field containing a white cross. The shield is flanked by two crossed keys (the keys of St. Peter) and topped by a crown. A ribbon at the bottom contains the motto 'AD VERVM DVCIT'.

Coat of arms of Brazil

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-fb15f15a7d964c8490c9317e43e40c1a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
## Introdução ao PCP
## Problema da Correspondência de Post (PCP)

O PCP foi introduzido por Emil Post em 1946.

É um problema indecidível que:

- Não envolve diretamente Máquinas de Turing
- É simples de enunciar
- É útil para provar indecidibilidade de outros problemas
### No contexto de Teoria da Computação

O PCP é frequentemente usado como “ponto de partida” para reduções, especialmente em problemas sobre gramáticas e linguagens formais.

{3}------------------------------------------------
### Definição do PCP
### Problema da Correspondência de Post (PCP)

**Entrada:** Uma coleção de **dominós** (pares de strings):

$$\left\{ \left[ \frac{t_1}{b_1} \right], \left[ \frac{t_2}{b_2} \right], \dots, \left[ \frac{t_k}{b_k} \right] \right\}$$

onde  $t_i$  é o “topo” e  $b_i$  é a “base” do  $i$ -ésimo dominó.

**Pergunta:** Existe uma sequência de índices  $i_1, i_2, \dots, i_n$  (com repetições permitidas) tal que:

$$t_{i_1} t_{i_2} \cdots t_{i_n} = b_{i_1} b_{i_2} \cdots b_{i_n}$$
### Em Outras Palavras

Podemos empilhar dominós de forma que a concatenação dos topos seja igual à concatenação das bases?

{4}------------------------------------------------
### Exemplo de Instância de PCP
#### Instância

| Dominó 1       | Dominó 2       | Dominó 3       |
|----------------|----------------|----------------|
| $\frac{a}{ab}$ | $\frac{b}{ca}$ | $\frac{ca}{a}$ |

Solução: sequência 1, 3, 2, 3

$$\frac{a}{ab} \quad \frac{ca}{a} \quad \frac{b}{ca} \quad \frac{ca}{a}$$

■ Topos:  $a \cdot ca \cdot b \cdot ca = acabca$

■ Bases:  $ab \cdot a \cdot ca \cdot a = abacaa$

Erro...

■ Topos:  $a \cdot ca \cdot ca \cdot b = acacab$

■ Bases:  $ab \cdot a \cdot a \cdot ca = abaaca$

Erro...

{5}------------------------------------------------

Problema da Correspondência de Post
Aplicações e Consequências
Exercícios
Referências

○ ○ ● ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○
○ ○ ○ ○
○ ○ ○

# Exemplo de Instância de PCP (contd.)

**Instância**

| Dominó 1       | Dominó 2       | Dominó 3       |
|----------------|----------------|----------------|
| $\frac{b}{ca}$ | $\frac{a}{ab}$ | $\frac{ca}{a}$ |

**Solução: sequência 2, 1, 3, 2, 1**

- Topos:  $a \cdot b \cdot ca \cdot a \cdot b = abcaab$
- Bases:  $ab \cdot ca \cdot a \cdot ab = abcaab \checkmark$

**Observação**

Encontrar soluções pode ser "difícil" e, para algumas instâncias, **não existe solução**.

Prof. Anderson R. P. Domingues
PCP      6 / 26

{6}------------------------------------------------
### Exemplo de Instância de PCP sem Solução
#### Instância

| Dominó 1         | Dominó 2         |
|------------------|------------------|
| $\frac{ab}{aba}$ | $\frac{bab}{ab}$ |
### Análise

- Dominó 1: topo tem 2 símbolos, base tem 3
- Dominó 2: topo tem 3 símbolos, base tem 2
- Se começarmos com dominó 1: topo fica 1 símbolo “atrás”
- Se começarmos com dominó 2: topo fica 1 símbolo “na frente”
- Qualquer sequência que comece com 1 terá topo sempre menor
- Qualquer sequência que comece com 2 terá topo sempre maior

{7}------------------------------------------------
### Indecidibilidade do PCP
### Teorema (Post, 1946)

O Problema da Correspondência de Post é **indecidível**.
### Estratégia da Prova

A prova costuma ser feita em **duas etapas**:

$$A_{TM} \leq_m MPCP \quad \text{e} \quad MPCP \leq_m PCP$$

A etapa central é a primeira: construir dominós que têm solução sse  $M$  aceita  $w$ .
#### Ideia Intuitiva

Os dominós codificam uma história de computação:

- A configuração inicial de  $M$  em  $w$
- Cada passo legal de transição
- A limpeza final quando um estado de aceitação aparece

{8}------------------------------------------------
### Como a Construção Funciona

- Uma configuração é escrita como  $\#u \ q \ a \ v\#$ : a fita contém  $uav$ , a cabeça lê  $a$ , e o estado atual é  $q$ .
- Se a computação aceitante for

$$C_0 \vdash C_1 \vdash \dots \vdash C_t,$$

queremos produzir

$$\text{topo} = \#C_0\#C_1\#\dots\#C_{t-1}\# \quad \text{base} = \#C_0\#C_1\#\dots\#C_t\#.$$

- A base fica uma configuração à frente; se  $C_t$  é aceitante, dominós especiais permitem ao topo consumir esse último sufixo.

{9}------------------------------------------------

Problema da Correspondência de Post  $\circ\circ\circ\circ\circ\circ\circ\bullet\circ\circ\circ\circ\circ\circ\circ\circ$ 
Aplicações e Consequências  $\circ\circ\circ\circ$ 
Exercícios  $\circ\circ\circ$ 
Referências

# Famílias de Dominós na Prova

- Inicial:**

$$\left[ \frac{\#}{\# q_0 w \#} \right]$$
- Cópia:**

$\left[ \frac{a}{a} \right]$ 
 $a \in \Gamma \cup \{\#\}$
- Transição à direita:**

$$\delta(q, a) = (r, b, R) \Rightarrow \left[ \frac{qa}{br} \right]$$
- Para movimento à esquerda, usa-se uma família um pouco maior para também copiar o vizinho à esquerda.**

Image: Coat of arms watermark with the text 'AD VERUM DUCIT'

Prof. Anderson R. P. Domingues
PCP
10 / 26

{10}------------------------------------------------
### Famílias de Dominós na Prova (cont.)
### Dominós de Aceitação

Quando  $q_{acc}$  aparece, usamos dominós que apagam os símbolos ao redor desse estado:

$$\left[ \frac{aq_{acc}}{q_{acc}} \right] \quad \left[ \frac{q_{acc}a}{q_{acc}} \right] \quad a \in \Gamma \cup \{\#\}$$

Eles fazem  $q_{acc}$  “engolir” a configuração restante.
### Do MPCP para o PCP

No MPCP, o primeiro dominó é forçado; no PCP comum, marcadores extras simulam essa obrigação.
### Moral da Construção

Uma solução válida descreve uma computação inteira de  $M$ .

{11}------------------------------------------------
### Exemplo Completo: Máquina e Computação
#### Máquina Exemplo

Considere a MT que, na entrada  $w = 01$ , faz:

$$\delta(q_0, 0) = (q_1, X, R) \quad \delta(q_1, 1) = (q_{acc}, 1, R)$$

A computação aceitante é:

$$C_0 = q_0 01 \# \vdash C_1 = X q_1 1 \# \vdash C_2 = X 1 q_{acc} \#$$
#### Dominós Necessários

$$s = \left[ \frac{\#}{\# q_0 01 \#} \right] \quad t_1 = \left[ \frac{q_0 0}{X q_1} \right] \quad t_2 = \left[ \frac{q_1 1}{1 q_{acc}} \right]$$

$$c_X = \left[ \frac{X}{X} \right], \quad c_1 = \left[ \frac{1}{1} \right], \quad c_{\#} = \left[ \frac{\#}{\#} \right]$$

{12}------------------------------------------------
### Exemplo Completo: Montando a História
#### Fase 1: Forçar a Configuração Inicial

$$s = \left[ \frac{\#}{\#q_01\#} \right] \Rightarrow \text{topo} = \# \quad \text{base} = \#q_01\#$$
#### Fase 2: Simular $C_0 \vdash C_1$

Escolhemos

$$t_1, c_1, c_\#$$

Isso acrescenta ao topo  $q_0 01\#$  e à base  $Xq_1 1\#$ . Logo:

$$\text{topo} = \#q_01\# \quad \text{base} = \#q_01\#Xq_11\#$$

{13}------------------------------------------------
### Exemplo Completo: Montando a História (cont.)
#### Fase 3: Simular $C_1 \vdash C_2$

Escolhemos

$$c_X, t_2, c_\#$$

e obtemos:

$$\text{topo} = \#q_001\#Xq_11\#$$

$$\text{base} = \#q_001\#Xq_11\#X1q_{acc}\#$$
### Padrão

Ao final de cada fase, a base fica exatamente uma configuração à frente do topo.

{14}------------------------------------------------
### Exemplo Completo: Fechando a Solução
#### Último Passo

Depois de simular a computação:

$$\text{topo} = \#C_0\#C_1\# \quad \text{base} = \#C_0\#C_1\#C_2\#$$

onde  $C_2 = X1q_{acc}\#$  é aceitante.
### Aceitação

Os dominós de aceitação fazem  $q_{acc}$  absorver os vizinhos:

$$X1q_{acc}\# \implies Xq_{acc}\# \implies q_{acc}\# \implies \#$$

Assim, o topo consome o sufixo aceitante que faltava, e a solução codifica exatamente

$$\#q_001\# \vdash \#Xq_11\# \vdash \#X1q_{acc}\#.$$

{15}------------------------------------------------

{16}------------------------------------------------
## PCP Modificado (MPCP)
### MPCP

Versão do PCP onde o primeiro dominó da sequência deve ser o dominó 1.
### Relação entre MPCP e PCP

1  $A_{TM} \leq_m MPCP$  (mais fácil de provar)

2  $MPCP \leq_m PCP$  (redução técnica)

Logo,  $A_{TM} \leq_m PCP$ , e PCP é indecidível.
### Redução MPCP $\rightarrow$ PCP

Adicionar marcadores especiais que forçam o dominó 1 a ser escolhido primeiro, sem essa restrição explícita.

{17}------------------------------------------------
### Variantes do PCP
#### Variantes Indecidíveis

- **PCP sobre alfabeto**  $|\Sigma| \geq 2$ : indecidível
- **PCP com dominós ilimitados**: indecidível
#### Variantes Decidíveis

- **PCP unário** ( $|\Sigma| = 1$ ): decidível
- **PCP com no máximo 2 dominós**: decidível
- **PCP com comprimento limitado de solução**: decidível
### Fronteira

- 2 dominós: decidível
- 5 ou mais dominós: indecidível
- 3-4 dominós: ainda em aberto!

{18}------------------------------------------------
### Usando PCP para Provar Indecidibilidade
### Por que PCP é Útil?

- Não envolve Máquinas de Turing explicitamente
- Fácil de relacionar com problemas sobre strings e gramáticas
- Ponto de partida para várias reduções
### Problemas Indecidíveis via Redução de PCP

- Ambiguidade de gramáticas livres de contexto
- Equivalência de gramáticas livres de contexto
- Interseção de linguagens livres de contexto
- Problemas em sistemas de reescrita de termos

{19}------------------------------------------------
### Ambiguidade de GLCs
### Definição

Uma gramática livre de contexto (GLC) é **ambígua** se existe uma string com duas ou mais árvores de derivação distintas.
### Teorema

O problema de decidir se uma GLC é ambígua é **indecidível**.
### Esboço da Prova (Redução de PCP)

Dada instância do PCP com dominós  $\{(t_i, b_i)\}$ :

- Construir GLC  $G_t$  que gera  $\{t_{i_1} \cdots t_{i_n} \# i_n \cdots i_1 \mid i_j \in \{1, \dots, k\}\}$
- Construir GLC  $G_b$  que gera  $\{b_{i_1} \cdots b_{i_n} \# i_n \cdots i_1 \mid i_j \in \{1, \dots, k\}\}$
- A união  $G = G_t \cup G_b$  é ambígua  $\iff$  PCP tem solução

{20}------------------------------------------------
### Equivalência de GLCs
### Teorema

O problema de decidir se duas GLCs  $G_1$  e  $G_2$  geram a mesma linguagem é **indecidível**.
### Prova (Esboço)

- Se pudéssemos decidir equivalência, poderíamos decidir se  $L(G) = \Sigma^*$
- Isso reduziria o PCP (ou  $A_{TM}$ )
### Contraste

Para linguagens **regulares**, equivalência É decidível (minimização de autômatos).

{21}------------------------------------------------
## Resumo: PCP
## O Que Sabemos

- PCP é um problema simples sobre strings e dominós
- PCP é indecidível (redução de  $A_{TM}$ )
- PCP é útil para provar indecidibilidade de outros problemas
- Variantes restritas podem ser decidíveis

{22}------------------------------------------------
### Exercício 1: PCP - Encontrando Soluções

Para cada instância do PCP, encontre uma solução ou argumente por que não existe:

- 1 Dominós:  $\left[ \frac{ab}{a} \right], \left[ \frac{a}{ab} \right], \left[ \frac{b}{b} \right]$
- 2 Dominós:  $\left[ \frac{aa}{a} \right], \left[ \frac{bb}{b} \right]$
- 3 Dominós:  $\left[ \frac{ab}{abb} \right], \left[ \frac{ba}{a} \right], \left[ \frac{a}{bab} \right]$
- 4 Dominós:  $\left[ \frac{1}{111} \right], \left[ \frac{10}{0} \right], \left[ \frac{01}{1} \right]$

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central star, flanked by two vertical panels containing stylized trees. Above the shield is a crown and two crossed scepters. A banner at the bottom reads "AD VERVM DVCIT".

Coat of arms of the University of São Paulo (USP)

{23}------------------------------------------------

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
### Exercício 2: PCP - Análise

- 1 Mostre que se todos os dominós têm  $|t_i| = |b_i|$  (mesmos tamanhos), então o PCP é decidível.
- 2 Mostre que se todos os dominós têm  $|t_i| > |b_i|$ , então a instância não tem solução.
- 3 Por que o PCP sobre alfabeto unário ( $\Sigma = \{a\}$ ) é decidível?
- 4 Suponha que limitamos o comprimento da solução a no máximo  $k$  dominós. Este problema restrito é decidível? Qual sua complexidade?

{24}------------------------------------------------
### Exercício 3: Reduções

- 1 Complete os detalhes da prova de que a ambiguidade de GLCs é indecidível usando redução do PCP.
- 2 Mostre que o problema “ $L(G_1) \cap L(G_2) = \emptyset$ ?” para GLCs  $G_1, G_2$  é indecidível.
- 3 Prove que o problema “ $L(G) = \Sigma^*$ ?” para uma GLC  $G$  é indecidível.  
*Dica:* Relacione com o complemento de uma linguagem construída a partir do PCP.

{25}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

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

<!-- IMAGE_DESCRIPTION: datalab-875c6f4f441fdd3ca7e1908fd1582983_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da Hierarquia de Chomsky mostrando a inclusão entre classes de linguagens.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-c036e2540a94b31357ceb0002f0cacab_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da hierarquia das linguagens de Chomsky, mostrando cinco níveis concêntricos de complexidade crescente.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-fa6c61be003dfbb4ca5587e48a71de94_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

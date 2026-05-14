<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **1 Problema da Correspondência de Post**
- **2 Aplicações e Consequências**
- **3 Exercícios**
- **Introdução ao PCP**
  - Problema da Correspondência de Post (PCP)
  - No contexto de Teoria da Computação
  - Definição do PCP
  - Problema da Correspondência de Post (PCP)
  - Em Outras Palavras
  - Exemplo de Instância de PCP
  - Exemplo de Instância de PCP (contd.)
  - Exemplo de Instância de PCP sem Solução
  - Análise
  - Indecidibilidade do PCP
  - Teorema (Post, 1946)
  - Estratégia da Prova
  - Como a Construção Funciona
  - Famílias de Dominós na Prova
  - Famílias de Dominós na Prova (cont.)
  - Do MPCP para o PCP
  - Moral da Construção
  - Exemplo Completo: Máquina e Computação
  - Exemplo Completo: Montando a História
  - Exemplo Completo: Montando a História (cont.)
  - Exemplo Completo: Fechando a Solução
  - Aceitação
  - Intuição da Construção
  - Funcionamento
  - PCP Modificado (MPCP)
  - MPCP
  - Relação entre MPCP e PCP
  - Redução MPCP $\rightarrow$ PCP
  - Variantes do PCP
  - Usando PCP para Provar Indecidibilidade
  - Por que PCP é Útil?
  - Problemas Indecidíveis via Redução de PCP
  - Ambiguidade de GLCs
  - Definição
  - Teorema
  - Contraste
- **Resumo: PCP**
  - O Que Sabemos
  - Exercício 1: PCP - Encontrando Soluções
  - Exercício 2: PCP - Análise
  - Exercício 3: Reduções
- **Referências I**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Problema da Correspondência de Post

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 14  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

24 de abril de 2026

The logo of the Pontifical Catholic University of Rio Grande do Sul (PUCRS) Escola Politécnica. It features a crest with a shield, a cross, and a sun, with the text "PUCRS" below it. To the right of the crest, the words "ESCOLA POLITÉCNICA" are written in a bold, blue, sans-serif font.

Logo of PUCRS Escola Politécnica

{1}------------------------------------------------
## Sumário
## 1 Problema da Correspondência de Post
## 2 Aplicações e Consequências
## 3 Exercícios

A faint, grayscale watermark of the coat of arms of the University of Coimbra is visible on the right side of the slide. The shield features a central star and is flanked by two sections with a repeating pattern of stylized trees. Above the shield is a crown and two crossed keys. A ribbon at the bottom bears the Latin motto 'AD VERVM DVICIT'.

Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-b6cb8677b4ffb35c6468fa5c24091bff_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
## Introdução ao PCP
### Problema da Correspondência de Post (PCP)

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

$$\left\{ \begin{bmatrix} t_1 \\ b_1 \end{bmatrix}, \begin{bmatrix} t_2 \\ b_2 \end{bmatrix}, \dots, \begin{bmatrix} t_k \\ b_k \end{bmatrix} \right\}$$

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

- Topos:  $a \cdot ca \cdot b \cdot ca = acabca$
- Bases:  $ab \cdot a \cdot ca \cdot a = abacaa$

Erro...

- Topos:  $a \cdot ca \cdot ca \cdot b = acacab$
- Bases:  $ab \cdot a \cdot a \cdot ca = abaaca$

Erro...

{5}------------------------------------------------
### Exemplo de Instância de PCP (contd.)
#### Instância

| Dominó 1       | Dominó 2       | Dominó 3       |
|----------------|----------------|----------------|
| $\frac{b}{ca}$ | $\frac{a}{ab}$ | $\frac{ca}{a}$ |

Solução: sequência 2, 1, 3, 2, 1

- Topos:  $a \cdot b \cdot ca \cdot a \cdot b = abcaab$
  - Bases:  $ab \cdot ca \cdot a \cdot ab = abcaab$  ✓
#### Observação

Encontrar soluções pode ser “difícil” e, para algumas instâncias, **não existe solução**.

{6}------------------------------------------------
### Exemplo de Instância de PCP sem Solução
#### Instância

| Dominó 1  | Dominó 2   |
|-----------|------------|
| <u>ab</u> | <u>bab</u> |
| aba       | ab         |
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

- Uma configuração é escrita como  $\#u q a v\#$ : a fita contém  $uav$ , a cabeça lê  $a$ , e o estado atual é  $q$ .
- Se a computação aceitante for

$$C_0 \vdash C_1 \vdash \dots \vdash C_t,$$

queremos produzir

$$\text{topo} = \#C_0\#C_1\#\dots\#C_{t-1}\# \quad \text{base} = \#C_0\#C_1\#\dots\#C_t\#.$$

- A base fica uma configuração à frente; se  $C_t$  é aceitante, dominós especiais permitem ao topo consumir esse último sufixo.

Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'D VERVM DVCT'.

{9}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-69acc34af53b0a86e532d491025d5f77_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a cross and the motto 'D VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
### Famílias de Dominós na Prova
#### ■ Inicial:

$$\left[ \begin{array}{c} \# \\ \#q_0w\# \end{array} \right]$$
#### ■ Cópia:

$$\left[ \begin{array}{c} a \\ a \end{array} \right] \quad a \in \Gamma \cup \{\#\}$$
#### ■ Transição à direita:

$$\delta(q, a) = (r, b, R) \Rightarrow \left[ \begin{array}{c} qa \\ br \end{array} \right]$$

- Para movimento à esquerda, usa-se uma família um pouco maior para também copiar o vizinho à esquerda.

The image is a watermark of the University of Coimbra's coat of arms. It features a shield with a cross and a central emblem, topped by a crown and flanked by two figures. Below the shield is a ribbon with the Latin motto "AD VERVM DVCT".

Watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVCT'.

{10}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-bd8e3fb102fd14e1edbc62f149241842_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
### Famílias de Dominós na Prova (cont.)
#### Dominós de Aceitação

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

$$C_0 = q_0 0 1 \# \vdash C_1 = X q_1 1 \# \vdash C_2 = X 1 q_{acc} \#$$
#### Dominós Necessários

$$s = \begin{bmatrix} \# \\ \#q_001\# \end{bmatrix}, \quad t_1 = \begin{bmatrix} q_00 \\ Xq_1 \end{bmatrix}, \quad t_2 = \begin{bmatrix} q_11 \\ 1q_{acc} \end{bmatrix}$$

$$c_X = \begin{bmatrix} X \\ X \end{bmatrix}, \quad c_1 = \begin{bmatrix} 1 \\ 1 \end{bmatrix}, \quad c_{\#} = \begin{bmatrix} \# \\ \# \end{bmatrix}$$

{12}------------------------------------------------
### Exemplo Completo: Montando a História
#### Fase 1: Forçar a Configuração Inicial

$$s = \left[ \frac{\#}{\#q_001\#} \right] \Rightarrow \text{topo} = \# \quad \text{base} = \#q_001\#$$
#### Fase 2: Simular $C_0 \vdash C_1$

Escolhemos

$$t_1, c_1, c_{\#}$$

Isso acrescenta ao topo  $q_0 \ 01\#$  e à base  $Xq_1 \ 1\#$ . Logo:

topo = #q<sub>0</sub>01#      base = #q<sub>0</sub>01#Xq<sub>1</sub>1#

{13}------------------------------------------------
### Exemplo Completo: Montando a História (cont.)
#### Fase 3: Simular $C_1 \vdash C_2$

Escolhemos

$$c_X, t_2, c_{\#}$$

e obtemos:

topo = # $q_0$ 01# $Xq_1$ 1#

base =  $\#q_001\#Xq_11\#X1q_{acc}\#$
#### Padrão

Ao final de cada fase, a base fica exatamente uma configuração à frente do topo.

{14}------------------------------------------------
### Exemplo Completo: Fechando a Solução
#### Último Passo

Depois de simular a computação:

topo = #C<sub>0</sub>#C<sub>1</sub>#      base = #C<sub>0</sub>#C<sub>1</sub>#C<sub>2</sub>#

onde  $C_2 = X1q_{acc}\#$  é aceitante.
### Aceitação

Os dominós de aceitação fazem  $q_{acc}$  absorver os vizinhos:

$$X_{1q_{acc}\#} \implies X_{q_{acc}\#} \implies q_{acc}\# \implies \#$$

Assim, o topo consome o sufixo aceitante que faltava, e a solução codifica exatamente

$$\#q_0 01\# \vdash \#Xq_1 1\# \vdash \#X1q_{acc}\#.$$

{15}------------------------------------------------
### Intuição da Construção

Topo:

#

Base:

# $q_0 w$ #

O topo "corre atrás" →  
da base
### Funcionamento

- A base sempre está “na frente” do topo
  - Dominós de transição fazem a base avançar simulando  $M$
  - Se  $M$  aceita, dominós especiais permitem o topo “alcançar” a base
  - Se  $M$  não aceita, o topo nunca alcança a base

{16}------------------------------------------------
### PCP Modificado (MPCP)
### MPCP

Versão do PCP onde o primeiro domínio da sequência deve ser o domínio 1.
### Relação entre MPCP e PCP

- 1  $A_{TM} \leq_m MPCP$  (mais fácil de provar)
  - 2  $MPCP \leq_m PCP$  (redução técnica)

Logo,  $A_{TM} \leq_m PCP$ , e PCP é indecidível.
### Redução MPCP $\rightarrow$ PCP

Adicionar marcadores especiais que forçam o dominó 1 a ser escolhido primeiro, sem essa restrição explícita.

{17}------------------------------------------------
### Variantes do PCP
#### Variantes Indecidíveis

- PCP sobre alfabeto  $|\Sigma| \geq 2$ : indecidível
  - PCP com dominós ilimitados: indecidível
#### Variantes Decidíveis

- **PCP unário** ( $|\Sigma| = 1$ ): decidível
  - **PCP com no máximo 2 dominós**: decidível
  - **PCP com comprimento limitado de solução**: decidível
#### Fronteira

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
#### Esboço da Prova (Redução de PCP)

Dada instância do PCP com dominós  $\{(t_i, b_i)\}$ :

- Construir GLC  $G_t$  que gera  $\{t_{i_1} \cdots t_{i_n} \# i_n \cdots i_1 \mid i_j \in \{1, \dots, k\}\}$
  - Construir GLC  $G_b$  que gera  $\{b_{i_1} \cdots b_{i_n} \# i_n \cdots i_1 \mid i_j \in \{1, \dots, k\}\}$
  - A união  $G = G_t \cup G_b$  é ambígua  $\iff$  PCP tem solução

{20}------------------------------------------------
#### Equivalência de GLCs
#### Teorema

O problema de decidir se duas GLCs  $G_1$  e  $G_2$  geram a mesma linguagem é **indecidível**.
#### Prova (Esboço)

- Se pudéssemos decidir equivalência, poderíamos decidir se  $L(G) = \Sigma^*$
  - Isso reduziria o PCP (ou  $A_{TM}$ )
### Contraste

Para linguagens **regulares**, equivalência É decidível (minimização de autômatos).

{21}------------------------------------------------
## Resumo: PCP
### O Que Sabemos

- PCP é um problema simples sobre strings e dominós
- PCP é indecidível (redução de  $A_{TM}$ )
- PCP é útil para provar indecidibilidade de outros problemas
- Variantes restritas podem ser decidíveis

A faint, grayscale watermark of the University of Coimbra seal is visible in the background. The seal features a central shield with a five-pointed star, flanked by two figures. Above the shield is a crown, and below it is a ribbon with the Latin motto "AD VERVM DVCTIT".

Faint background watermark of the University of Coimbra seal, featuring a star and the motto 'AD VERVM DVCTIT'.

{22}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-5756508641ee599941f6d1e85de7e84b_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the University of Coimbra seal, featuring a star and the motto 'AD VERVM DVCTIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 1: PCP - Encontrando Soluções

Para cada instância do PCP, encontre uma solução ou argumente por que não existe:

- 1 Dominós:  $\left[ \frac{ab}{a} \right], \left[ \frac{a}{ab} \right], \left[ \frac{b}{b} \right]$
- 2 Dominós:  $\left[ \frac{aa}{a} \right], \left[ \frac{bb}{b} \right]$
- 3 Dominós:  $\left[ \frac{ab}{abb} \right], \left[ \frac{ba}{a} \right], \left[ \frac{a}{bab} \right]$
- 4 Dominós:  $\left[ \frac{1}{111} \right], \left[ \frac{10}{0} \right], \left[ \frac{01}{1} \right]$

A faint, large watermark of the coat of arms of the University of Coimbra is visible in the background. It features a shield with a star and the motto 'AD VERVM DVOCIT' on a ribbon below. The shield is flanked by two figures, and the entire emblem is rendered in a light gray color.

Faint watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{23}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-0ab720844e454afef91e5d68f4ab8ad9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: PCP - Análise

- 1 Mostre que se todos os dominós têm  $|t_i| = |b_i|$  (mesmos tamanhos), então o PCP é decidível.
- 2 Mostre que se todos os dominós têm  $|t_i| > |b_i|$ , então a instância não tem solução.
- 3 Por que o PCP sobre alfabeto unário ( $\Sigma = \{a\}$ ) é decidível?
- 4 Suponha que limitamos o comprimento da solução a no máximo  $k$  dominós. Este problema restrito é decidível? Qual sua complexidade?

A faint, grayscale watermark of the University of Coimbra's coat of arms is visible in the background. It features a shield with a cross and a star, topped by a crown and flanked by two figures. Below the shield is a ribbon with the Latin motto 'AD VERVM DVOCIT'.

Faint background watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

{24}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-a95bbb7c401e0f3ee7e6c1a870f4917c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-03d99823cac9b0c49db95d65dc155d8c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 3: Reduções

- 1 Complete os detalhes da prova de que a ambiguidade de GLCs é indecidível usando redução do PCP.
- 2 Mostre que o problema " $L(G_1) \cap L(G_2) = \emptyset$ ?" para GLCs  $G_1, G_2$  é indecidível.
- 3 Prove que o problema " $L(G) = \Sigma^*$ ?" para uma GLC  $G$  é indecidível.  
*Dica:* Relacione com o complemento de uma linguagem construída a partir do PCP.

A faint, grayscale watermark of the University of Coimbra's coat of arms is visible in the background. It features a shield with a cross and a star, flanked by two figures. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT".

Faint background watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

{25}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

A faint, semi-transparent watermark of the University of Coimbra's coat of arms is visible in the background. It features a shield with a cross and the motto 'AD VERVM DVCT' on a ribbon below.

Faint background watermark of the University of Coimbra crest, featuring a shield with a cross and the motto 'AD VERVM DVCT'.

<!-- IMAGE_DESCRIPTION: datalab-55fb58e14ec092ccc4fe111de0dc6278_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the University of Coimbra crest, featuring a shield with a cross and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-84a1d09fb489061482111515543b60dc_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS Escola Politécnica
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

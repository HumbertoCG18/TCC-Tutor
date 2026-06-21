<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Duas Visões de Computação**
- **MT como Reconhecedor de Linguagens**
- **MT como Computador de Funções**
- **Equivalência**
- **Funções Turing-Computáveis**
  - Definição
  - Convenção para Funções Numéricas
  - Exemplos de Funções Computáveis
  - Funções Totais vs. Parciais
  - Correspondência com MTs
  - Composição de Funções Computáveis
  - Teorema
- **Funções de Múltiplas Variáveis**
  - Codificação de Tuplas
  - Opções de Codificação
  - Independência da Codificação
  - Codificando MTs como Cadeias
  - Motivação
  - Exemplo de Codificação
  - Uma Codificação Simples
  - Propriedades da Codificação
  - Bijeção Parcial
  - Convenção
- **Enumeração de MTs**
- **A Máquina de Turing Universal**
  - Teorema (Turing, 1936)
  - Funcionamento de $U$
  - Implementação da MT Universal
  - Consequências da MT Universal
  - Programabilidade
  - Auto-Referência
  - Numeração de Gödel
  - Ideia
  - Função Universal
  - Definição
  - Pergunta
  - Teorema da Equivalência
  - A Tese de Church-Turing
  - Outros Modelos Equivalentes
  - Máquinas de Registradores (RAM)
  - Sistemas de Reescrita
  - Implicações da Equivalência
  - Robustez da Definição
  - Limites Absolutos
  - Fundamentos Sólidos
  - Funções Computáveis vs. Não-Computáveis
  - Funções Não-Computáveis (exemplos)
- **Resumo: Equivalências**
  - Todos Caracterizam a Mesma Classe
- **Exercício 1: Funções Computáveis**
  - Exercício 2: Codificação
  - Exercício 3: MT Universal
  - Exercício 4: Equivalência de Modelos
  - Exercício 5: Funções e Linguagens
- **Desafio: Teorema s-m-n com MTs**
- **Referências I**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Máquinas de Turing como Processadoras de Funções

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 08

Teoria da Computabilidade e Complexidade  
Ciência da Computação

1 de abril de 2026

The logo of PUCRS, featuring a shield with a cross and a star, and the text 'PUCRS' below it.

Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

{1}------------------------------------------------
## Sumário

- 1 Máquinas de Turing e Funções
- 2 Codificação de Máquinas de Turing
- 3 Equivalência com Funções Recursivas
- 4 Exercícios

The image is a faint, light gray watermark of the Coat of Arms of Brazil. It features a central shield with a green field containing a white five-pointed star and a gold field containing a white cross. The shield is surmounted by a crown and flanked by two crossed keys. A ribbon at the bottom contains the motto 'AD VERVM DVCIT'.

Coat of arms of Brazil

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-cb00037bd3b3af9720d5551ad2f818dd_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of Brazil
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-a4f8ab9085cf6977168da3fa62e04b7e_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of Brazil
<!-- /IMAGE_DESCRIPTION -->
## Duas Visões de Computação
## MT como Reconhecedor de Linguagens

- Entrada: cadeia  $w$
- Saída: Aceita ou Rejeita (ou loop)
- Decide se  $w \in L$
## MT como Computador de Funções

- Entrada: valor  $x$  (codificado como cadeia)
- Saída: valor  $f(x)$  na fita (ou loop)
- Computa uma função  $f : \mathbb{N}^k \rightarrow \mathbb{N}$
## Equivalência

As duas visões são equivalentes! Podemos converter problemas de linguagens em problemas de funções e vice-versa.

{3}------------------------------------------------
## Funções Turing-Computáveis
### Definição

Uma função parcial  $f : \Sigma^* \rightarrow \Sigma^*$  é **Turing-computável** se existe uma MT  $M$  tal que, para toda entrada  $w$ :

- Se  $f(w)$  está definida:  $M$  para com  $f(w)$  na fita
- Se  $f(w)$  não está definida:  $M$  não para
### Convenção para Funções Numéricas

Para  $f : \mathbb{N}^k \rightarrow \mathbb{N}$ :

- Entrada:  $(n_1, \dots, n_k)$  codificado como  $\text{bin}(n_1)\# \dots \# \text{bin}(n_k)$
- Ou em unário:  $1^{n_1}\# \dots \# 1^{n_k}$
- Saída:  $f(n_1, \dots, n_k)$  na mesma codificação

{4}------------------------------------------------
### Exemplos de Funções Computáveis
#### Função Sucessora

$$S(n) = n + 1$$

MT (em unário): adicione um 1 ao final da entrada.
#### Adição

$$\text{add}(m, n) = m + n$$

MT (em unário): substitua # por 1, apague um 1.

$$1^m \# 1^n \rightarrow 1^{m+n}$$
#### Multiplicação

$$\text{mult}(m, n) = m \times n$$

MT: copie  $1^n$  um total de  $m$  vezes.
#### Função Parcial

$f(x) = x/2$  se  $x$  é par, indefinida caso contrário.

MT: remove 1s de dois em dois; se sobrar 1, loop infinito.

{5}------------------------------------------------
### Funções Totais vs. Parciais
#### Função Total

Uma função é **total** se está definida para todas as entradas do domínio.

Exemplo:  $f(n) = n + 1$  é total em  $\mathbb{N}$ .
#### Função Parcial

Uma função é **parcial** se pode não estar definida para algumas entradas.

Exemplo:  $f(x, y) = x/y$  é parcial (indefinida quando  $y = 0$ ).
### Correspondência com MTs

- Função total  $\leftrightarrow$  MT que sempre para
- Função parcial  $\leftrightarrow$  MT que pode não parar

{6}------------------------------------------------
### Composição de Funções Computáveis
### Teorema

Se  $f : \Sigma^* \rightarrow \Sigma^*$  e  $g : \Sigma^* \rightarrow \Sigma^*$  são Turing-computáveis, então  $g \circ f$  também é.
#### Prova

Sejam  $M_f$  e  $M_g$  MTs que computam  $f$  e  $g$ .

Construa  $M_{g \circ f}$ :

- 1 Execute  $M_f$  na entrada  $w$
- 2 Se  $M_f$  para com resultado  $f(w)$ , execute  $M_g$  em  $f(w)$
- 3 Se  $M_g$  para com resultado  $g(f(w))$ , pare com este resultado

Se  $f(w) \uparrow$  ou  $g(f(w)) \uparrow$ , então  $(g \circ f)(w) \uparrow$ .  $\square$

{7}------------------------------------------------
## Funções de Múltiplas Variáveis
### Codificação de Tuplas

Para computar  $f : \mathbb{N}^k \rightarrow \mathbb{N}$ , precisamos codificar  $(n_1, \dots, n_k)$  como uma única cadeia.
### Opções de Codificação

- 1 **Separador:**  $\text{bin}(n_1)\# \text{bin}(n_2)\# \dots \# \text{bin}(n_k)$
- 2 **Unário:**  $1^{n_1}01^{n_2}0 \dots 01^{n_k}$
- 3 **Função de pareamento:** usar  $\langle n_1, n_2 \rangle$  recursivamente
### Independência da Codificação

Diferentes codificações “razoáveis” resultam na mesma classe de funções computáveis, pois podemos converter entre codificações com MTs.

{8}------------------------------------------------
### Codificando MTs como Cadeias
### Motivação

Para estudar MTs “sobre” MTs (como a MT Universal), precisamos representar MTs como cadeias.
#### Ideia

Uma MT  $M = (Q, \Sigma, \Gamma, \delta, q_0, q_{acc}, q_{rej})$  é um objeto finito:

- Finitos estados: enumere como  $q_0, q_1, \dots, q_n$
- Finito alfabeto: enumere símbolos
- Finitas transições: liste cada  $\delta(q_i, a) = (q_j, b, D)$

Toda esta informação pode ser escrita como uma cadeia!
#### Notação

$\langle M \rangle$  = codificação da MT  $M$  como cadeia.

$\langle M, w \rangle$  = codificação do par (MT  $M$ , entrada  $w$ ).

{9}------------------------------------------------
### Exemplo de Codificação
### Uma Codificação Simples

Assuma alfabeto binário para a codificação.

- Estados:  $q_i$  codificado como  $0^{i+1}$
- Símbolos de  $\Gamma$ :  $a_j$  codificado como  $0^{j+1}$
- Direções:  $L = 0$ ,  $R = 1$
- Transição  $\delta(q_i, a_j) = (q_k, a_l, D)$ :  
codificada como  $0^{i+1}10^{j+1}10^{k+1}10^{l+1}1D$
- Transições separadas por 11
- MT completa: 111*transições*111
#### Observação

A codificação específica não importa muito, o importante é que:

- 1 Seja possível recuperar  $M$  a partir de  $\langle M \rangle$
- 2 O processo de codificação/decodificação seja computável

{10}------------------------------------------------
### Propriedades da Codificação
### Bijeção Parcial

Nem toda cadeia é uma codificação válida de MT.

Seja  $TM = \{\langle M \rangle : M \text{ é uma MT válida}\}$ .

TM é decidível (podemos verificar se uma cadeia é codificação válida).
### Convenção

Quando uma MT recebe entrada  $\langle M \rangle$  que não é codificação válida, convencionamos que ela rejeita.
## Enumeração de MTs

Como  $TM \subseteq \{0, 1\}^*$  e  $\{0, 1\}^*$  é enumerável, o conjunto de todas as MTs é **enumerável**.

Podemos listar:  $M_0, M_1, M_2, \dots$

{11}------------------------------------------------
## A Máquina de Turing Universal
### Teorema (Turing, 1936)

Existe uma MT  $U$  (chamada **Universal**) tal que:

$$U(\langle M, w \rangle) = M(w)$$

para toda MT  $M$  e entrada  $w$ .
### Funcionamento de $U$

Na entrada  $\langle M, w \rangle$ :

- 1 Verifica se  $\langle M \rangle$  é codificação válida
- 2 Simula  $M$  passo a passo na entrada  $w$
- 3 Se  $M$  aceita,  $U$  aceita
- 4 Se  $M$  rejeita,  $U$  rejeita
- 5 Se  $M$  não para,  $U$  não para

{12}------------------------------------------------
### Implementação da MT Universal
#### Estrutura de $U$ (3 fitas)

- **Fita 1:** Descrição de  $M$  (transições)
- **Fita 2:** Fita simulada de  $M$  (conteúdo atual)
- **Fita 3:** Estado atual de  $M$
#### Simulação de um Passo

- 1 Leia o símbolo atual na Fita 2
- 2 Consulte as transições na Fita 1 para o estado na Fita 3
- 3 Encontre a transição aplicável
- 4 Atualize: símbolo na Fita 2, posição, estado na Fita 3
#### Importância

$U$  é um **interpretador**: um programa que executa outros programas. É a base teórica para computadores de propósito geral!

{13}------------------------------------------------
### Consequências da MT Universal
### Programabilidade

Um único dispositivo (a MT Universal) pode simular qualquer computação, desde que receba a “descrição do programa”.  
Esta é a ideia por trás dos computadores modernos!
### Auto-Referência

MTs podem operar sobre descrições de outras MTs (ou de si mesmas).

Isso leva a resultados profundos:

- Problema da Parada
- Teorema da Recursão
- Teoremas de Incompletude de Gödel

{14}------------------------------------------------
### Numeração de Gödel
### Ideia

Cada MT pode ser associada a um número natural único:

$$M \mapsto e \text{ onde } e = \text{número correspondente a } \langle M \rangle$$
#### Notação

- $M_e$  = a MT com número  $e$
- $\varphi_e$  = a função computada por  $M_e$
- $W_e = L(M_e)$  = linguagem reconhecida por  $M_e$
### Função Universal

A função universal  $\Phi : \mathbb{N}^2 \rightarrow \mathbb{N}$ :

$$\Phi(e, x) = \varphi_e(x)$$

é computável (pela MT Universal).

{15}------------------------------------------------
#### Recordando: Funções Recursivas Parciais
### Definição

As funções  $\mu$ -recursivas (recursivas parciais) são construídas a partir de:

- Funções básicas:  $Z$ ,  $S$ ,  $P_i^k$
- Composição
- Recursão primitiva
- Minimização ( $\mu$ )
### Pergunta

As funções Turing-computáveis são exatamente as funções recursivas parciais?

**Resposta: SIM!**

Este é um dos resultados fundamentais da teoria da computabilidade.

{16}------------------------------------------------
### Teorema da Equivalência
#### Teorema

Uma função  $f : \mathbb{N}^k \rightarrow \mathbb{N}$  é Turing-computável se e somente se é  $\mu$ -recursiva.
#### Prova (Esboço)
#### **( $\mu$ -recursiva $\Rightarrow$ Turing-computável)**

- Funções básicas são claramente computáveis por MTs
- Composição: execute MTs em sequência
- Recursão primitiva: use loop com contador
- Minimização: busca sequencial (while)
#### **(Turing-computável $\Rightarrow$ $\mu$ -recursiva)**

- Codifique configurações de MT como números
- A função “próxima configuração” é recursiva primitiva
- Use minimização para encontrar configuração de parada

{17}------------------------------------------------
### A Tese de Church-Turing
#### Tese (Não é teorema!)

A noção informal de “função efetivamente computável” coincide com a noção formal de “função Turing-computável” (equivalentemente,  $\mu$ -recursiva).
#### Evidências

- Todos os modelos de computação propostos são equivalentes:
  - Máquinas de Turing
  - Funções  $\mu$ -recursivas
  - Cálculo Lambda
  - Máquinas de Post
  - Máquinas RAM
- Nenhuma função “intuitivamente computável” escapa da definição
- Computadores físicos possuem mesma expressividade de MTs

{18}------------------------------------------------
### Outros Modelos Equivalentes
#### Cálculo Lambda (Church, 1936)

Modelo baseado em funções e aplicação.

- Termos: variáveis,  $\lambda x.M$ ,  $(M N)$
- Computação:  $\beta$ -redução
- Base para linguagens funcionais (Lisp, Haskell)
### Máquinas de Registradores (RAM)

Modelo próximo a computadores reais:

- Registradores ilimitados
- Instruções: INC, DEC, JZ (jump if zero)
- Base para linguagens imperativas
### Sistemas de Reescrita

Gramáticas irrestritas (Tipo 0) geram exatamente linguagens r.e.

{19}------------------------------------------------
### Implicações da Equivalência
### Robustez da Definição

A classe das funções computáveis é “natural” — não depende do modelo específico escolhido.
### Limites Absolutos

Resultados de impossibilidade (como indecidibilidade do Halting Problem) valem para **qualquer** modelo de computação!
### Fundamentos Sólidos

Podemos usar o modelo mais conveniente para cada situação:

- MTs para provas de impossibilidade
- Funções recursivas para definições matemáticas
- RAM para análise de complexidade

{20}------------------------------------------------
### Funções Computáveis vs. Não-Computáveis
#### Funções Computáveis (exemplos)

- Aritmética:  $+$ ,  $\times$ ,  $!$ , primos, gcd
- Strings: concatenação, reverso, palíndromo
- Ackermann: total mas cresce muito rápido
- Busy Beaver parcial:  $BB'(n) = BB(n)$  se  $n \leq 4$ , indefinida caso contrário
### Funções Não-Computáveis (exemplos)

- Busy Beaver:  $BB(n)$  = maior output de MT com  $n$  estados
- Função de Parada:  $h(e, x) = 1$  se  $\varphi_e(x) \downarrow$ , 0 caso contrário
- Kolmogorov:  $K(x)$  = menor programa que gera  $x$
- Função característica de qualquer conjunto r.e. não-decidível

{21}------------------------------------------------
## Resumo: Equivalências

```
graph TD; MT[Máquinas de Turing] <--> FR[Funções $\mu$-recursivas]; CL[Cálculo Lambda] <--> GT[Gramáticas Tipo 0]; MT <--> CL; MT <--> GT; FR <--> CL; FR <--> GT;
```

Diagram showing the equivalence between four computational models: Máquinas de Turing, Funções $\mu$-recursivas, Cálculo Lambda, and Gramáticas Tipo 0. All four models are interconnected with double-headed arrows, indicating that they all characterize the same class of computable functions.

<!-- IMAGE_DESCRIPTION: datalab-7d3d5fb5d09c0cd35a9d637be241651e_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram showing the equivalence between four computational models: Máquinas de Turing, Funções μ-recursivas, Cálculo Lambda, and Gramáticas Tipo 0.
<!-- /IMAGE_DESCRIPTION -->
### Todos Caracterizam a Mesma Classe

- Funções computáveis = Turing-computáveis =  $\mu$ -recursivas
- Linguagens r.e. = Turing-reconhecíveis = Tipo 0
- Linguagens decidíveis = Turing-decidíveis = recursivas

{22}------------------------------------------------
## Exercício 1: Funções Computáveis

Mostre que as seguintes funções são Turing-computáveis, descrevendo (em alto nível) uma MT que as computa:

- 1  $f(n) = 2n$  (dobro, em unário)
- 2  $g(n) = \lfloor n/2 \rfloor$  (metade inteira)
- 3  $h(m, n) = m^n$  (exponenciação)
- 4  $p(n)$  =  $n$ -ésimo número primo
- 5  $\text{gcd}(m, n)$  = máximo divisor comum

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central vertical band containing a stylized 'M' and 'U' monogram. The shield is flanked by two crossed flags (one green and gold, the other red and green) and topped by a crown. A banner at the bottom reads 'AD VERVM DVCIT'.

Coat of arms of the University of São Paulo (USP)

{23}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-0ab720844e454afef91e5d68f4ab8ad9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-03d99823cac9b0c49db95d65dc155d8c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-55fb58e14ec092ccc4fe111de0dc6278_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-87d9833379b490461fb3451cf389cb4a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Codificação

- 1** Dada a MT com estados  $\{q_0, q_1, q_{acc}\}$ , alfabeto  $\{0, 1, \sqcup\}$ , e transições:
- $\delta(q_0, 0) = (q_1, 1, R)$
  - $\delta(q_1, 1) = (q_0, 0, L)$
  - $\delta(q_0, \sqcup) = (q_{acc}, \sqcup, R)$

Escreva uma possível codificação  $\langle M \rangle$  usando a convenção da aula.

- 2** Dada a cadeia  $\langle M \rangle$ , como você verifica se ela é uma codificação válida de MT?
- 3** Por que a verificação de validade de  $\langle M \rangle$  é decidível?

{24}------------------------------------------------
### Exercício 3: MT Universal

- 1 Explique por que a MT Universal  $U$  precisa de pelo menos 2 fitas (ou recursos equivalentes) para funcionar eficientemente.
- 2 Se  $M$  é uma MT que sempre para,  $U$  sempre para na entrada  $\langle M, w \rangle$ ? Justifique.
- 3 Se  $U(\langle M, w \rangle)$  aceita, o que podemos concluir sobre  $M$  e  $w$ ?
- 4 Descreva o que acontece quando executamos  $U(\langle U, \langle U, w \rangle \rangle)$  — uma MT Universal simulando ela mesma.

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a large five-pointed star in the center. The shield is flanked by two figures, possibly representing the university's history or values. Above the shield is a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{25}------------------------------------------------
### Exercício 4: Equivalência de Modelos

- 1 Mostre como simular a função básica  $S(n) = n + 1$  usando uma MT (em unário).
- 2 Mostre como simular composição  $f = g \circ h$  com MTs, dadas MTs para  $g$  e  $h$ .
- 3 Mostre como simular minimização  $f(x) = \mu y[g(x, y) = 0]$  com uma MT, dada MT para  $g$ .
- 4 Por que a simulação de recursão primitiva não introduz loops infinitos, mas a de minimização pode?

The image shows the coat of arms of the University of São Paulo (USP). It features a central shield with a white background and a pattern of green pine trees. Above the shield is a crown, and on either side are two crossed keys. Below the shield is a banner with the Latin motto 'AD VERVM DVCT'.

Coat of arms of the University of São Paulo (USP)

{26}------------------------------------------------
### Exercício 5: Funções e Linguagens

- 1 Se  $f : \mathbb{N} \rightarrow \mathbb{N}$  é computável total, mostre que o conjunto  $\{(x, f(x)) : x \in \mathbb{N}\}$  (o grafo de  $f$ ) é decidível.
- 2 Se  $L$  é decidível, mostre que sua função característica  $\chi_L$  é computável total.
- 3 Se  $f : \mathbb{N} \rightarrow \mathbb{N}$  é computável e  $A = \{x : f(x) = 0\}$ , o que podemos afirmar sobre  $A$ ? É sempre decidível? É sempre reconhecível?
- 4 Dê exemplo de função  $f$  computável tal que  $\{x : f(x) = 0\}$  é reconhecível mas não decidível.

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a blue field containing a white star and a red field containing a white cross. The shield is surmounted by a crown and flanked by two golden lions. A banner at the bottom reads "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{27}------------------------------------------------
## Desafio: Teorema s-m-n com MTs

O **Teorema s-m-n** afirma que existe função computável  $s$  tal que:

$$\varphi_{s(e,y)}(x) = \varphi_e(x, y)$$

- 1 Interprete este teorema em termos de MTs: o que  $s(e, y)$  representa?
- 2 Descreva como construir uma MT que computa  $s$ :
  - Entrada:  $\langle M_e, y \rangle$
  - Saída:  $\langle M' \rangle$  onde  $M'(x) = M_e(x, y)$
- 3 Este teorema é usado para provar o Teorema do Ponto Fixo (Recursão). Pesquise e explique a conexão.

{28}------------------------------------------------
## Referências I

The image is a faded, light gray watermark of the official coat of arms of Brazil. It features a central shield with a green field containing a large white star and a gold field containing a white cross. The shield is flanked by two golden branches of coffee and tobacco. Above the shield is a golden crown. A blue ribbon at the bottom of the shield contains the Latin motto 'AD VERVM DVCIT'.

Coat of arms of Brazil

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-1d7527f4316cfe2d342b08d1653d1592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

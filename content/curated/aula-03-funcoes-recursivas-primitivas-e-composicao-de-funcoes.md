<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Motivação**
- **Questão Central**
- **A Tese de Church-Turing**
  - Tese de Church-Turing
  - Observação
- **Funções Recursivas: Visão Geral**
- **Abordagem**
  - Hierarquia de Classes
  - Domínio das Funções
  - Convenção
  - Notação
- **As Três Funções Básicas**
  - 1. Função Zero
  - 2. Função Sucessora
  - 3. Funções de Projeção
  - Funções de Projeção
  - Conexão com Axiomas de Peano
  - Axiomas de Peano (simplificado)
  - Relação
- **Operação 1: Composição**
  - Definição
  - Notação
  - Intuição
  - Exemplos de Composição
- **Operação 2: Recursão Primitiva**
  - Definição
  - Notação
  - Estrutura
  - Visualização da Recursão Primitiva
  - Definição Indutiva
  - Propriedades das Funções Recursivas Primitivas
  - Exemplos
  - Somatório e Produtório Limitados
  - Teorema
  - Quantificação Limitada (Universal e Existencial)
  - Teorema
  - Construção
- **Importante**
- **Resumo: Funções Recursivas Primitivas**
  - O que Conseguimos Definir
- **Próxima Aula**
  - Exercício 1: Funções Básicas
  - Exercício 2: Construções por Composição
  - Exercício 3: Recursão Primitiva
  - Desafio!
  - Exercício 4: Predicados
  - Exercício 5: Busca Limitada
  - Exercício 6: Codificação de Pares
  - Exercício 7: Função de Ackermann
- **Importante**
- **Referências I**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Funções Recursivas Primitivas; Composição de Funções

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 03

Teoria da Computabilidade e Complexidade  
Ciência da Computação

25 de fevereiro de 2026

The logo of PUCRS, featuring a shield with a cross and a star, and the text "PUCRS" below it.

Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

{1}------------------------------------------------
## Sumário

- 1 Introdução
- 2 Funções Básicas
- 3 Composição e Recursão Primitiva
- 4 Exemplos de Funções Recursivas Primitivas
- 5 Exercícios

The image is a large, light gray watermark of the coat of arms of the University of São Paulo (USP). It features a shield with a central vertical band containing a stylized 'M' and a star. The shield is flanked by two crossed keys (the keys of St. Peter) and topped with a crown. A banner at the bottom reads 'AD VERVM DVCIT'.

Coat of arms of the University of São Paulo (USP)

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-317e0525ef1b2458976c246876f4a948_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-c092f712a80ce3310c5e29d0fa0e454a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-5f5807dc5366ae1d316a6f93e0f583c4_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->
## Motivação
## Questão Central

O que significa uma função ser **computável**?

- Antes dos computadores, matemáticos buscavam formalizar a noção de computação
- David Hilbert e Wilhelm Ackermann (1928):  
**Entscheidungsproblem**, *existe um procedimento mecânico que decida se uma fórmula lógica é universalmente válida?*
  - Universalmente válida: verdadeira em todas as interpretações e modelos; sua negação deve ser uma contradição!
  - Gödel (1931) considera universalmente válida uma fórmula que é provável utilizando lógica de primeira-ordem.
- Várias formalizações independentes surgiram nos anos 1930:
  - **Funções recursivas** (Gödel, 1931; Kleene, 1936)
  - **Cálculo- $\lambda$**  (Alonzo Church, 1930/1936)
  - **Máquinas de Turing** (Turing, 1936)
- **As três formalizações acima são equivalentes!**

{3}------------------------------------------------
## A Tese de Church-Turing
### Tese de Church-Turing

Uma função é **efetivamente computável** se e somente se é computável por uma Máquina de Turing (ou equivalentemente, é uma função recursiva).
### Observação

Esta é uma **tese**, não um teorema e não pode ser provada matematicamente, pois o termo “efetivamente computável” não é um conceito informal.

No entanto, há evidências para afirmar que:

- Todos os modelos de computação propostos são equivalentes
- Nenhuma função intuitivamente computável sai da definição
- Computadores físicos são equiparáveis a máquinas de turing

{4}------------------------------------------------
## Funções Recursivas: Visão Geral
## Abordagem

Definir uma classe de funções computáveis através de:

- 1 Um conjunto de **funções básicas** (claramente computáveis)
- 2 **Operações** que preservam computabilidade
### Hierarquia de Classes

- 1 **Funções Recursivas Primitivas** — obtidas por composição e recursão primitiva
- 2 **Funções Recursivas Parciais** — adicionam a operação de minimização; sem garantia de “parada”
- 3 **Funções Recursivas (Totais)** — recursivas parciais que são totais; cada entrada possui um valor de saída correspondente

{5}------------------------------------------------
### Domínio das Funções
### Convenção

Trabalharemos com funções  $f : \mathbb{N}^k \rightarrow \mathbb{N}$ , onde:

- $\mathbb{N} = \{0, 1, 2, 3, \dots\}$
- $k \geq 0$ , aridade (número de argumentos)
- $k = 0$ , constantes
### Notação

- $f^{(k)}$  indica que  $f$  tem aridade  $k$
- $\vec{x}$  denota  $(x_1, x_2, \dots, x_k)$
- $f(\vec{x})$  é abreviação de  $f(x_1, \dots, x_k)$

{6}------------------------------------------------
## As Três Funções Básicas
### 1. Função Zero

$$Z : \mathbb{N} \rightarrow \mathbb{N}$$

$$Z(x) = 0$$

Retorna zero, independentemente da entrada.
### 2. Função Sucessora

$$S : \mathbb{N} \rightarrow \mathbb{N}$$

$$S(x) = x + 1$$

Retorna o sucessor do argumento.
### 3. Funções de Projeção

$$P_i^k : \mathbb{N}^k \rightarrow \mathbb{N}, \text{ para } 1 \leq i \leq k$$

$$P_i^k(x_1, x_2, \dots, x_k) = x_i$$

Retorna o  $i$ -ésimo argumento.

{7}------------------------------------------------
#### Exemplo: Funções Básicas
#### Função Zero

- $Z(0) = 0$
- $Z(5) = 0$
- $Z(1000) = 0$
#### Função Sucessora

- $S(0) = 1$
- $S(5) = 6$
- $S(S(S(0))) = 3$
### Funções de Projeção

- $P_1^2(3, 7) = 3$
- $P_2^2(3, 7) = 7$
- $P_2^3(5, 8, 2) = 8$

{8}------------------------------------------------
### Conexão com Axiomas de Peano
### Axiomas de Peano (simplificado)

- 1 0 é um número natural
- 2 Se  $n$  é natural, então  $S(n)$  é natural
- 3  $S(n) \neq 0$  para todo  $n$
- 4  $S(n) = S(m) \Rightarrow n = m$
- 5 Princípio da Indução
### Relação

- $Z$  fornece acesso ao elemento base 0
- $S$  fornece um “construtor de números”
- Projeções são necessárias para acessar múltiplos valores
- A recursão primitiva corresponde ao princípio da indução (ver operações)

{9}------------------------------------------------
## Operação 1: Composição
### Definição

Sejam  $g : \mathbb{N}^m \rightarrow \mathbb{N}$  e  $h_1, \dots, h_m : \mathbb{N}^k \rightarrow \mathbb{N}$ .

A **composição** de  $g$  com  $h_1, \dots, h_m$  é a função  $f : \mathbb{N}^k \rightarrow \mathbb{N}$  definida por:

$$f(x_1, \dots, x_k) = g(h_1(x_1, \dots, x_k), \dots, h_m(x_1, \dots, x_k))$$
### Notação

$$f = g \circ (h_1, \dots, h_m) \text{ ou } f = \text{Comp}[g, h_1, \dots, h_m]$$
### Intuição

- Aplique cada  $h_i$  aos argumentos
- Use os resultados como entrada para  $g$
- Corresponde a “chamar funções dentro de funções”

{10}------------------------------------------------
### Exemplos de Composição
#### Exemplo 1: Função Constante 1

$$f(x) = 1$$

Como?  $f = S \circ Z$ , ou seja:

$$f(x) = S(Z(x)) = S(0) = 1$$
#### Exemplo 2: Função Constante $n$

$$f(x) = n$$

Como?  $f = \underbrace{S \circ S \circ \dots \circ S}_{n \text{ vezes}} \circ Z$
#### Exemplo 3: Soma de dois

$$f(x) = x + 2$$

Como?  $f = S \circ S \circ P_1^1 = S \circ S$ , ou seja:

$$f(x) = S(S(x))$$

{11}------------------------------------------------
## Operação 2: Recursão Primitiva
### Definição

Sejam  $g : \mathbb{N}^k \rightarrow \mathbb{N}$  e  $h : \mathbb{N}^{k+2} \rightarrow \mathbb{N}$ .

A função  $f : \mathbb{N}^{k+1} \rightarrow \mathbb{N}$  definida por **recursão primitiva** a partir de  $g$  e  $h$  é:

$$f(x_1, \dots, x_k, 0) = g(x_1, \dots, x_k)$$

$$f(x_1, \dots, x_k, y + 1) = h(x_1, \dots, x_k, y, f(x_1, \dots, x_k, y))$$
### Notação

$f = \text{Rec}[g, h]$  ou  $f = \rho(g, h)$
### Estrutura

- $g$  define o **caso base** (quando o último argumento é 0)
- $h$  define o **passo recursivo** (dado o valor anterior, calcula o próximo)

{12}------------------------------------------------
### Visualização da Recursão Primitiva

Para calcular  $f(x_1, \dots, x_k, n)$ :

$$\begin{array}{c}
 f(\vec{x}, 0) = g(\vec{x}) \\
 \downarrow \\
 f(\vec{x}, 1) = h(\vec{x}, 0, f(\vec{x}, 0)) \\
 \downarrow \\
 f(\vec{x}, 2) = h(\vec{x}, 1, f(\vec{x}, 1)) \\
 \downarrow \\
 \vdots \\
 \downarrow \\
 f(\vec{x}, n) = h(\vec{x}, n-1, f(\vec{x}, n-1))
 \end{array}$$

The image shows the official coat of arms of the University of São Paulo (USP). It features a shield with a central panel containing a stylized 'M' and 'U' monogram, flanked by two panels with a cross pattern. Above the shield is a crown, and below it is a banner with the Latin motto 'AD VERVM DVCT'. The shield is supported by two figures, likely representing the university's history and values.

Coat of arms of the University of São Paulo (USP)

{13}------------------------------------------------
#### Definição: Funções Recursivas Primitivas
### Definição Indutiva

O conjunto das **funções recursivas primitivas** é o menor conjunto de funções que:

**1** Contém as funções básicas:

- Função zero:  $Z$
- Função sucessor:  $S$
- Funções de projeção:  $P_i^k$  para todo  $k \geq 1$  e  $1 \leq i \leq k$

**2** É fechado sob **composição**:

- Se  $g, h_1, \dots, h_m$  são recursivas primitivas, então  $g \circ (h_1, \dots, h_m)$  também é

**3** É fechado sob **recursão primitiva**:

- Se  $g, h$  são recursivas primitivas, então  $\text{Rec}[g, h]$  também é

{14}------------------------------------------------
### Propriedades das Funções Recursivas Primitivas
#### Teorema

Toda função recursiva primitiva é **total**, ou seja, está definida para todas as entradas em  $\mathbb{N}^k$ .
#### “Prova”

- Funções básicas são claramente totais
- Composição de funções totais é total
- Recursão primitiva de funções totais é total (sempre termina em  $n + 1$  passos)
- Por indução, toda função recursiva primitiva é total.
#### Consequência

As funções recursivas primitivas não podem expressar todas as funções computáveis — existem funções computáveis totais que **não** são recursivas primitivas!

{15}------------------------------------------------
#### Exemplo 1: Adição
##### Definição

$$\text{add}(x, y) = x + y$$
##### Construção por Recursão Primitiva

$$\begin{aligned}\text{add}(x, 0) &= x = P_1^1(x) \\ \text{add}(x, y + 1) &= \text{add}(x, y) + 1 = S(P_3^3(x, y, \text{add}(x, y)))\end{aligned}$$

$$\text{Portanto: } \text{add} = \text{Rec}[P_1^1, S \circ P_3^3]$$
##### Verificação: $\text{add}(2, 3)$

$$\begin{aligned}\text{add}(2, 0) &= 2 \\ \text{add}(2, 1) &= S(\text{add}(2, 0)) = S(2) = 3 \\ \text{add}(2, 2) &= S(\text{add}(2, 1)) = S(3) = 4 \\ \text{add}(2, 3) &= S(\text{add}(2, 2)) = S(4) = 5\checkmark\end{aligned}$$

{16}------------------------------------------------
#### Exemplo 2: Multiplicação
##### Definição

$$\text{mult}(x, y) = x \cdot y$$
##### Construção por Recursão Primitiva

$$\text{mult}(x, 0) = 0 = Z(x)$$

$$\text{mult}(x, y + 1) = \text{mult}(x, y) + x = \text{add}(P_3^3(x, y, r), P_1^3(x, y, r))$$

onde  $r = \text{mult}(x, y)$ .

Portanto:  $\text{mult} = \text{Rec}[Z, \text{add} \circ (P_3^3, P_1^3)]$
##### Verificação: $\text{mult}(3, 2)$

$$\text{mult}(3, 0) = 0$$

$$\text{mult}(3, 1) = \text{mult}(3, 0) + 3 = 0 + 3 = 3$$

$$\text{mult}(3, 2) = \text{mult}(3, 1) + 3 = 3 + 3 = 6\checkmark$$

{17}------------------------------------------------
#### Exemplo 3: Exponenciação
##### Definição

$$\text{exp}(x, y) = x^y$$
##### Construção por Recursão Primitiva

$$\text{exp}(x, 0) = 1 = S(Z(x))$$

$$\text{exp}(x, y + 1) = \text{exp}(x, y) \cdot x = \text{mult}(P_3^3, P_1^3)$$

Portanto:  $\text{exp} = \text{Rec}[S \circ Z, \text{mult} \circ (P_3^3, P_1^3)]$
##### Verificação: $\text{exp}(2, 3)$

$$\text{exp}(2, 0) = 1$$

$$\text{exp}(2, 1) = \text{exp}(2, 0) \cdot 2 = 1 \cdot 2 = 2$$

$$\text{exp}(2, 2) = \text{exp}(2, 1) \cdot 2 = 2 \cdot 2 = 4$$

$$\text{exp}(2, 3) = \text{exp}(2, 2) \cdot 2 = 4 \cdot 2 = 8 \checkmark$$

{18}------------------------------------------------
#### Exemplo 4: Predecessor
##### Definição

$$\text{pred}(x) = \begin{cases} 0 & \text{se } x = 0 \\ x - 1 & \text{se } x > 0 \end{cases}$$
##### Construção por Recursão Primitiva

$$\text{pred}(0) = 0$$

$$\text{pred}(y + 1) = y = P_1^2(y, \text{pred}(y))$$

Usando uma função auxiliar constante  $g = Z$  (aridade 0):

$$\text{pred} = \text{Rec}[Z, P_1^2]$$
##### Verificação

$$\text{pred}(0) = 0, \text{pred}(1) = 0, \text{pred}(5) = 4 \quad \checkmark$$

{19}------------------------------------------------
#### Exemplo 5: Subtração Truncada (Monus)
##### Definição

$$x \dot{-} y = \begin{cases} x - y & \text{se } x \geq y \\ 0 & \text{se } x < y \end{cases}$$
##### Construção por Recursão Primitiva

$$\begin{aligned} x \dot{-} 0 &= x = P_1^1(x) \\ x \dot{-} (y + 1) &= \text{pred}(x \dot{-} y) \end{aligned}$$

Portanto:  $\text{monus} = \text{Rec}[P_1^1, \text{pred} \circ P_3^3]$
### Exemplos

- $5 \dot{-} 3 = 2$
- $3 \dot{-} 5 = 0$
- $7 \dot{-} 7 = 0$

{20}------------------------------------------------
#### Exemplo 6: Função Sinal
##### Definição

$$\text{sg}(x) = \begin{cases} 0 & \text{se } x = 0 \\ 1 & \text{se } x > 0 \end{cases}$$
##### Construção

Observe que  $\text{sg}(x) = 1 \dot{-} (1 \dot{-} x)$

Ou por recursão primitiva direta:

$$\text{sg}(0) = 0$$

$$\text{sg}(y + 1) = 1$$
##### Função Sinal Complementar

$$\overline{\text{sg}}(x) = 1 \dot{-} \text{sg}(x) = \begin{cases} 1 & \text{se } x = 0 \\ 0 & \text{se } x > 0 \end{cases}$$

{21}------------------------------------------------
#### Exemplo 7: Comparações
##### Menor ou Igual

$$\text{leq}(x, y) = \begin{cases} 1 & \text{se } x \leq y \\ 0 & \text{caso contrário} \end{cases} = \overline{\text{sg}}(x \dot{-} y)$$
##### Igualdade

$$\text{eq}(x, y) = \begin{cases} 1 & \text{se } x = y \\ 0 & \text{caso contrário} \end{cases} = \text{leq}(x, y) \cdot \text{leq}(y, x)$$

Ou:  $\text{eq}(x, y) = \overline{\text{sg}}((x \dot{-} y) + (y \dot{-} x))$
##### Menor Estrito

$$\text{lt}(x, y) = \text{leq}(x, y) \cdot \overline{\text{sg}}(\text{eq}(x, y))$$

Ou simplesmente:  $\text{lt}(x, y) = \text{sg}(y \dot{-} x)$

{22}------------------------------------------------
#### Exemplo 8: Operações Lógicas

**Verdadeiro** = 1, **Falso** = 0

Negação

$$\text{not}(x) = 1 \dot{-} x$$

Conjunção (E lógico)

$$\text{and}(x, y) = x \cdot y$$

Disjunção (OU lógico)

$$\text{or}(x, y) = \text{sg}(x + y)$$

Condicional (Se-Então-Senão)

$$\text{cond}(c, x, y) = c \cdot x + (1 \dot{-} c) \cdot y$$

Se  $c = 1$ , retorna  $x$ ; se  $c = 0$ , retorna  $y$ .

{23}------------------------------------------------
#### Exemplo 9: Divisão Inteira e Resto
##### Quociente

$\text{quo}(x, y) = \lfloor x/y \rfloor$  (para  $y > 0$ )

$$\text{quo}(0, y) = 0$$

$$\text{quo}(x + 1, y) = \text{quo}(x, y) + \text{eq}(\text{rem}(x + 1, y), 0)$$

Ideia: incrementa o quociente quando o resto volta a zero.
##### Resto da Divisão

$\text{rem}(x, y) =$  resto de  $x$  dividido por  $y$  (para  $y > 0$ )

$$\text{rem}(0, y) = 0$$

$$\text{rem}(x + 1, y) = (1 + \text{rem}(x, y)) \cdot \overline{\text{sg}}(\text{eq}(1 + \text{rem}(x, y), y))$$

Ideia: incrementa o resto, mas zera se atingir  $y$ .

{24}------------------------------------------------
#### Exemplo 10: Fatorial
##### Definição

$$\text{fact}(n) = n!$$
##### Construção por Recursão Primitiva

$$\text{fact}(0) = 1$$

$$\text{fact}(n + 1) = (n + 1) \cdot \text{fact}(n) = \text{mult}(S(P_1^2), P_2^2)$$
##### Verificação

$$\text{fact}(0) = 1$$

$$\text{fact}(1) = 1 \cdot 1 = 1$$

$$\text{fact}(2) = 2 \cdot 1 = 2$$

$$\text{fact}(3) = 3 \cdot 2 = 6$$

$$\text{fact}(4) = 4 \cdot 6 = 24\checkmark$$

{25}------------------------------------------------
### Somatório e Produtório Limitados
### Teorema

Se  $f(x_1, \dots, x_k, y)$  é recursiva primitiva, então também são:

$$\sum_{i=0}^y f(x_1, \dots, x_k, i) \quad \text{e} \quad \prod_{i=0}^y f(x_1, \dots, x_k, i)$$
#### Prova (Somatório)

Defina  $g(\vec{x}, y) = \sum_{i=0}^y f(\vec{x}, i)$  por:

$$\begin{aligned} g(\vec{x}, 0) &= f(\vec{x}, 0) \\ g(\vec{x}, y + 1) &= g(\vec{x}, y) + f(\vec{x}, y + 1) \end{aligned}$$

A prova para o produtório é análogo, usando multiplicação.

NOTA: Apenas somatórios e produtórios **limitados** ( $y$ ) são garantidamente recursivos primitivos.

{26}------------------------------------------------
### Quantificação Limitada (Universal e Existencial)
### Teorema

Se  $P(x_1, \dots, x_k, y)$  é um predicado recursivo primitivo (valores em  $\{0, 1\}$ ), então também são:

$$\forall_{i \leq y} P(\vec{x}, i) \quad \text{e} \quad \exists_{i \leq y} P(\vec{x}, i)$$
### Construção

$$\forall_{i \leq y} P(\vec{x}, i) = \prod_{i=0}^y P(\vec{x}, i)$$
$$\exists_{i \leq y} P(\vec{x}, i) = \text{sg} \left( \sum_{i=0}^y P(\vec{x}, i) \right)$$
## Importante

Quantificação **limitada** preserva recursividade primitiva.

{27}------------------------------------------------
## Resumo: Funções Recursivas Primitivas
### O que Conseguimos Definir

- Aritmética básica:  $+$ ,  $\times$ , potência, predecessor,  $\dot{-}$
- Comparações:  $=$ ,  $<$ ,  $\leq$
- Operações lógicas:  $\neg$ ,  $\wedge$ ,  $\vee$
- Divisão inteira e resto
- Fatorial
- Somatórios e produtórios limitados
- Quantificação limitada (universal e existencial)
## Próxima Aula

Veremos que as funções recursivas primitivas **não** capturam todas as funções computáveis. Precisaremos de uma operação adicional: a **minimização**.

{28}------------------------------------------------
### Exercício 1: Funções Básicas

Calcule:

- 1  $Z(100)$
- 2  $S(S(S(0)))$
- 3  $P_2^4(3, 7, 2, 9)$
- 4  $P_3^3(5, 5, 5)$
- 5  $(S \circ S \circ Z)(42)$

Coat of arms of Brazil, featuring a shield with a star, a banner reading 'AD VERVM DVCIT', and a crown on top.

{29}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-67f9de2f1a2e5acf0d35a9adbcbd2d22_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of Brazil, featuring a shield with a star, a banner reading 'AD VERVM DVCIT', and a crown on top.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Construções por Composição

Expresse as seguintes funções usando apenas  $Z$ ,  $S$ ,  $P_i^k$  e composição:

- 1  $f(x) = 0$  (função zero com aridade 1)
- 2  $g(x) = 3$  (função constante 3)
- 3  $h(x, y) = y$  (projeção no segundo argumento)
- 4  $k(x, y, z) = x + 2$  (ignorando  $y$  e  $z$ )
- 5  $m(x) = x$  (função identidade)

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a large five-pointed star in the center. The shield is flanked by two crossed keys (the keys of St. Peter) and topped by a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{30}------------------------------------------------
### Exercício 3: Recursão Primitiva

Mostre que as seguintes funções são recursivas primitivas, dando explicitamente  $g$  e  $h$  na definição  $f = \text{Rec}[g, h]$ :

- 1  $f(x, y) = x + 2y$
- 2  $f(x, y) = x^2 + y$  (dica: assumo que  $x^2$  é recursiva primitiva)
- 3  $f(n) = 2^n$
- 4  $f(n) = n \cdot (n + 1)$
### Desafio!

- 1 Fibonacci:  $F(0) = 0, F(1) = 1, F(n + 2) = F(n + 1) + F(n)$ 
  - Dica: defina uma função auxiliar que retorna um “par”  
( $F(n), F(n + 1)$ )

{31}------------------------------------------------
### Exercício 4: Predicados

Mostre que os seguintes predicados são recursivos primitivos:

$$1 \quad \text{É\_Zero}(x) = \begin{cases} 1 & \text{se } x = 0 \\ 0 & \text{caso contrário} \end{cases}$$

$$2 \quad \text{É\_Par}(x) = \begin{cases} 1 & \text{se } x \text{ é par} \\ 0 & \text{caso contrário} \end{cases}$$

$$3 \quad \text{Divide}(x, y) = \begin{cases} 1 & \text{se } x \mid y \\ 0 & \text{caso contrário} \end{cases}$$

$$4 \quad \text{É\_Primo}(n) = \begin{cases} 1 & \text{se } n \text{ é primo} \\ 0 & \text{caso contrário} \end{cases}$$

**Dica:**  $n$  é primo sse  $n > 1$  e não existe  $2 \leq d < n$  que divide  $n$

Faint watermark of the University of Coimbra crest on the right side of the slide.

{32}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-d9a8b92ba7fc661ebe736ba3e4088eb5_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra crest on the right side of the slide.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 5: Busca Limitada
#### Definição

Se  $P(\vec{x}, y)$  é um predicado recursivo primitivo, definimos:

$$(\mu y \leq z)P(\vec{x}, y) = \begin{cases} \text{menor } y \leq z \text{ tal que } P(\vec{x}, y) = 1 & \text{se existir} \\ z + 1 & \text{caso contrário} \end{cases}$$

- 1 **Desafio!** Prove que  $(\mu y \leq z)P(\vec{x}, y)$  é recursiva primitiva.

Dica: somas limitadas são recursivas primitivas!

- 2 Use busca limitada para definir:
  - $\sqrt{n}$  (raiz quadrada inteira,  $= \lfloor \sqrt{n} \rfloor$ )
  - O  $n$ -ésimo número primo  $p(n)$

{33}------------------------------------------------
### Exercício 6: Codificação de Pares

**Desafio!** A função de pareamento de Cantor codifica pares de naturais como um único natural:

$$\langle x, y \rangle = \frac{(x + y)(x + y + 1)}{2} + y$$

- 1 Mostre que  $\langle \cdot, \cdot \rangle$  é recursiva primitiva.
- 2 Defina funções recursivas primitivas  $\pi_1$  e  $\pi_2$  tais que:

$$\pi_1(\langle x, y \rangle) = x \quad \text{e} \quad \pi_2(\langle x, y \rangle) = y$$

- 3 Use pareamento para mostrar que a função de Fibonacci é recursiva primitiva sem usar funções auxiliares que “retornam pares”.

{34}------------------------------------------------
### Exercício 7: Função de Ackermann

**Desafio!** A função de Ackermann é definida por:

$$A(m, n) = \begin{cases} n + 1 & \text{se } m = 0 \\ A(m - 1, 1) & \text{se } m > 0 \text{ e } n = 0 \\ A(m - 1, A(m, n - 1)) & \text{se } m > 0 \text{ e } n > 0 \end{cases}$$

- 1 Calcule  $A(0, 5)$ ,  $A(1, 3)$ ,  $A(2, 2)$ ,  $A(3, 1)$ .
- 2 Mostre que  $A$  é total (sempre termina).
- 3 A função de Ackermann é computável (pode ser implementada em qualquer linguagem de programação), mas **não** é recursiva primitiva!
## Importante

Por que a função de Ackermann não é recursiva primitiva? O que isso nos diz sobre a classe das funções recursivas primitivas?

{35}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and the motto 'AD VERVM DVCT'.

<!-- IMAGE_DESCRIPTION: datalab-711ec8db6b4a2d4e24b0c0b2ed8853b8_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-fa6c61be003dfbb4ca5587e48a71de94_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

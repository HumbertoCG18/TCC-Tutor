<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Revisão**
- **Funções Recursivas Primitivas**
  - Pergunta
  - A Função de Ackermann
  - Definição
  - Propriedades
  - Primeiros Valores
  - Limitação Fundamental
  - O Problema
  - A Função de Ackermann é Recursiva Primitiva?
  - Trade-off
- **Funções Parciais**
  - Definição
  - Domínio
  - O Operador de Minimização $\mu$
  - Definição: Funções Recursivas Parciais
  - Definição
  - Funções Recursivas Totais
  - Definição
  - Hierarquia
  - Objetivo
  - Usando Minimização
  - Objetivo
  - Parcialidade
  - Minimização Limitada vs. Ilimitada
  - A Tese de Church-Turing Revisitada
  - Equivalências
- **Terminologia**
- **Funções Computáveis Totais**
  - Definição
  - Problema
- **Codificação de Funções Recursivas Parciais**
  - Codificação
  - Consequência
  - Notação
  - Função Universal
  - Teorema (Kleene)
  - O Teorema s-m-n (Kleene)<sup>1</sup>
  - Teorema do Ponto Fixo
  - Teorema (Kleene, Teorema da Recursão)
- **Funções Não-Computáveis**
  - Argumento de Contagem
  - Teorema
  - Prova por Diagonalização
- **Resumo**
- **Classes de Funções**
  - Exercício 1: Funções Parciais
  - Exercício 2: Minimização
  - Exercício 3: Totalidade
  - Exercício 4: Teoremas de Kleene
  - Exercício 5: Não-Computabilidade
  - Exercício 6: O Castor Ocupado
- **Valores Conhecidos**
- **Referências I**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Funções Computáveis: Funções Recursivas Parciais

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 04

Teoria da Computabilidade e Complexidade  
Ciência da Computação

7 de março de 2026

The logo of PUCRS, featuring a shield with a cross and a star, and the text 'PUCRS' below it.

Logo of PUCRS (Universidade Católica do Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

{1}------------------------------------------------
## Sumário

**1** Limitações das Funções Recursivas Primitivas

**2** Funções Parciais e Minimização

**3** Funções Computáveis

**4** Exercícios

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central vertical band containing a stylized 'M' and 'U' monogram, flanked by two vertical bands with a repeating cross pattern. A large five-pointed star is positioned at the bottom center of the shield. Above the shield is a crown, and on either side are crossed keys. A banner at the bottom of the shield contains the Latin motto 'AD VERVM DVCT'.

Coat of arms of the University of São Paulo (USP)

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-1211e36d120f0d2912a745437f4c8f19_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9887cf85c05205c57271d28ecc108b32_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-a3f81dedbdc5b702f397d07ef476d53e_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->
## Revisão
## Funções Recursivas Primitivas

- Funções básicas:  $Z$ ,  $S$ ,  $P_i^k$
- Operações: composição e recursão primitiva
- Todas são **totais** (definidas para todas as entradas)
### Pergunta

As funções recursivas primitivas capturam todas as funções computáveis?
#### Resposta: Não!

Existem funções computáveis totais que **não** são recursivas primitivas.

Exemplo clássico: **Função de Ackermann**

{3}------------------------------------------------
### A Função de Ackermann
### Definição

$$A(m, n) = \begin{cases} n + 1 & \text{se } m = 0 \\ A(m - 1, 1) & \text{se } m > 0 \text{ e } n = 0 \\ A(m - 1, A(m, n - 1)) & \text{se } m > 0 \text{ e } n > 0 \end{cases}$$
### Propriedades

- $A$  é **total** — sempre termina
- $A$  é **computável** — existe algoritmo
- $A$  **não** é recursiva primitiva!
### Primeiros Valores

| $A(m, n)$ | $n = 0$ | $n = 1$ | $n = 2$ | $n = 3$ | $n = 4$ |
|-----------|---------|---------|---------|---------|---------|
| $m = 0$   | 1       | 2       | 3       | 4       | 5       |
| $m = 1$   | 2       | 3       | 4       | 5       | 6       |

{4}------------------------------------------------
### Limitação Fundamental
### O Problema

A recursão primitiva só permite recursão sobre um único argumento que **decrece de 1 em 1**.

$$\begin{aligned}f(\vec{x}, 0) &= g(\vec{x}) \\f(\vec{x}, y + 1) &= h(\vec{x}, y, f(\vec{x}, y))\end{aligned}$$

Isso garante terminação, mas limita o poder expressivo.
#### Observação

A função de Ackermann usa recursão **aninhada**:

$$A(m, n) = A(m - 1, \underbrace{A(m, n - 1)}_{\text{chamada recursiva como argumento}})$$

chamada recursiva como argumento

{5}------------------------------------------------
### A Função de Ackermann é Recursiva Primitiva?
#### Teorema

Para toda função recursiva primitiva  $f : \mathbb{N}^k \rightarrow \mathbb{N}$ , existe  $m$  tal que:

$$f(x_1, \dots, x_k) < A(m, \max(x_1, \dots, x_k))$$

para todos  $x_1, \dots, x_k$ .
#### Consequência

A função diagonal  $d(n) = A(n, n)$  cresce mais rápido que qualquer função recursiva primitiva.

Se  $A$  fosse recursiva primitiva, teríamos:

$$A(n, n) < A(m, n) \text{ para algum } m \text{ fixo}$$

Mas  $A(n, n) > A(m, n)$  para  $n > m$ . Contradição!

{6}------------------------------------------------
#### O que está faltando?
#### Análise

As funções recursivas primitivas não podem expressar:

- Funções que crescem “muito rápido” (como Ackermann)
- Busca ilimitada: “encontre o menor  $y$  tal que...”
- Loops que podem não terminar (while)
#### Solução

Precisamos de uma nova operação: **minimização** (operador  $\mu$ )  
Esta operação permite buscar o menor valor que satisfaz uma condição, mas pode **não terminar** se tal valor não existir.
### Trade-off

Ao adicionar minimização:

- Ganhamos poder expressivo (todas as funções computáveis)
- Perdemos garantia de totalidade (funções podem ser parciais)

{7}------------------------------------------------
## Funções Parciais
### Definição

Uma **função parcial**  $f : \mathbb{N}^k \rightarrow \mathbb{N}$  é uma função que pode não estar definida para algumas entradas.

- $f(\vec{x}) \downarrow$  significa que  $f$  está **definida** em  $\vec{x}$
- $f(\vec{x}) \uparrow$  significa que  $f$  está **indefinida** em  $\vec{x}$
- $f(\vec{x}) = y$  implica  $f(\vec{x}) \downarrow$
### Domínio

$$\text{dom}(f) = \{\vec{x} \in \mathbb{N}^k : f(\vec{x}) \downarrow\}$$
#### Exemplo

$f(x) = \lfloor \sqrt{x} \rfloor$  se  $x$  é quadrado perfeito, indefinida caso contrário.  
 $\text{dom}(f) = \{0, 1, 4, 9, 16, 25, \dots\}$

{8}------------------------------------------------
### O Operador de Minimização $\mu$
#### Definição Informal

$\mu y[P(y)] =$  “o menor  $y$  tal que  $P(y)$  é verdadeiro”
#### Definição Formal

Seja  $g : \mathbb{N}^{k+1} \rightarrow \mathbb{N}$  uma função (total ou parcial).

A **minimização** de  $g$  é a função  $f : \mathbb{N}^k \rightarrow \mathbb{N}$  definida por:

$$f(x_1, \dots, x_k) = \mu y[g(x_1, \dots, x_k, y) = 0]$$

que significa:  $f(\vec{x}) =$  o menor  $y$  tal que:

- 1  $g(\vec{x}, 0), g(\vec{x}, 1), \dots, g(\vec{x}, y)$  estão todas definidas
- 2  $g(\vec{x}, y) = 0$

Se tal  $y$  não existir,  $f(\vec{x})$  é indefinida.

{9}------------------------------------------------
#### Visualização da Minimização

Para calcular  $f(\vec{x}) = \mu y[g(\vec{x}, y) = 0]$ :

$y = 0$ :  $g(\vec{x}, 0) = 5 \neq 0$ , continua...

$y = 1$ :  $g(\vec{x}, 1) = 3 \neq 0$ , continua...

$y = 2$ :  $g(\vec{x}, 2) = 7 \neq 0$ , continua...

$y = 3$ :  $g(\vec{x}, 3) = 0 = 0$ , retorna  $y = 3!$
#### Cuidado!

Se  $g(\vec{x}, y) \neq 0$  para todo  $y$ , ou se  $g(\vec{x}, y) \uparrow$  para algum  $y$  antes de encontrar zero, então  $f(\vec{x}) \uparrow$  (loop infinito).

{10}------------------------------------------------
#### Notação para Minimização
#### Notações Equivalentes

- $f = \mu[g]$  ou  $f = \mu y[g(\vec{x}, y) = 0]$
- $f(\vec{x}) = \mu y[g(\vec{x}, y) = 0]$
- $f(\vec{x}) = \mu y[P(\vec{x}, y)]$  onde  $P$  é um predicado
#### Convenção

Quando escrevemos  $\mu y[P(\vec{x}, y)]$ , assumimos:

$$P(\vec{x}, y) = 1 \iff g(\vec{x}, y) = 0$$

para alguma função  $g$  apropriada.

{11}------------------------------------------------
### Definição: Funções Recursivas Parciais
### Definição

O conjunto das **funções recursivas parciais** (ou  $\mu$ -recursivas) é o menor conjunto de funções parciais que:

- 1 Contém as funções básicas:  $Z$ ,  $S$ ,  $P_i^k$
- 2 É fechado sob **composição**:
  - $f(\vec{x}) = g(h_1(\vec{x}), \dots, h_m(\vec{x}))$
  - $f(\vec{x}) \downarrow$  sse todos  $h_i(\vec{x}) \downarrow$  e  $g(h_1(\vec{x}), \dots) \downarrow$
- 3 É fechado sob **recursão primitiva**
- 4 É fechado sob **minimização**:
  - Se  $g$  é recursiva parcial, então  $\mu[g]$  também é
#### Definição: Conjunto Fechado

$S$  é **fechado** sob uma operação  $\Psi$  se sempre que aplicamos  $\Psi$  a elementos de  $S$ , o resultado também está em  $S$ .

Isto é: Se  $a, b \in S$ , então  $a \circ b \in S$ .

{12}------------------------------------------------
### Funções Recursivas Totais
### Definição

Uma função recursiva parcial que é **total** (definida para todas as entradas) é chamada simplesmente de **função recursiva** ou **função recursiva total**.
### Hierarquia

Rec. Primitivas  $\subset$  Recursivas Totais  $\subset$  Recursivas Parciais
#### Exemplos

- Adição, multiplicação: recursivas primitivas
- Função de Ackermann: recursiva total, mas não primitiva
- “Menor  $y$  tal que  $y^2 > x$ ”: recursiva total (sempre existe)
- “Menor  $y$  tal que programa  $x$  para na entrada  $y$ ”: recursiva parcial (pode não existir)

{13}------------------------------------------------
#### Exemplo: Raiz Quadrada Inteira
### Objetivo

$\text{sqrt}(x) = \lfloor \sqrt{x} \rfloor = \text{maior inteiro cujo quadrado} \leq x$
### Usando Minimização

$$\text{sqrt}(x) = \mu y[(y + 1)^2 > x]$$

Ou seja: menor  $y$  tal que  $(y + 1)^2 > x$ .

Definindo  $g(x, y) = (y + 1)^2 \dot{-} (x + 1)$  (é 0 quando  $(y + 1)^2 \leq x \dots$  não, precisamos ajustar)

Melhor:  $\text{sqrt}(x) = \mu y[\text{sg}((y + 1)^2 \dot{-} (x + 1)) = 1] \dot{-} 1$
#### Observação

Esta função é **total** porque sempre existe tal  $y$  (basta  $y > x$ ).

{14}------------------------------------------------
#### Exemplo: Divisão
### Objetivo

$\text{div}(x, y) = \lfloor x/y \rfloor$  para  $y > 0$
#### Usando Minimização

$\text{div}(x, y) = \mu q[(q + 1) \cdot y > x]$

Menor  $q$  tal que  $(q + 1) \cdot y > x$ , ou seja,  $q \cdot y \leq x < (q + 1) \cdot y$ .
### Parcialidade

E se  $y = 0$ ?

$(q + 1) \cdot 0 = 0 \not> x$  para  $x > 0$ .

A busca nunca encontra tal  $q$ , então  $\text{div}(x, 0) \uparrow$ .

A divisão por zero é **indefinida**; comportamento correto!

{15}------------------------------------------------
### Minimização Limitada vs. Ilimitada
#### Minimização Limitada

$(\mu y \leq z)[P(\vec{x}, y)] =$  menor  $y \leq z$  tal que  $P(\vec{x}, y)$ , ou  $z + 1$  se não existir.

- É **recursiva primitiva**
- Sempre **termina** (busca até  $z$ , no máximo)
- Preserva totalidade
#### Minimização Ilimitada

$\mu y[P(\vec{x}, y)] =$  menor  $y$  tal que  $P(\vec{x}, y)$ .

- É a operação que define funções recursivas parciais
- Pode **não terminar** se tal  $y$  não existir
- Pode introduzir parcialidade

{16}------------------------------------------------
### A Tese de Church-Turing Revisitada
#### Tese de Church-Turing

Uma função  $f : \mathbb{N}^k \rightarrow \mathbb{N}$  é **efetivamente computável** se e somente se é **recursiva parcial**.
### Equivalências

Os seguintes são equivalentes para uma função  $f$ :

- $f$  é recursiva parcial ( $\mu$ -recursiva)
- $f$  é Turing-computável
- $f$  é computável por cálculo lambda
- $f$  pode ser implementada em qualquer linguagem de programação Turing-completa
## Terminologia

“Recursiva Parcial” = “Turing-computável” = “Computável (nos dias de hoje)”. Estes termos são *intercambiáveis*.

{17}------------------------------------------------
## Funções Computáveis Totais
### Definição

Uma função é **computável total** se é computável e total (definida em todas as entradas).
#### Pergunta Natural

Por que não definir “computável” como “computável total”?
### Problema

- O conjunto das funções computáveis totais **não é efetivamente enumerável!**
- Não existe algoritmo que lista todas as funções computáveis totais.
- Isso torna a classe difícil de trabalhar teoricamente.
- Em contraste, as funções recursivas parciais podem ser efetivamente enumeradas (via codificação de programas).

{18}------------------------------------------------
## Codificação de Funções Recursivas Parciais
### Codificação

Cada função recursiva parcial pode ser descrita por uma “receita” finita:

- Quais funções básicas usa
- Como são combinadas (composição, recursão, minimização)

Esta receita pode ser codificada como um número natural!
### Consequência

Existe uma enumeração  $\varphi_0, \varphi_1, \varphi_2, \dots$  de todas as funções recursivas parciais de uma variável.

$\varphi_e =$  a função com “código” (ou índice)  $e$ .
### Notação

$\varphi_e^{(k)}$  denota a  $e$ -ésima função recursiva parcial de  $k$  variáveis.

{19}------------------------------------------------
### Função Universal
### Teorema (Kleene)

Existe uma função recursiva parcial  $U : \mathbb{N}^2 \rightarrow \mathbb{N}$  tal que:

$$U(e, x) = \varphi_e(x)$$

para todo  $e$  e  $x$ .
#### Interpretação

$U$  é um **interpretador universal**: dado o código  $e$  de um programa e uma entrada  $x$ , simula a execução de  $\varphi_e$  em  $x$ .

$U$  é recursiva parcial; o próprio interpretador pode ser implementado!
#### Analogia

$U$  **equivale** a Máquina de Turing Universal: ambas podem processar qualquer programa, já que programas são dados e podem ser codificados como entrada.

{20}------------------------------------------------
### O Teorema s-m-n (Kleene)<sup>1</sup>
#### Definição

Existe uma função recursiva primitiva  $s : \mathbb{N}^2 \rightarrow \mathbb{N}$  tal que:

$$\varphi_{s(e,y)}(x) = \varphi_e(x, y)$$
#### Interpretação

Dado um programa  $e$  de duas variáveis e um valor  $y$ , podemos computar o código  $s(e, y)$  de um novo programa que “fixa” o segundo argumento em  $y$ .

Isso é **aplicação parcial** ou **currificação** (Cálculo- $\lambda$ )!

Desenvolvido por Schönfinkel e Frege; e Haskell Curry (ind.)
#### Exemplo em Python

```
1 def add(x, y): return x + y
2 add5 = lambda x: add(x, 5) # s(add, 5)
```

{21}------------------------------------------------
### Teorema do Ponto Fixo
### Teorema (Kleene, Teorema da Recursão)

Para toda função recursiva total  $f : \mathbb{N} \rightarrow \mathbb{N}$ , existe  $n$  tal que:

$$\varphi_n = \varphi_{f(n)}$$
#### Interpretação

Qualquer “transformação”  $f$  de programas tem um **ponto fixo**: um programa  $n$  que se comporta igual à sua transformação  $f(n)$ .
#### Consequências Surpreendentes

- Existem programas que imprimem seu próprio código (quines<sup>2</sup>)
- Muitos problemas sobre programas são indecidíveis
- Programas podem “se referir a si mesmos”

<sup>2</sup>[https://en.wikipedia.org/wiki/Quine\\_\(computing\)](https://en.wikipedia.org/wiki/Quine_(computing))

{22}------------------------------------------------
## Funções Não-Computáveis
### Argumento de Contagem

- Funções computáveis são enumeráveis ( $\aleph_0$ )
- Todas as funções  $f : \mathbb{N} \rightarrow \mathbb{N}$  são incontáveis ( $2^{\aleph_0}$ )
- Logo, existem funções não-computáveis (“a maioria”!)
#### Exemplo Concreto: Função de Parada

Defina  $h : \mathbb{N} \rightarrow \{0, 1\}$  por:

$$h(e) = \begin{cases} 1 & \text{se } \varphi_e(e) \downarrow \\ 0 & \text{se } \varphi_e(e) \uparrow \end{cases}$$

$h$  é total mas **não computável!**

{23}------------------------------------------------
#### Prova: Função de Parada Não é Computável
### Teorema

$h(e) = [\varphi_e(e) \downarrow]$  não é computável.
### Prova por Diagonalização

Suponha que  $h$  seja computável. Defina:

$$g(e) = \begin{cases} 0 & \text{se } h(e) = 0 \\ \uparrow & \text{se } h(e) = 1 \end{cases}$$

$g$  é computável (se  $h$  for): loop infinito quando  $h(e) = 1$ .

Seja  $g = \varphi_k$  para algum  $k$ . O que é  $g(k)$ ?

- Se  $\varphi_k(k) \downarrow$ , então  $h(k) = 1$ , então  $g(k) \uparrow$ . Contradição!
- Se  $\varphi_k(k) \uparrow$ , então  $h(k) = 0$ , então  $g(k) = 0 \downarrow$ . Contradição!

Logo,  $h$  não pode ser computável.  $\square$

{24}------------------------------------------------
## Resumo
## Classes de Funções

The diagram illustrates the hierarchy of function classes using four concentric ellipses. The outermost ellipse is labeled "Todas as funções  $\mathbb{N}^k \rightarrow \mathbb{N}$ ". Inside it is an ellipse labeled "Recursivas Parciais (Computáveis)". Inside that is an ellipse labeled "Recursivas Totais". The innermost ellipse is labeled "Rec. Primitivas".

Venn diagram showing the hierarchy of function classes: Todas as funções N^k -> N, Recursivas Parciais (Computáveis), Recursivas Totais, and Rec. Primitivas.

{25}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8d325fc12b494e42c9ea7ed2a7f327a6_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Venn diagram showing the hierarchy of function classes: Todas as funções N^k -> N, Recursivas Parciais (Computáveis), Recursivas Totais, and Rec.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 1: Funções Parciais

Para cada função abaixo, determine seu domínio:

- 1  $f(x) = \mu y[y^2 = x]$  (raiz quadrada exata)
- 2  $g(x, y) = \mu z[x + z = y]$  (“subtração”)
- 3  $h(x) = \mu y[2y = x]$  (metade exata)
- 4  $p(x) = \mu y[y > x \wedge y \text{ é primo}]$  (próximo primo)
- 5  $q(x) = \mu y[x \cdot y = 0]$

Quais destas funções são totais?

The image is a faint, light gray watermark of the coat of arms of the University of São Paulo (USP). It features a central shield with a large five-pointed star at the bottom. The shield is flanked by two crossed flags (one green and gold, the other red and green) and topped by a crown. A banner at the bottom of the shield contains the Latin motto 'AD VERVM DVCT'.

Coat of arms of the University of São Paulo (USP)

{26}------------------------------------------------
### Exercício 2: Minimização

Expresse as seguintes funções usando minimização:

- 1  $\log_2(x) = \lfloor \log_2 x \rfloor$  para  $x \geq 1$
- 2 O  $n$ -ésimo número primo  $p(n)$
- 3 A função inversa de Cantor: dado  $z = \langle x, y \rangle$ , encontre  $x$  e  $y$
- 4  $\gcd(x, y)$  usando o fato de que  $\gcd(x, y) =$  menor  $d > 0$  que divide ambos (que existe)

**Dica:** Para cada item, identifique o predicado  $P$  tal que a resposta é  $\mu y[P(y)]$ .

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a five-pointed star in the center, surrounded by a wreath. Above the shield is a crown. The shield is flanked by two crossed flags. Below the shield is a ribbon with the Latin motto 'AD VERVM DVCT'.

Coat of arms of the University of São Paulo (USP)

{27}------------------------------------------------
### Exercício 3: Totalidade

Determine se as seguintes funções são recursivas primitivas, recursivas totais (mas não primitivas), ou apenas recursivas parciais:

- 1  $f(x) = x!$
- 2  $g(x) = A(x, x)$  onde  $A$  é a função de Ackermann
- 3  $h(x, y) = \lfloor x/y \rfloor$  (para  $y > 0$ , indefinida para  $y = 0$ )
- 4  $p(x) =$  o  $x$ -ésimo número primo
- 5  $q(x) = \mu y[\varphi_x(y) \downarrow]$  (menor entrada para a qual o programa  $x$  para)

Faint watermark of the coat of arms of the University of São Paulo (USP) on the right side of the slide.

{28}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-83db47f9541df5f9be73289497eaae90_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of São Paulo (USP) on the right side of the slide.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 4: Teoremas de Kleene

- 1 Explique intuitivamente por que a função universal  $U(e, x) = \varphi_e(x)$  pode ser computável. O que um algoritmo para  $U$  precisa fazer?
- 2 Dado o teorema s-m-n, mostre que existe uma função recursiva primitiva  $s' : \mathbb{N}^3 \rightarrow \mathbb{N}$  tal que:

$$\varphi_{s'(e,y,z)}(x) = \varphi_e(x, y, z)$$

- 3 Use o teorema do ponto fixo para mostrar que existe um programa  $n$  tal que  $\varphi_n(x) = n$  para todo  $x$ . (Este programa “imprime seu próprio código” independentemente da entrada!)

{29}------------------------------------------------
### Exercício 5: Não-Computabilidade
#### 1 **Requer conceitos ainda não trabalhados na disciplina!**

A função  $\text{tot} : \mathbb{N} \rightarrow \{0, 1\}$ , definida abaixo, é computável?

$$\text{tot}(e) = \begin{cases} 1 & \text{se } \varphi_e \text{ é total} \\ 0 & \text{caso contrário} \end{cases}$$

Use redução ao problema da parada em sua demonstração.
#### 2 **Requer conceitos ainda não trabalhados na disciplina!**

Prove que não existe uma enumeração computável de todas as funções computáveis **totais**.

Imagine se existisse  $f_0, f_1, f_2, \dots$ , todas computáveis.

Considere  $g(x) = f_x(x) + 1$ .

{30}------------------------------------------------
### Exercício 6: O Castor Ocupado

**Requer conceitos ainda não trabalhados na disciplina!**

O **Busy Beaver**  $BB(n)$  é definido como o maior número de 1s que uma Máquina de Turing com  $n$  estados pode escrever em uma fita inicialmente em branco, antes de parar.

- 1 Argumente que  $BB(n)$  é uma função bem definida (existe um máximo finito para cada  $n$ ).
- 2 Prove que  $BB$  não é computável.

**Dica:** Se  $BB$  fosse computável, poderíamos resolver o problema da parada.

- 3 Mostre que  $BB$  cresce mais rápido que qualquer função computável: para toda função computável  $f$ , existe  $N$  tal que  $BB(n) > f(n)$  para todo  $n > N$ .
## Valores Conhecidos

$BB(1) = 1$ ,  $BB(2) = 4$ ,  $BB(3) = 6$ ,  $BB(4) = 13$ ,  
 $BB(5) \geq 47176870$  ...  $BB(6)$  é desconhecido!

{31}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and a banner below reading 'AD VERVM DVCIT'.

<!-- IMAGE_DESCRIPTION: datalab-aa7a4ea43951479b7e7b4c530ea5bc2d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and a banner below reading 'AD VERVM DVCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-d3294dc879b451b369c0b06f42e9b39f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

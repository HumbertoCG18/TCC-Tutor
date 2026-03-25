Exercícios

Prof. Anderson Roberto Pinheiro Domingues

anderson.domingues@pucrs.br

Aula 04 Teoria da Computabilidade e Complexidade Ciência da Computação

7 de março de 2026

![](content/images/aula-04-funções-computáveis-funções-recursivas-parciais-_page_0_Picture_9.png)

## Sumário

00000

- 1 Limitações das Funções Recursivas Primitivas
- 2 Funções Parciais e Minimização
- 3 Funções Computáveis
- 4 Exercícios

![](content/images/aula-04-funções-computáveis-funções-recursivas-parciais-_page_1_Picture_10.png)

## Revisão

## Funções Recursivas Primitivas

- Funcões básicas: Z. S. P<sup>k</sup>
- Operações: composição e recursão primitiva
- Todas são totais (definidas para todas as entradas)

## Pergunta

As funções recursivas primitivas capturam todas as funções computáveis?

## Resposta: Não!

Existem funções computáveis totais que **não** são recursivas primitivas.

Exemplo clássico: Função de Ackermann

# A Função de Ackermann

Limitações das Funções Recursivas Primitivas

## Definição

$$A(m,n) = \begin{cases} n+1 & \text{se } m=0\\ A(m-1,1) & \text{se } m>0 \text{ e } n=0\\ A(m-1,A(m,n-1)) & \text{se } m>0 \text{ e } n>0 \end{cases}$$

## **Propriedades**

- A é **total** sempre termina
- A é computável existe algoritmo
- A não é recursiva primitiva!

#### Primeiros Valores

$$A(m,n)$$
  $n=0$   $n=1$   $n=2$   $n=3$   $n=4$   $m=0$  1 2 3 4 5  $m=1$  2 3 4 5

## Limitação Fundamental

### O Problema

A recursão primitiva só permite recursão sobre um único argumento que decresce de 1 em 1.

$$f(\vec{x}, 0) = g(\vec{x})$$
  
 $f(\vec{x}, y + 1) = h(\vec{x}, y, f(\vec{x}, y))$ 

Isso garante terminação, mas limita o poder expressivo.

#### Observação

A função de Ackermann usa recursão aninhada:

$$A(m,n) = A(m-1, \underbrace{A(m,n-1)}$$

chamada recursiva como argumento

## A Função de Ackermann é Recursiva Primitiva?

#### Teorema

Para toda função recursiva primitiva  $f: \mathbb{N}^k \to \mathbb{N}$ , existe m tal que:

$$f(x_1,\ldots,x_k) < A(m,\max(x_1,\ldots,x_k))$$

para todos  $x_1, \ldots, x_k$ .

### Consequência

A função diagonal d(n) = A(n, n) cresce mais rápido que qualquer função recursiva primitiva.

Se A fosse recursiva primitiva, teríamos:

$$A(n, n) < A(m, n)$$
 para algum  $m$  fixo

Mas A(n, n) > A(m, n) para n > m. Contradição!

#### Análise

As funções recursivas primitivas não podem expressar:

- Funções que crescem "muito rápido" (como Ackermann)
- Busca ilimitada: "encontre o menor y tal que..."
- Loops que podem não terminar (while)

### Solução

Precisamos de uma nova operação: **minimização** (operador  $\mu$ ) Esta operação permite buscar o menor valor que satisfaz uma condição, mas pode **não terminar** se tal valor não existir.

#### Trade-off

Ao adicionar minimização:

- Ganhamos poder expressivo (todas as funções computáveis)
- Perdemos garantia de totalidade (funções podem ser parciais)

000000000

# Funções Parciais

Limitações das Funções Recursivas Primitivas

## Definição

Uma função parcial  $f: \mathbb{N}^k \to \mathbb{N}$  é uma função que pode não estar definida para algumas entradas.

- $f(\vec{x}) \downarrow$  significa que f está **definida** em  $\vec{x}$
- $f(\vec{x}) \uparrow$  significa que f está **indefinida** em  $\vec{x}$
- $f(\vec{x}) = y$  implies  $f(\vec{x}) \downarrow$

#### Domínio

$$dom(f) = \{\vec{x} \in \mathbb{N}^k : f(\vec{x}) \downarrow\}$$

### Exemplo

 $f(x) = |\sqrt{x}|$  se x é quadrado perfeito, indefinida caso contrário.  $dom(f) = \{0, 1, 4, 9, 16, 25, \ldots\}$ 

# O Operador de Minimização $\mu$

### Definição Informal

Limitações das Funções Recursivas Primitivas

 $\mu_V[P(v)] =$  "o menor v tal que P(v) é verdadeiro"

## Definição Formal

Seja  $g: \mathbb{N}^{k+1} \to \mathbb{N}$  uma função (total ou parcial).

A **minimização** de g é a função  $f: \mathbb{N}^k \to \mathbb{N}$  definida por:

$$f(x_1,...,x_k) = \mu y[g(x_1,...,x_k,y) = 0]$$

que significa:  $f(\vec{x}) = o$  menor y tal que:

$$g(\vec{x},0),g(\vec{x},1),\ldots,g(\vec{x},y)$$
 estão todas definidas

$$g(\vec{x}, y) = 0$$

Se tal y não existir,  $f(\vec{x})$  é indefinida.

# Visualização da Minimização

Limitações das Funções Recursivas Primitivas

Para calcular  $f(\vec{x}) = \mu y[g(\vec{x}, y) = 0]$ :

$$y = 0$$
:  $g(\vec{x}, 0) = 5 \neq 0$ , continua...

$$y=1$$
:  $g(\vec{x},1)=3\neq 0$ , continua...

$$y = 2$$
:  $g(\vec{x}, 2) = 7 \neq 0$ , continua...

$$y = 3$$
:  $g(\vec{x}, 3) = 0 = 0$ , retorna  $y = 3$ !

#### Cuidado!

Se  $g(\vec{x}, y) \neq 0$  para todo y, ou se  $g(\vec{x}, y) \uparrow$  para algum y antes de encontrar zero, então  $f(\vec{x}) \uparrow$  (loop infinito).

റററ്ററററററ

# Notação para Minimização

## Notações Equivalentes

Limitações das Funções Recursivas Primitivas

- $f = \mu[g]$  ou  $f = \mu v[g(\vec{x}, v) = 0]$
- $f(\vec{x}) = \mu y [g(\vec{x}, y) = 0]$
- $f(\vec{x}) = \mu y[P(\vec{x}, y)]$  onde P é um predicado

### Convenção

Quando escrevemos  $\mu y[P(\vec{x}, y)]$ , assumimos:

$$P(\vec{x}, y) = 1 \iff g(\vec{x}, y) = 0$$

para alguma função g apropriada.

# Definição: Funções Recursivas Parciais

## Definição

Limitações das Funções Recursivas Primitivas

O conjunto das funções recursivas parciais (ou  $\mu$ -recursivas) é o menor conjunto de funções parciais que:

- 1 Contém as funções básicas: Z, S,  $P_i^k$
- **2** É fechado sob **composição**:
  - $f(\vec{x}) = g(h_1(\vec{x}), \dots, h_m(\vec{x}))$
  - $f(\vec{x}) \downarrow$  sse todos  $h_i(\vec{x}) \downarrow$  e  $g(h_1(\vec{x}),...) \downarrow$
- É fechado sob recursão primitiva
- 4 É fechado sob minimização:
  - Se g é recursiva parcial, então  $\mu[g]$  também é

## Definição: Conjunto Fechado

S é fechado sob uma operação  $\Psi$  se sempre que aplicamos  $\Psi$  a elementos de S. o resultado também está em S. Isto é: Se  $a, b \in S$ , então  $a \circ b \in S$ .

Prof. Anderson R. P. Domingues

## Funcões Recursivas Totais

## Definicão

Uma função recursiva parcial que é total (definida para todas as entradas) é chamada simplesmente de função recursiva ou função recursiva total.

## Hierarquia

Rec. Primitivas $\subset$ Recursivas Totais $\subset$ Recursivas Parciais

## Exemplos

- Adição, multiplicação: recursivas primitivas
- Função de Ackermann: recursiva total, mas não primitiva
- "Menor y tal que  $y^2 > x$ ": recursiva total (sempre existe)
- "Menor v tal que programa x para na entrada v": recursiva parcial (pode não existir)

## Exemplo: Raiz Quadrada Inteira

## Objetivo

 $\operatorname{sqrt}(x) = |\sqrt{x}| = \operatorname{maior} inteiro cujo quadrado < x$ 

### Usando Minimização

Limitações das Funções Recursivas Primitivas

$$\operatorname{sqrt}(x) = \mu y[(y+1)^2 > x]$$

Ou seia: menor y tal que  $(y+1)^2 > x$ .

Definindo  $g(x, y) = (y + 1)^2 - (x + 1)$  (é 0 guando  $(y + 1)^2 < x...$ 

não, precisamos ajustar)

Melhor:  $sqrt(x) = \mu y [sg((y+1)^2 - (x+1)) = 1] - 1$ 

#### Observação

Esta função é **total** porque sempre existe tal v (basta v > x).

## Exemplo: Divisão

## Objetivo

$$\operatorname{div}(x,y) = |x/y|$$
 para  $y > 0$ 

### Usando Minimização

$$\operatorname{div}(x,y) = \mu q[(q+1) \cdot y > x]$$
 Menor  $q$  tal que  $(q+1) \cdot y > x$ , ou seja,  $q \cdot y \le x < (q+1) \cdot y$ .

#### Parcialidade

E se 
$$y = 0$$
?

$$(q+1) \cdot 0 = 0 \not> x$$
 para  $x > 0$ .

A busca nunca encontra tal q, então div(x,0)\u221\u221.

A divisão por zero é indefinida; comportamento correto!

## Minimização Limitada vs. Ilimitada

## Minimização Limitada

Limitações das Funções Recursivas Primitivas

 $(\mu y \leq z)[P(\vec{x}, y)] = \text{menor } y \leq z \text{ tal que } P(\vec{x}, y), \text{ ou } z + 1 \text{ se não}$ existir.

- É recursiva primitiva
- Sempre **termina** (busca até z, no máximo)
- Preserva totalidade

#### Minimização Ilimitada

 $\mu_y[P(\vec{x}, y)] = \text{menor } y \text{ tal que } P(\vec{x}, y).$ 

- É a operação que define funções recursivas parciais
- Pode **não terminar** se tal *y* não existir
- Pode introduzir parcialidade

### Tese de Church-Turing

Uma função  $f: \mathbb{N}^k \to \mathbb{N}$  é efetivamente computável se e somente se é recursiva parcial.

### Equivalências

Os seguintes são equivalentes para uma função f:

- $\blacksquare$  f é recursiva parcial ( $\mu$ -recursiva)
- f é Turing-computável
- f é computável por cálculo lambda
- f pode ser implementada em qualquer linguagem de programação Turing-completa

### **Terminologia**

"Recursiva Parcial" = "Turing-computável" = "Computável (nos dias de hoje)". Estes termos são intercambiáveis.

### Definição

Uma função é **computável total** se é computável e total (definida em todas as entradas).

## Pergunta Natural

Por que não definir "computável" como "computável total"?

#### Problema

- O conjunto das funções computáveis totais não é efetivamente enumerável!
- Não existe algoritmo que lista todas as funções computáveis totais.
- Isso torna a classe difícil de trabalhar teoricamente.
- Em contraste, as funções recursivas parciais podem ser efetivamente enumeradas (via codificação de programas).

## Codificação

Cada função recursiva parcial pode ser descrita por uma "receita" finita:

- Quais funções básicas usa
- Como são combinadas (composição, recursão, minimização)

Esta receita pode ser codificada como um número natural!

## Consequência

Existe uma enumeração  $\varphi_0, \varphi_1, \varphi_2, \ldots$  de todas as funções recursivas parciais de uma variável.

 $\varphi_e=$  a função com "código" (ou índice) e.

## Notação

 $\varphi_{\rm e}^{(k)}$  denota a e-ésima função recursiva parcial de k variáveis.

## Função Universal

## Teorema (Kleene)

Existe uma função recursiva parcial  $U: \mathbb{N}^2 \to \mathbb{N}$  tal que:

$$U(e,x)=\varphi_e(x)$$

para todo  $e \in x$ .

## Interpretação

U é um interpretador universal: dado o código e de um programa e uma entrada x, simula a execução de  $\varphi_{\varepsilon}$  em x. U é recursiva parcial; o próprio interpretador pode ser implementado!

### Analogia

U equivale a Máquina de Turing Universal: ambas podem processar qualquer programa, já que programas são dados e podem ser codificados como entrada.

# O Teorema s-m-n (Kleene)<sup>1</sup>

## Definição

Existe uma função recursiva primitiva  $s: \mathbb{N}^2 \to \mathbb{N}$  tal que:

$$\varphi_{s(e,y)}(x) = \varphi_e(x,y)$$

## Interpretação

Dado um programa e de duas variáveis e um valor y, podemos computar o código s(e, y) de um novo programa que "fixa" o segundo argumento em v.

Isso é aplicação parcial ou currificação (Cálculo- $\lambda$ )! Desenvolvido por Schönfinkel e Frege; e Haskell Curry (ind.)

## Exemplo em Python

```
def add(x, y): return x + y
add5 = lambda x: add(x. 5) # s(add. 5)
```

## Teorema do Ponto Fixo

## Teorema (Kleene, Teorema da Recursão)

Para toda função recursiva total  $f : \mathbb{N} \to \mathbb{N}$ , existe n tal que:

$$\varphi_n = \varphi_{f(n)}$$

### Interpretação

Qualquer "transformação" f de programas tem um **ponto fixo**: um programa n que se comporta igual à sua transformação f(n).

### Consequências Surpreendentes

- Existem programas que imprimem seu próprio código (quines²)
- Muitos problemas sobre programas são indecidíveis
- Programas podem "se referir a si mesmos"

<sup>&</sup>lt;sup>2</sup>https://en.wikipedia.org/wiki/Quine\_(computing)

# Funções Não-Computáveis

## Argumento de Contagem

- Funções computáveis são enumeráveis  $(\aleph_0)$
- Todas as funções  $f: \mathbb{N} \to \mathbb{N}$  são incontáveis  $(2^{\aleph_0})$
- Logo, existem funções não-computáveis ("a maioria"!)

## Exemplo Concreto: Função de Parada

Defina  $h: \mathbb{N} \to \{0,1\}$  por:

$$h(e) = \begin{cases} 1 & \text{se } \varphi_e(e) \downarrow \\ 0 & \text{se } \varphi_e(e) \uparrow \end{cases}$$

h é total mas não computável!

# Prova: Função de Parada Não é Computável

#### Teorema

 $h(e) = [\varphi_e(e) \downarrow]$  não é computável.

## Prova por Diagonalização

Suponha que h seja computável. Defina:

$$g(e) = \begin{cases} 0 & \text{se } h(e) = 0 \\ \uparrow & \text{se } h(e) = 1 \end{cases}$$

g é computável (se h for): loop infinito quando h(e) = 1. Seja  $g = \varphi_k$  para algum k. O que é g(k)?

- Se  $\varphi_k(k)\downarrow$ , então h(k)=1, então  $g(k)\uparrow$ . Contradição!
- Se  $\varphi_k(k)\uparrow$ , então h(k)=0, então  $g(k)=0\downarrow$ . Contradição!

Logo, h não pode ser computável.  $\square$ 

## Resumo

00000

![](content/images/aula-04-funções-computáveis-funções-recursivas-parciais-_page_24_Picture_6.png)

# Exercício 1: Funcões Parciais

Limitações das Funções Recursivas Primitivas

Para cada função abaixo, determine seu domínio:

$$b(x) = \mu y[2y = x]$$
 (metade exata)

4 
$$p(x) = \mu y[y > x \land y \text{ \'e primo}]$$
 (próximo primo)

5 
$$q(x) = \mu y[x \cdot y = 0]$$

Quais destas funções são totais?

![](_page_25_Picture_13.jpeg)

## Exercício 2: Minimização

Expresse as seguintes funções usando minimização:

- $\log_2(x) = |\log_2 x| \text{ para } x \ge 1$
- 2 O n-ésimo número primo p(n)
- **3** A função inversa de Cantor: dado  $z = \langle x, y \rangle$ , encontre  $x \in y$
- 4 gcd(x, y) usando o fato de que gcd(x, y) = menor d > 0 que divide ambos (que existe)

**Dica**: Para cada item, identifique o predicado P tal que a resposta  $\notin \mu_{\mathcal{V}}[P(y)].$ 

Limitações das Funções Recursivas Primitivas

Determine se as seguintes funções são recursivas primitivas, recursivas totais (mas não primitivas), ou apenas recursivas parciais:

- 1 f(x) = x!
- g(x) = A(x,x) onde A é a função de Ackermann
- 3  $h(x,y) = \lfloor x/y \rfloor$  (para y > 0, indefinida para y = 0)
- 4 p(x) = o x-ésimo número primo
- 5  $q(x) = \mu y[\varphi_x(y)\downarrow]$  (menor entrada para a qual o programa x para)

Limitações das Funções Recursivas Primitivas

- 1 Explique intuitivamente por que a função universal  $U(e,x) = \varphi_e(x)$  pode ser computável. O que um algoritmo para *U* precisa fazer?
- 2 Dado o teorema s-m-n, mostre que existe uma função recursiva primitiva  $s': \mathbb{N}^3 \to \mathbb{N}$  tal que:

$$\varphi_{s'(e,y,z)}(x) = \varphi_e(x,y,z)$$

3 Use o teorema do ponto fixo para mostrar que existe um programa n tal que  $\varphi_n(x) = n$  para todo x. (Este programa "imprime seu próprio código" independentemente da entrada!)

Funções Computáveis

## Exercício 5: Não-Computabilidade

Requer conceitos ainda não trabalhados na disciplina! A função tot :  $\mathbb{N} \to \{0,1\}$ , definida abaixo, é computável?

$$tot(e) = \begin{cases} 1 & \text{se } \varphi_e \text{ \'e total} \\ 0 & \text{caso contr\'ario} \end{cases}$$

Use redução ao problema da parada em sua demonstração.

2 Reguer conceitos ainda não trabalhados na disciplina! Prove que não existe uma enumeração computável de todas as funções computáveis totais. Imagine se existisse  $f_0, f_1, f_2, \ldots$ , todas computáveis. Considere  $g(x) = f_x(x) + 1$ .

## Requer conceitos ainda não trabalhados na disciplina!

O **Busy Beaver** BB(n) é definido como o maior número de 1s que uma Máquina de Turing com n estados pode escrever em uma fita inicialmente em branco, antes de parar.

- **1** Argumente que BB(n) é uma função bem definida (existe um máximo finito para cada n).
- ${\bf 2}$  Prove que  ${\it BB}$  não é computável.
  - **Dica**: Se *BB* fosse computável, poderíamos resolver o problema da parada.
- 3 Mostre que BB cresce mais rápido que qualquer função computável: para toda função computável f, existe N tal que BB(n) > f(n) para todo n > N.

#### Valores Conhecidos

$$BB(1) = 1$$
,  $BB(2) = 4$ ,  $BB(3) = 6$ ,  $BB(4) = 13$ ,  $BB(5) \ge 47176870$  ...  $BB(6)$  é desconhecido!

Limitações das Funções Recursivas Primitivas

## Referências I

- [1] Sanjeev Arora e Boaz Barak. Computational Complexity: A Modern Approach. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. Introduction to Automata Theory, Languages, and Computation. 3rd. Pearson, 2006.
- Christos H. Papadimitriou. Computational Complexity. [3] Addison-Wesley, 1994.
- [4] Michael Sipser. Introduction to the Theory of Computation. 3rd. Cengage Learning, 2012.

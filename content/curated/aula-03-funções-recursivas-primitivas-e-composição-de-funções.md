# Funções Recursivas Primitivas; Composição de Funções

Prof. Anderson Roberto Pinheiro Domingues

anderson.domingues@pucrs.br

Aula 03

Teoria da Computabilidade e Complexidade Ciência da Computação

25 de fevereiro de 2026

![](content/images/aula-03-funções-recursivas-primitivas-e-composição-de-funções-_page_0_Picture_7.png)

### Sumário

- 1 Introdução
- 2 Funções Básicas
- 3 Composição e Recursão Primitiva
- 4 Exemplos de Funções Recursivas Primitivas
- 5 Exercícios

![](content/images/aula-03-funções-recursivas-primitivas-e-composição-de-funções-_page_1_Picture_7.png)

### Motivação

### Questão Central

O que significa uma função ser computável?

- Antes dos computadores, matemáticos buscavam formalizar a noção de computação
- David Hilbert e Wilhelm Ackermann (1928): Entscheidungsproblem, existe um procedimento mecânico que decida se uma fórmula lógica é universalmente válida?
  - Universalmente válida: verdadeira em todas as interpretações e modelos; sua negação deve ser uma contradição!
  - Gödel (1931) considera universalmente válida uma fórmula que é provável utilizando lógica de primeira-ordem.
- Várias formalizações independentes surgiram nos anos 1930:
  - Funções recursivas (Gödel, 1931; Kleene, 1936)
  - Cálculo- $\lambda$  (Alonzo Church, 1930/1936)
  - Máquinas de Turing (Turing, 1936)
- As três formalizações acima são equivalentes!

### A Tese de Church-Turing

### Tese de Church-Turing

Uma função é **efetivamente computável** se e somente se é computável por uma Máquina de Turing (ou equivalentemente, é uma função recursiva).

#### Observação

Esta é uma tese, não um teorema e não pode ser provada matematicamente, pois o termo "efetivamente computável" não é um conceito informal.

No entanto, há evidências para afirmar que:

- Todos os modelos de computação propostos são equivalentes
- Nenhuma função intuitivamente computável sai da definição
- Computadores físicos são equiparáveis a máquinas de turing

### Funcões Recursivas: Visão Geral

### Abordagem

Definir uma classe de funções computáveis através de:

- 1 Um conjunto de funções básicas (claramente computáveis)
- 2 Operações que preservam computabilidade

### Hierarquia de Classes

- **Funções Recursivas Primitivas** obtidas por composição e recursão primitiva
- 2 Funções Recursivas Parciais adicionam a operação de minimização; sem garantia de "parada"
- 3 Funções Recursivas (Totais) recursivas parciais que são totais: cada entrada possui um valor de saída correspondente

### Domínio das Funções

### Convenção

Trabalharemos com funções  $f: \mathbb{N}^k \to \mathbb{N}$ . onde:

- $\mathbb{N} = \{0, 1, 2, 3, \ldots\}$
- k > 0, aridade (número de argumentos)
- $\mathbf{k} = 0$ , constantes

### Notação

- $f^{(k)}$  indica que f tem aridade k
- $\vec{x}$  denota  $(x_1, x_2, \dots, x_k)$
- $f(\vec{x})$  é abreviação de  $f(x_1, \dots, x_k)$

### As Três Funções Básicas

### 1. Função Zero

 $Z:\mathbb{N}\to\mathbb{N}$ 

$$Z(x) = 0$$

Retorna zero, independentemente da entrada.

### 2. Função Sucessora

 $S: \mathbb{N} \to \mathbb{N}$ 

$$S(x) = x + 1$$

Retorna o sucessor do argumento.

### 3. Funções de Projeção

 $P_i^k : \mathbb{N}^k \to \mathbb{N}$ , para 1 < i < k

$$P_i^k(x_1, x_2, \ldots, x_k) = x_i$$

Retorna o *i*-ésimo argumento.

### Exemplo: Funções Básicas

### Função Zero

- Z(0) = 0
- Z(5) = 0
- Z(1000) = 0

### Função Sucessora

- S(0) = 1
- S(5) = 6
- S(S(S(0))) = 3

### Funções de Projeção

- $P_1^2(3,7)=3$
- $P_2^2(3,7)=7$
- $P_2^3(5,8,2)=8$

### Axiomas de Peano (simplificado)

- 0 é um número natural
- Se n é natural, então S(n) é natural
- $S(n) \neq 0$  para todo n
- 4  $S(n) = S(m) \Rightarrow n = m$
- 5 Princípio da Indução

### Relação

- Z fornece acesso ao elemento base 0
- *S* fornece um "construtor de números"
- Projeções são necessárias para acessar múltiplos valores
- A recursão primitiva corresponde ao princípio da indução (ver operações)

### Definição

Sejam  $g: \mathbb{N}^m \to \mathbb{N}$  e  $h_1, \ldots, h_m: \mathbb{N}^k \to \mathbb{N}$ .

A **composição** de g com  $h_1, \ldots, h_m$  é a função  $f : \mathbb{N}^k \to \mathbb{N}$ definida por:

$$f(x_1,...,x_k) = g(h_1(x_1,...,x_k),...,h_m(x_1,...,x_k))$$

### Notação

$$f = g \circ (h_1, \dots, h_m)$$
 ou  $f = \mathsf{Comp}[g, h_1, \dots, h_m]$ 

### Intuição

- $\blacksquare$  Aplique cada  $h_i$  aos argumentos
- Use os resultados como entrada para g
- Corresponde a "chamar funções dentro de funções"

### Exemplo 1: Função Constante 1

$$f(x) = 1$$

Como?  $f = S \circ Z$ , ou seja:

$$f(x) = S(Z(x)) = S(0) = 1$$

### Exemplo 2: Função Constante n

$$f(x) = n$$

Como? 
$$f = \underbrace{S \circ S \circ \cdots \circ S} \circ Z$$

#### n vezes

### Exemplo 3: Soma de dois

$$f(x) = x + 2$$

Como?  $f = S \circ S \circ P_1^1 = S \circ S$ , ou seja:

$$f(x) = S(S(x))$$

### Operação 2: Recursão Primitiva

### Definição

Sejam  $g: \mathbb{N}^k \to \mathbb{N}$  e  $h: \mathbb{N}^{k+2} \to \mathbb{N}$ .

A função  $f: \mathbb{N}^{k+1} \to \mathbb{N}$  definida por **recursão primitiva** a partir de g e h é:

$$f(x_1,...,x_k,0) = g(x_1,...,x_k)$$
  
$$f(x_1,...,x_k,y+1) = h(x_1,...,x_k,y,f(x_1,...,x_k,y))$$

#### Notação

$$f = \operatorname{Rec}[g, h]$$
 ou  $f = \rho(g, h)$ 

#### Estrutura

- g define o caso base (quando o último argumento é 0)
- h define o passo recursivo (dado o valor anterior, calcula o próximo)

$$f(\vec{x},0) = g(\vec{x})$$

$$\downarrow$$

$$f(\vec{x},1) = h(\vec{x},0,f(\vec{x},0))$$

$$\downarrow$$

$$f(\vec{x},2) = h(\vec{x},1,f(\vec{x},1))$$

$$\downarrow$$

$$\vdots$$

![](content/images/aula-03-funções-recursivas-primitivas-e-composição-de-funções-_page_12_Picture_6.png)

#### Definição Indutiva

O conjunto das **funções recursivas primitivas** é o menor conjunto de funções que:

- Contém as funções básicas:
  - Função zero: Z
  - Função sucessor: *S*
  - Funções de projeção:  $P_i^k$  para todo k > 1 e 1 < i < k
- **2** É fechado sob **composição**:
  - Se  $g, h_1, \ldots, h_m$  são recursivas primitivas, então  $g \circ (h_1, \ldots, h_m)$  também é
- É fechado sob recursão primitiva:
  - Se g, h são recursivas primitivas, então Rec[g, h] também é

## Propriedades das Funções Recursivas Primitivas

#### Teorema

Toda função recursiva primitiva é **total**, ou seja, está definida para todas as entradas em  $\mathbb{N}^k$ .

#### "Prova"

- Funções básicas são claramente totais
- Composição de funções totais é total
- Recursão primitiva de funções totais é total (sempre termina em n+1 passos)
- Por indução, toda função recursiva primitiva é total.

#### Consequência

As funções recursivas primitivas não podem expressar todas as funções computáveis — existem funções computáveis totais que **não** são recursivas primitivas!

### Exemplo 1: Adição

### Definição

$$\mathsf{add}(x,y) = x + y$$

### Construção por Recursão Primitiva

$$add(x,0) = x = P_1^1(x)$$
  
 $add(x,y+1) = add(x,y) + 1 = S(P_3^3(x,y,add(x,y)))$ 

Portanto: add =  $Rec[P_1^1, S \circ P_3^3]$ 

### Verificação: add(2,3)

add
$$(2,0) = 2$$
  
add $(2,1) = S(add(2,0)) = S(2) = 3$   
add $(2,2) = S(add(2,1)) = S(3) = 4$   
add $(2,3) = S(add(2,2)) = S(4) = 5\checkmark$ 

### Definição

 $mult(x, y) = x \cdot y$ 

### Construção por Recursão Primitiva

$$\operatorname{mult}(x,0) = 0 = Z(x)$$

$$mult(x, y + 1) = mult(x, y) + x = add(P_3^3(x, y, r), P_1^3(x, y, r))$$

onde r = mult(x, y).

Portanto: mult =  $Rec[Z, add \circ (P_3^3, P_1^3)]$ 

### Verificação: mult(3, 2)

$$mult(3,0) = 0$$

$$mult(3,1) = mult(3,0) + 3 = 0 + 3 = 3$$

$$mult(3,2) = mult(3,1) + 3 = 3 + 3 = 6\sqrt{2}$$

### Definição

$$\exp(x, y) = x^y$$

### Construção por Recursão Primitiva

$$\exp(x,0) = 1 = S(Z(x))$$
  
 $\exp(x,y+1) = \exp(x,y) \cdot x = \text{mult}(P_3^3, P_1^3)$ 

Portanto:  $\exp = \text{Rec}[S \circ Z, \text{mult} \circ (P_3^3, P_1^3)]$ 

### Verificação: exp(2,3)

$$\exp(2,0) = 1$$
  
 $\exp(2,1) = \exp(2,0) \cdot 2 = 1 \cdot 2 = 2$   
 $\exp(2,2) = \exp(2,1) \cdot 2 = 2 \cdot 2 = 4$   
 $\exp(2,3) = \exp(2,2) \cdot 2 = 4 \cdot 2 = 8$ 

### Exemplo 4: Predecessor

### Definição

$$\operatorname{pred}(x) = \begin{cases} 0 & \text{se } x = 0 \\ x - 1 & \text{se } x > 0 \end{cases}$$

### Construção por Recursão Primitiva

$$pred(0) = 0$$
 $pred(y+1) = y = P_1^2(y, pred(y))$ 

Usando uma função auxiliar constante g = Z (aridade 0):

$$pred = Rec[Z, P_1^2]$$

### Verificação

$$pred(0) = 0$$
,  $pred(1) = 0$ ,  $pred(5) = 4 \checkmark$ 

### Exemplo 5: Subtração Truncada (Monus)

#### Definicão

$$x - y = \begin{cases} x - y & \text{se } x \ge y \\ 0 & \text{se } x < y \end{cases}$$

### Construção por Recursão Primitiva

$$x - 0 = x = P_1^1(x)$$
  
 $x - (y + 1) = pred(x - y)$ 

Portanto: monus =  $Rec[P_1^1, pred \circ P_3^3]$ 

### **Exemplos**

- $5 \div 3 = 2$
- $= 3 \div 5 = 0$
- $7 \div 7 = 0$

### Exemplo 6: Função Sinal

### Definicão

$$sg(x) = \begin{cases} 0 & \text{se } x = 0 \\ 1 & \text{se } x > 0 \end{cases}$$

#### Construção

Observe que sg(x) = 1 - (1 - x)

Ou por recursão primitiva direta:

$$sg(0) = 0$$
$$sg(y+1) = 1$$

### Função Sinal Complementar

$$\overline{\operatorname{sg}}(x) = 1 - \operatorname{sg}(x) = \begin{cases} 1 & \text{se } x = 0 \\ 0 & \text{se } x > 0 \end{cases}$$

#### Menor ou Igual

$$leq(x,y) = \begin{cases} 1 & \text{se } x \le y \\ 0 & \text{caso contrário} \end{cases} = \overline{sg}(x - y)$$

#### Igualdade

$$eq(x,y) = \begin{cases} 1 & \text{se } x = y \\ 0 & \text{caso contrário} \end{cases} = leq(x,y) \cdot leq(y,x)$$

Ou: 
$$eq(x, y) = \overline{sg}((x - y) + (y - x))$$

#### Menor Estrito

$$\mathsf{lt}(x,y) = \mathsf{leq}(x,y) \cdot \overline{\mathsf{sg}}(\mathsf{eq}(x,y))$$

Ou simplesmente: lt(x, y) = sg(y - x)

### Exemplo 8: Operações Lógicas

**Verdadeiro** = 1. **Falso** = 0

### Negação

$$not(x) = 1 - x$$

### Conjunção (E lógico)

$$\operatorname{and}(x,y) = x \cdot y$$

### Disjunção (OU lógico)

$$\operatorname{or}(x,y) = \operatorname{sg}(x+y)$$

### Condicional (Se-Então-Senão)

$$cond(c, x, y) = c \cdot x + (1 - c) \cdot y$$
  
Se  $c = 1$ , retorna  $x$ ; se  $c = 0$ , retorna  $y$ .

### Exemplo 9: Divisão Inteira e Resto

#### Quociente

$${\sf quo}(x,y)=\lfloor x/y \rfloor$$
 (para  $y>0$ ) 
$${\sf quo}(0,y)=0$$
 
$${\sf quo}(x+1,y)={\sf quo}(x,y)+{\sf eq}({\sf rem}(x+1,y),0)$$

Ideia: incrementa o quociente quando o resto volta a zero.

#### Resto da Divisão

$$rem(x, y) = resto de x dividido por y (para  $y > 0$ )$$

$$\operatorname{rem}(0, y) = 0$$

$$\operatorname{rem}(x + 1, y) = (1 + \operatorname{rem}(x, y)) \cdot \overline{\operatorname{sg}}(\operatorname{eq}(1 + \operatorname{rem}(x, y), y))$$

Ideia: incrementa o resto, mas zera se atingir v.

### Exemplo 10: Fatorial

### Definição

$$fact(n) = n!$$

### Construção por Recursão Primitiva

$$\mathsf{fact}(0) = 1$$
 
$$\mathsf{fact}(n+1) = (n+1) \cdot \mathsf{fact}(n) = \mathsf{mult}(S(P_1^2), P_2^2)$$

### Verificação

fact(0) = 1  
fact(1) = 
$$1 \cdot 1 = 1$$
  
fact(2) =  $2 \cdot 1 = 2$   
fact(3) =  $3 \cdot 2 = 6$   
fact(4) =  $4 \cdot 6 = 24\sqrt{2}$ 

### Somatório e Produtório Limitados

#### Teorema

Se  $f(x_1, ..., x_k, y)$  é recursiva primitiva, então também são:

$$\sum_{i=0}^{y} f(x_1,...,x_k,i) \quad e \quad \prod_{i=0}^{y} f(x_1,...,x_k,i)$$

### Prova (Somatório)

Defina  $g(\vec{x}, y) = \sum_{i=0}^{y} f(\vec{x}, i)$  por:

$$g(\vec{x}, 0) = f(\vec{x}, 0)$$
  
$$g(\vec{x}, y + 1) = g(\vec{x}, y) + f(\vec{x}, y + 1)$$

A prova para o produtório é análogo, usando multiplicação. NOTA: Apenas somatórios e produtórios limitados (v) são garantidamente recursivos primitivos.

### Quantificação Limitada (Universal e Existencial)

#### Teorema

Se  $P(x_1, ..., x_k, y)$  é um predicado recursivo primitivo (valores em  $\{0,1\}$ ), então também são:

$$\forall_{i \leq y} P(\vec{x}, i)$$
 e  $\exists_{i \leq y} P(\vec{x}, i)$ 

### Construção

$$\forall_{i \leq y} P(\vec{x}, i) = \prod_{i=0}^{y} P(\vec{x}, i)$$
$$\exists_{i \leq y} P(\vec{x}, i) = \operatorname{sg}\left(\sum_{i=0}^{y} P(\vec{x}, i)\right)$$

#### **Importante**

Quantificação limitada preserva recursividade primitiva.

### Resumo: Funções Recursivas Primitivas

### O que Conseguimos Definir

- Aritmética básica: +, $\times$, potência, predecessor, -
- $\blacktriangle$  Comparações: =, <,  $\leq$
- Operações lógicas: $\neg$, $\land$, $\lor$
- Divisão inteira e resto
- Fatorial
- Somatórios e produtórios limitados
- Quantificação limitada (universal e existencial)

#### Próxima Aula

Veremos que as funções recursivas primitivas **não** capturam todas as funções computáveis. Precisaremos de uma operação adicional: a **minimização**.

### Exercício 1: Funções Básicas

#### Calcule:

Introdução 000

- 1 Z(100)
- S(S(S(0)))
- $P_2^4(3,7,2,9)$
- $P_3^3(5,5,5)$
- **5**  $(S \circ S \circ Z)(42)$

![](content/images/aula-03-funções-recursivas-primitivas-e-composição-de-funções-_page_28_Picture_11.png)

### Exercício 2: Construções por Composição

Expresse as seguintes funções usando apenas Z, S,  $P_i^k$  e composição:

- 1 f(x) = 0 (função zero com aridade 1)
- g(x) = 3 (função constante 3)
- h(x, y) = y (projeção no segundo argumento)
- 4 k(x, y, z) = x + 2 (ignorando y e z)
- 5 m(x) = x (função identidade)

Mostre que as seguintes funções são recursivas primitivas, dando explicitamente g e h na definição f = Rec[g, h]:

1 
$$f(x, y) = x + 2y$$

2 
$$f(x,y) = x^2 + y$$
 (dica: assuma que  $x^2$  é recursiva primitiva)

3 
$$f(n) = 2^n$$

4 
$$f(n) = n \cdot (n+1)$$

#### Desafio!

**1** Fibonacci: 
$$F(0) = 0$$
,  $F(1) = 1$ ,  $F(n+2) = F(n+1) + F(n)$ 

■ Dica: defina uma função auxiliar que retorna um "par" (F(n), F(n+1))

### Mostre que os seguintes predicados são recursivos primitivos:

Divide
$$(x, y) = \begin{cases} 1 & \text{se } x \mid y \\ 0 & \text{caso contrário} \end{cases}$$

**Dica**:  $n \in \text{primo sse } n > 1 \text{ e não existe } 2 \leq d < n \text{ que divide } n$ 

### Definição

Se  $P(\vec{x}, y)$  é um predicado recursivo primitivo, definimos:

$$(\mu y \le z)P(\vec{x},y) = \begin{cases} \text{menor } y \le z \text{ tal que } P(\vec{x},y) = 1 & \text{se existir} \ z+1 & \text{caso contrário} \end{cases}$$

- **1** Desafio! Prove que  $(\mu y \le z)P(\vec{x}, y)$  é recursiva primitiva. Dica: somas limitadas são recursivas primitivas!
- 2 Use busca limitada para definir:
  - $\blacksquare \sqrt{n}$  (raiz quadrada inteira,  $= |\sqrt{n}|$ )
  - O *n*-ésimo número primo p(n)

### Exercício 6: Codificação de Pares

Desafio! A função de pareamento de Cantor codifica pares de naturais como um único natural:

$$\langle x,y\rangle = \frac{(x+y)(x+y+1)}{2} + y$$

- **1** Mostre que  $\langle \cdot, \cdot \rangle$  é recursiva primitiva.
- **2** Defina funções recursivas primitivas  $\pi_1$  e  $\pi_2$  tais que:

$$\pi_1(\langle x, y \rangle) = x$$
 e  $\pi_2(\langle x, y \rangle) = y$ 

3 Use pareamento para mostrar que a função de Fibonacci é recursiva primitiva sem usar funções auxiliares que "retornam pares".

### Exercício 7: Função de Ackermann

**Desafio!** A função de Ackermann é definida por

$$A(m,n) = \begin{cases} n+1 & \text{se } m = 0\\ A(m-1,1) & \text{se } m > 0 \text{ e } n = 0\\ A(m-1,A(m,n-1)) & \text{se } m > 0 \text{ e } n > 0 \end{cases}$$

- **1** Calcule A(0,5), A(1,3), A(2,2), A(3,1).
- Mostre que A é total (sempre termina).
- 3 A função de Ackermann é computável (pode ser implementada em qualquer linguagem de programação), mas não é recursiva primitiva!

#### **Importante**

Por que a função de Ackermann não é recursiva primitiva? O que isso nos diz sobre a classe das funções recursivas primitivas?

### Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. Introduction to Automata Theory, Languages, and Computation. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

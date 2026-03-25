Prof. Anderson Roberto Pinheiro Domingues

anderson.domingues@pucrs.br

Aula 05 Teoria da Computabilidade e Complexidade Ciência da Computação

17 de marco de 2026

![](content/images/aula-05-minimização-de-funções-recursivas-parciais-_page_0_Picture_9.png)

### Sumário

1 O Operador de Minimização

000000

- 2 Propriedades da Minimização
- 3 Aplicações da Minimização
- 4 Exercícios

![](content/images/aula-05-minimização-de-funções-recursivas-parciais-_page_1_Picture_9.png)

# Recapitulação: Por que Minimização?

#### O Problema

Funções recursivas primitivas são insuficientes:

- Todas são totais (sempre terminam)
- Não conseguem expressar busca ilimitada
- Função de Ackermann é computável mas não recursiva primitiva

#### A Solução

O operador de **minimização** (operador  $\mu$ ) adiciona a capacidade de:

- Buscar o menor valor satisfazendo uma condição
- Expressar loops "while" que podem não terminar
- Capturar todas as funções computáveis

# Definição Formal do Operador $\mu$

#### Definição

Seja  $g: \mathbb{N}^{k+1} \longrightarrow \mathbb{N}$  uma função parcial.

A minimização de g é a função  $f: \mathbb{N}^k \rightharpoonup \mathbb{N}$ :

$$f(\vec{x}) = \mu y[g(\vec{x}, y) = 0]$$

definida como o **menor**  $y \in \mathbb{N}$  tal que:

**1** 
$$g(\vec{x},0)\downarrow$$
,  $g(\vec{x},1)\downarrow$ , ...,  $g(\vec{x},y)\downarrow$  (todos definidos)

**2** 
$$g(\vec{x},0) \neq 0$$
,  $g(\vec{x},1) \neq 0$ , ...,  $g(\vec{x},y-1) \neq 0$ 

$$g(\vec{x},y)=0$$

Se tal y não existe, então  $f(\vec{x})\uparrow$  (indefinido).

# Semântica Operacional

# Algoritmo para $\mu y[g(\vec{x},y)=0]$

```
y = 0
while True:
    # se g(x, y) não estiver definido, o programa falha (indefinido)
    # se g(x, y) não convergir, o programa entra em loop infinito (ind
    if g(x, y) == 0:
        return y
    y = y + 1
```

#### Observações

4

5

- É um loop while, não um loop for
- Pode não terminar se  $g(\vec{x}, y) \neq 0$  para todo y
- Pode não terminar se  $g(\vec{x}, y) \uparrow$  para algum y

O Operador de Minimização

#### Convenção

Usamos  $\mu y[g(\vec{x}, y) = 0]$  (busca por zero) em vez de  $\mu y[P(\vec{x}, y)]$  (busca por verdadeiro) por convenção.

### Equivalência

Para um predicado  $P(\vec{x}, y)$  (valores 0 ou 1):

$$\mu y[P(\vec{x}, y) = 1] = \mu y[1 - P(\vec{x}, y) = 0]$$

Ou seja, podemos buscar por "verdadeiro" complementando o predicado.

#### Exemplo

"Menor y tal que  $y^2 > x$ " pode ser escrito como:

$$\mu y[\operatorname{sg}(y^2 - x) = 0]$$

# Minimização Regular

### Definição

O Operador de Minimização

A minimização  $\mu y[g(\vec{x},y)=0]$  é **regular** se, para toda entrada  $\vec{x}$ :

$$\exists y: g(\vec{x},y)=0$$

Ou seja, sempre existe um y que satisfaz a condição.

### Propriedade

Se g é recursiva primitiva e a minimização é regular, então  $\mu[g]$  é uma função **total**.

### Exemplo: Raiz Quadrada Inteira

$$\operatorname{sqrt}(x) = \mu y[(y+1)^2 > x]$$
  
Regular porque para  $y = x+1$ , temos  $(x+2)^2 > x$ .

### Minimização Limitada (Recursiva Primitiva)

$$(\mu y \leq z)[g(\vec{x},y)=0] = \begin{cases} \text{menor } y \leq z : g(\vec{x},y)=0 & \text{se existir} \ z+1 & \text{caso contrário} \end{cases}$$

- Sempre termina (busca até z)
- Preserva recursividade primitiva
- Função total se g é total

## Minimização Ilimitada (Operador $\mu$ )

$$\mu y[g(\vec{x},y)=0]$$

- Pode não terminar
- Necessária para funções recursivas parciais
- Pode introduzir parcialidade

# Implementação da Minimização Limitada

#### Teorema

Se g é recursiva primitiva, então  $(\mu y \le z)[g(\vec{x},y)=0]$  também é.

### Construção

Defina  $f(\vec{x}, z) = (\mu y \le z)[g(\vec{x}, y) = 0]$  por:

$$f(\vec{x}, z) = \sum_{i=0}^{z} \prod_{j=0}^{i} sg(g(\vec{x}, j))$$

**Ideia**: O produto é 1 enquanto todos  $g(\vec{x},j) \neq 0$  (para  $j \leq i$ ), e vira 0 a partir do primeiro zero. A soma conta quantos "prefixos" não têm zero, dando o índice do primeiro zero.

#### Alternativa

Podemos também definir por recursão primitiva diretamente.

## Fechamento sob Minimização

#### Teorema

Se  $g: \mathbb{N}^{k+1} \to \mathbb{N}$  é recursiva parcial, então  $f = \mu[g]$  também é recursiva parcial.

### Prova (Esboço)

Por definição, o conjunto das funções recursivas parciais é o menor conjunto que:

- 1 Contém as funções básicas
- 2 É fechado sob composição
- 3 É fechado sob recursão primitiva
- 4 É fechado sob minimização

O item 4 garante diretamente o resultado.

# Composição de Minimizações

#### Teorema

Toda função recursiva parcial pode ser expressa usando no máximo **uma** minimização aplicada a uma função recursiva primitiva.

#### Forma Normal de Kleene

Para toda função recursiva parcial  $f: \mathbb{N}^k \rightharpoonup \mathbb{N}$ , existem funções recursivas primitivas g e h tais que:

$$f(\vec{x}) = g(\mu y[h(\vec{x}, y) = 0])$$

#### Consequência

Minimizações aninhadas podem sempre ser "achatadas" em uma única minimização. A complexidade está na função recursiva primitiva, não na estrutura de minimizações.

### O Predicado T de Kleene

### Teorema (Kleene)

Existe um predicado recursivo primitivo T(e, x, y) e uma função recursiva primitiva U(y) tais que:

$$\varphi_e(x) = U(\mu y [T(e, x, y) = 0])$$

onde  $\varphi_e$  é a e-ésima função recursiva parcial.

#### Interpretação

- T(e, x, y): "y codifica uma computação válida do programa e na entrada x"
- U(y): extrai o resultado da computação codificada em y
- A busca por v encontra a menor computação que termina

# Consequências da Forma Normal

#### Corolário 1: Enumeração Efetiva

Existe uma enumeração computável  $\varphi_0, \varphi_1, \varphi_2, \ldots$  de todas as funções recursivas parciais.

Dado e, podemos simular  $\varphi_e$  usando T e U.

#### Corolário 2: Função Universal

A função  $U(e,x) = \varphi_e(x)$  é recursiva parcial.

$$U(e,x) = U'(\mu y[T(e,x,y) = 0])$$

onde U' é a função de extração (recursiva primitiva).

### Corolário 3: Complexidade da Parcialidade

Toda a "parcialidade" de uma função recursiva parcial está concentrada em uma única minimização ilimitada.

# Minimização e Totalidade

### Quando $\mu[g]$ é Total?

A função  $f(\vec{x}) = \mu y[g(\vec{x}, y) = 0]$  é total se e somente se:

$$\forall \vec{x} \exists y : g(\vec{x}, y) = 0 \text{ e } g(\vec{x}, 0), \dots, g(\vec{x}, y - 1) \text{ definidos}$$

### Condição Suficiente

Se g é recursiva primitiva (portanto total) e:

$$\forall \vec{x}\exists y: g(\vec{x},y)=0$$

então  $\mu[g]$  é total (e recursiva total, mas possivelmente não primitiva).

#### Observação

Verificar se  $\mu[g]$  é total é, em geral, **indecidível**!

# Hierarquia de Funções

![](content/images/aula-05-minimização-de-funções-recursivas-parciais-_page_14_Figure_5.png)

- Rec. Primitivas $\subset$ Rec. Totais $\subset$ Rec. Parciais
- Todas as inclusões são estritas

# Aplicação 1: Inversa de Funções

#### Problema

O Operador de Minimização

Dada uma função  $g: \mathbb{N} \to \mathbb{N}$  injetora, encontrar  $g^{-1}$ .

### Solução

$$g^{-1}(y) = \mu x[g(x) = y] = \mu x[|g(x) - y| = 0]$$

Usando subtração truncada:

$$g^{-1}(y) = \mu x [(g(x) - y) + (y - g(x)) = 0]$$

#### Parcialidade

 $g^{-1}(y)\uparrow$  se  $y\notin \text{imagem}(g)$ . Se g é bijetora, então  $g^{-1}$  é total.

# Aplicação 2: Logaritmo Discreto

#### Definição

 $\log_b(x) = \text{menor } y \text{ tal que } b^y \ge x \text{ (para } b > 1)$ 

### Usando Minimização

$$\log_b(x) = \mu y [b^{y+1} > x]$$

Ou equivalentemente:

$$\log_b(x) = \mu y [\operatorname{sg}(b^{y+1} - x) = 1]$$

### Verificação

$$\log_2(8) = \mu y[2^{y+1} > 8]$$

$$y = 0: 2^1 = 2 > 8$$

$$y = 1: 2^2 = 4 > 8$$

$$y = 2: 2^3 = 8 \ge 8$$

$$y = 3: 2^4 = 16 > 8 \checkmark$$

Exercícios

# Aplicação 3: Números Primos

#### O *n*-ésimo Primo

Seja p(n) o n-ésimo número primo (p(0) = 2, p(1) = 3, ...).

### Construção Recursiva

$$p(0) = 2$$

$$p(n+1) = \mu y[y > p(n) \land \mathsf{IsPrime}(y)]$$

onde IsPrime(y) = 1 sse y é primo.

#### Por que é Total?

Pelo postulado de Bertrand, sempre existe um primo entre n e 2n para n > 1. Logo, a busca sempre termina.

# Aplicação 4: Função de Pareamento Inversa

#### Recordando: Função de Pareamento de Cantor

$$\langle x,y\rangle = \frac{(x+y)(x+y+1)}{2} + y$$

#### Funções Inversas

O Operador de Minimização

$$\pi_1(z) = \mu x [\exists y \le z : \langle x, y \rangle = z]$$
  
$$\pi_2(z) = \mu y [\langle \pi_1(z), y \rangle = z]$$

Ou usando a quantificação limitada (recursiva primitiva):

$$\pi_1(z) = (\mu x \le z)[(\mu y \le z)[\langle x, y \rangle = z] \le z]$$

#### Observação

Como a função de pareamento é bijetora, as inversas são totais e. de fato, recursivas primitivas.

# Aplicação 5: Simulação de Máquinas de Turing

#### Ideia

#### Podemos codificar:

- Uma Máquina de Turing *M* como um número *e*
- Uma entrada w como um número x
- Uma computação (sequência de configurações) como um número y

#### Predicado de Computação Válida

Existe predicado recursivo primitivo Valid(e, x, y) tal que:

 $\mathsf{Valid}(e,x,y) = 1 \iff y \; \mathsf{codifica} \; \mathsf{uma} \; \mathsf{computa}$ ção válida de  $M_e \; \mathsf{em} \; x$ 

### Resultado da Computação

$$\mathsf{Result}(e,x) = \textit{U}(\mu y[\mathsf{Valid}(e,x,y)])$$

onde U extrai o resultado da computação codificada em y.

### Definicão

O **problema da parada** pergunta: dado um programa *e* e entrada  $x, \varphi_e(x)$  termina?

### Como Função

$$\mathsf{HALT}(e,x) = \begin{cases} 1 & \mathsf{se} \ \varphi_e(x) \downarrow \\ 0 & \mathsf{se} \ \varphi_e(x) \uparrow \end{cases}$$

### Teorema (Turing, 1936)

HALT não é computável (não é recursiva parcial, nem total).

#### Prova

Por diagonalização.

Exercícios

# Conseguências do Problema da Parada

#### Indecidibilidade

Muitos problemas são **indecidíveis** (não têm algoritmo):

- Determinar se um programa para em alguma entrada
- Determinar se dois programas computam a mesma função
- Determinar se um programa computa uma função total
- Verificar propriedades não-triviais de programas (Teorema de Rice)

#### Teorema de Rice

Seja P uma propriedade não-trivial de funções recursivas parciais (i.e., algumas funções têm P e outras não).

Então o conjunto  $\{e : \varphi_e \text{ tem propriedade } P\}$  não é decidível.

# Resumo: O Poder da Minimização

### O que a Minimização Adiciona

- Busca ilimitada (loops while)
- Capacidade de expressar todas as funções computáveis
- Possibilidade de funções parciais (não-terminação)

### O Preço a Pagar

- Perda de garantia de terminação
- Indecidibilidade de propriedades de programas
- Necessidade de raciocinar sobre parcialidade

### Equivalência com Máquinas de Turing

As funções recursivas parciais são exatamente as funções computáveis por Máquinas de Turing. Esta equivalência (Tese de Church-Turing) é fundamental para a teoria da computabilidade.

O Operador de Minimização

Escreva as seguintes funções usando minimização e verifique se são totais:

- 1  $f(x) = |\sqrt{x}|$  (raiz quadrada inteira)
- **2**  $g(x) = |\log_3 x|$  para  $x \ge 1$
- 3 h(x, y) = |x/y| para y > 0
- 4 prev\_prime(x) = maior primo  $\langle x \rangle$  (para x > 2)
- 5 sqrt\_exact(x) =  $\sqrt{x}$  se x é quadrado perfeito, indefinida caso contrário

Para cada função abaixo, determine se a minimização é regular (sempre encontra um zero) e, portanto, se a função resultante é total:

**1** 
$$f(x) = \mu y[y^2 \ge x]$$

**2** 
$$g(x) = \mu y[2y = x]$$

3 
$$h(x) = \mu y[y! > x]$$

$$p(x,y) = \mu z[x \cdot z = y]$$

$$q(x) = \mu y[IsPrime(x+y)]$$

**Dica**: Para mostrar que é total, encontre um limitante para o valor de y.

Evercícios

## Exercício 3: Forma Normal de Kleene

**Desafio!** Explique por que toda função recursiva parcial pode ser escrita na forma:

$$f(\vec{x}) = g(\mu y[h(\vec{x}, y) = 0])$$

com g e h recursivas primitivas.

- 2 Dada  $f(x) = \mu y[y^2 > x] + \mu z[z^3 > x]$ , reescreva f usando apenas uma minimização.
  - **Dica**: Codifique o par (y, z) como um único número e busque o primeiro par válido.
- 3 Por que não podemos eliminar completamente a minimização e expressar todas as funções computáveis usando apenas funções recursivas primitivas?

## Exercício 4: Predicado T de Kleene

Considere uma linguagem de programação simples onde programas são sequências de instruções sobre registradores.

- 1 Descreva informalmente como codificar:
  - Um programa como um número natural
  - Uma configuração (estado dos registradores) como um número
  - Uma computação (sequência de configurações) como um número
- 2 Explique por que o predicado "y codifica uma computação válida do programa e na entrada x" é recursivo primitivo.
- Por que a função que extrai o resultado de uma computação codificada é recursiva primitiva?

### Exercício 5: Indecidibilidade

#### Requer conhecimentos ainda não apresentados na disciplina!

- **1** Prove que o conjunto  $\{e : \varphi_e(0)\downarrow\}$  não é decidível. **Dica**: Reduza ao problema da parada.
- 2 Prove que o conjunto  $\{e : \varphi_e \text{ é constante}\}$  não é decidível. **Dica**: Use o Teorema de Rice.
- 3 Prove que não existe função computável f tal que:

$$f(e) = \begin{cases} 1 & \text{se } \varphi_e \text{ \'e total} \\ 0 & \text{caso contr\'ario} \end{cases}$$

A função de Ackermann é definida por:

$$A(m,n) = \begin{cases} n+1 & \text{se } m = 0\\ A(m-1,1) & \text{se } m > 0 \text{ e } n = 0\\ A(m-1,A(m,n-1)) & \text{se } m > 0 \text{ e } n > 0 \end{cases}$$

- 1 Mostre que A é recursiva total (não primitiva, mas total).
- **2** Escreva A na forma:

O Operador de Minimização

$$A(m,n) = g(\mu y[h(m,n,y) = 0])$$

onde g e h são recursivas primitivas.

**Dica**: h verifica se y codifica uma "tabela" completa de valores A(i, j) para  $i \le m$  e j suficientemente grande.

# Referências I

O Operador de Minimização

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. Introduction to Automata Theory, Languages, and Computation. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

Exercícios

Referências

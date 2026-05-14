<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Recapitulação: Por que Minimização?**
  - O Problema
  - A Solução
- **Definição Formal do Operador $\mu$**
  - Definição
  - Semântica Operacional
  - Algoritmo para $\mu y[g(\vec{x}, y) = 0]$
  - Observações
  - Por que “= 0”?
  - Convenção
  - Equivalência
  - Exemplo
- **Minimização Regular**
  - Definição
  - Propriedade
- **Minimização Limitada vs. Ilimitada**
  - Minimização Limitada (Recursiva Primitiva)
  - Minimização Ilimitada (Operador $\mu$ )
  - Implementação da Minimização Limitada
  - Teorema
  - Construção
  - Alternativa
  - Fechamento sob Minimização
  - Teorema
  - Prova (Esboço)
  - Composição de Minimizações
  - Teorema
  - Forma Normal de Kleene
  - Consequência
  - O Predicado T de Kleene
  - Teorema (Kleene)
  - Interpretação
  - Consequências da Forma Normal
- **Corolário 1: Enumeração Efetiva**
- **Corolário 2: Função Universal**
- **Corolário 3: Complexidade da Parcialidade**
- **Minimização e Totalidade**
  - Quando $\mu[g]$ é Total?
  - Condição Suficiente
  - Hierarquia de Funções
- **Aplicação 1: Inversa de Funções**
  - Problema
  - Solução
  - Parcialidade
- **Aplicação 2: Logaritmo Discreto**
  - Definição
  - Usando Minimização
  - Verificação
- **Aplicação 3: Números Primos**
  - O $n$ -ésimo Primo
  - Construção Recursiva
  - Por que é Total?
- **Aplicação 4: Função de Pareamento Inversa**
  - Recordando: Função de Pareamento de Cantor
  - Funções Inversas
- **Aplicação 5: Simulação de Máquinas de Turing**
  - Ideia
  - Predicado de Computação Válida
  - Resultado da Computação
- **Aplicação 6: O Problema da Parada**
  - Definição
  - Como Função
  - Teorema (Turing, 1936)
  - Prova
  - Consequências do Problema da Parada
  - Indecidibilidade
  - Teorema de Rice
- **Resumo: O Poder da Minimização**
  - O que a Minimização Adiciona
  - O Preço a Pagar
  - Equivalência com Máquinas de Turing
- **Exercício 1: Minimização Básica**
- **Exercício 2: Verificação de Totalidade**
- **Exercício 3: Forma Normal de Kleene**
  - Exercício 4: Predicado T de Kleene
- **Exercício 5: Indecidibilidade**
- **Desafio: Função de Ackermann via Minimização**
- **Referências I**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Minimização de Funções Recursivas Parciais

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 05  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

17 de março de 2026

The logo of the Escola Politécnica PUCRS. It features a crest with a shield, a star, and a book, with the text "PUCRS" below it. To the right of the crest, the words "ESCOLA" and "POLITÉCNICA" are stacked vertically in a bold, blue, sans-serif font.

Logo of Escola Politécnica PUCRS

{1}------------------------------------------------
## Sumário

- 1** O Operador de Minimização
- 2** Propriedades da Minimização
- 3** Aplicações da Minimização
- 4** Exercícios

A faint, gray watermark of the coat of arms of the University of Coimbra is visible on the right side of the slide. The shield features a central star and is flanked by two smaller shields with a repeating pattern of stylized trees. Above the shield is a crown, and below it is a ribbon with the Latin motto "AD VERVM DVICIT".

Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8c378a184b5ae4d1605cb74d7b7a7e3f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
## Recapitulação: Por que Minimização?
### O Problema

Funções recursivas primitivas são insuficientes:

- Todas são totais (sempre terminam)
- Não conseguem expressar busca ilimitada
- Função de Ackermann é computável mas não recursiva primitiva
### A Solução

O operador de **minimização** (operador  $\mu$ ) adiciona a capacidade de:

- Buscar o menor valor satisfazendo uma condição
- Expressar loops “while” que podem não terminar
- Capturar todas as funções computáveis

{3}------------------------------------------------
## Definição Formal do Operador $\mu$
### Definição

Seja  $g : \mathbb{N}^{k+1} \rightharpoonup \mathbb{N}$  uma função parcial.

A **minimização** de  $g$  é a função  $f : \mathbb{N}^k \rightharpoonup \mathbb{N}$ :

$$f(\vec{x}) = \mu y[g(\vec{x}, y) = 0]$$

definida como o **menor**  $y \in \mathbb{N}$  tal que:

- 1  $g(\vec{x}, 0) \downarrow, g(\vec{x}, 1) \downarrow, \dots, g(\vec{x}, y) \downarrow$  (todos definidos)
- 2  $g(\vec{x}, 0) \neq 0, g(\vec{x}, 1) \neq 0, \dots, g(\vec{x}, y-1) \neq 0$
- 3  $g(\vec{x}, y) = 0$

Se tal  $y$  não existe, então  $f(\vec{x}) \uparrow$  (indefinido).

{4}------------------------------------------------
### Semântica Operacional
### Algoritmo para $\mu y[g(\vec{x}, y) = 0]$

```
1 y = 0
2 while True:
3     # se g(x, y) não estiver definido, o programa falha (indefinido)
4     # se g(x, y) não convergir, o programa entra em loop infinito (ind)
5     if g(x, y) == 0:
6         return y
7     y = y + 1
```
### Observações

- É um loop `while`, não um loop `for`
- Pode não terminar se  $g(\vec{x}, y) \neq 0$  para todo  $y$
- Pode não terminar se  $g(\vec{x}, y) \uparrow$  para algum  $y$

{5}------------------------------------------------
### Por que “= 0”?
### Convenção

Usamos  $\mu y[g(\vec{x}, y) = 0]$  (busca por zero) em vez de  $\mu y[P(\vec{x}, y)]$  (busca por verdadeiro) por convenção.
### Equivalência

Para um predicado  $P(\vec{x}, y)$  (valores 0 ou 1):

$$\mu y[P(\vec{x}, y) = 1] = \mu y[1 \dot{-} P(\vec{x}, y) = 0]$$

Ou seja, podemos buscar por “verdadeiro” complementando o predicado.
### Exemplo

“Menor  $y$  tal que  $y^2 > x$ ” pode ser escrito como:

$$\mu y[\text{sg}(y^2 \dot{-} x) = 0]$$

{6}------------------------------------------------
## Minimização Regular
### Definição

A minimização  $\mu y[g(\vec{x}, y) = 0]$  é **regular** se, para toda entrada  $\vec{x}$ :

$$\exists y : g(\vec{x}, y) = 0$$

Ou seja, sempre existe um  $y$  que satisfaz a condição.
### Propriedade

Se  $g$  é recursiva primitiva e a minimização é regular, então  $\mu[g]$  é uma função **total**.
#### Exemplo: Raiz Quadrada Inteira

$$\text{sqr}(x) = \mu y[(y + 1)^2 > x]$$

Regular porque para  $y = x + 1$ , temos  $(x + 2)^2 > x$ .

{7}------------------------------------------------
## Minimização Limitada vs. Ilimitada
### Minimização Limitada (Recursiva Primitiva)

$$(\mu y \leq z)[g(\vec{x}, y) = 0] = \begin{cases} \text{menor } y \leq z : g(\vec{x}, y) = 0 & \text{se existir} \\ z + 1 & \text{caso contrário} \end{cases}$$

- Sempre termina (busca até  $z$ )
- Preserva recursividade primitiva
- Função total se  $g$  é total
### Minimização Ilimitada (Operador $\mu$ )

$$\mu y[g(\vec{x}, y) = 0]$$

- Pode não terminar
- Necessária para funções recursivas parciais
- Pode introduzir parcialidade

{8}------------------------------------------------
### Implementação da Minimização Limitada
### Teorema

Se  $g$  é recursiva primitiva, então  $(\mu y \leq z)[g(\vec{x}, y) = 0]$  também é.
### Construção

Defina  $f(\vec{x}, z) = (\mu y \leq z)[g(\vec{x}, y) = 0]$  por:

$$f(\vec{x}, z) = \sum_{i=0}^z \prod_{j=0}^i \text{sg}(g(\vec{x}, j))$$

**Ideia:** O produto é 1 enquanto todos  $g(\vec{x}, j) \neq 0$  (para  $j \leq i$ ), e vira 0 a partir do primeiro zero. A soma conta quantos “prefixos” não têm zero, dando o índice do primeiro zero.
### Alternativa

Podemos também definir por recursão primitiva diretamente.

{9}------------------------------------------------
### Fechamento sob Minimização
### Teorema

Se  $g : \mathbb{N}^{k+1} \rightharpoonup \mathbb{N}$  é recursiva parcial, então  $f = \mu[g]$  também é recursiva parcial.
### Prova (Esboço)

Por definição, o conjunto das funções recursivas parciais é o menor conjunto que:

- 1 Contém as funções básicas
- 2 É fechado sob composição
- 3 É fechado sob recursão primitiva
- 4 É fechado sob minimização

O item 4 garante diretamente o resultado.

{10}------------------------------------------------
### Composição de Minimizações
### Teorema

Toda função recursiva parcial pode ser expressa usando no máximo **uma** minimização aplicada a uma função recursiva primitiva.
### Forma Normal de Kleene

Para toda função recursiva parcial  $f : \mathbb{N}^k \rightarrow \mathbb{N}$ , existem funções recursivas primitivas  $g$  e  $h$  tais que:

$$f(\vec{x}) = g(\mu y[h(\vec{x}, y) = 0])$$
### Consequência

Minimizações aninhadas podem sempre ser “achatadas” em uma única minimização. A complexidade está na função recursiva primitiva, não na estrutura de minimizações.

{11}------------------------------------------------
### O Predicado T de Kleene
### Teorema (Kleene)

Existe um predicado recursivo primitivo  $T(e, x, y)$  e uma função recursiva primitiva  $U(y)$  tais que:

$$\varphi_e(x) = U(\mu y[T(e, x, y) = 0])$$

onde  $\varphi_e$  é a  $e$ -ésima função recursiva parcial.
### Interpretação

- $T(e, x, y)$ : “ $y$  codifica uma computação válida do programa  $e$  na entrada  $x$ ”
- $U(y)$ : extrai o resultado da computação codificada em  $y$
- A busca por  $y$  encontra a menor computação que termina

{12}------------------------------------------------
### Consequências da Forma Normal
## Corolário 1: Enumeração Efetiva

Existe uma enumeração computável  $\varphi_0, \varphi_1, \varphi_2, \dots$  de todas as funções recursivas parciais.

Dado  $e$ , podemos simular  $\varphi_e$  usando  $T$  e  $U$ .
## Corolário 2: Função Universal

A função  $U(e, x) = \varphi_e(x)$  é recursiva parcial.

$$U(e, x) = U'(\mu y [T(e, x, y) = 0])$$

onde  $U'$  é a função de extração (recursiva primitiva).
## Corolário 3: Complexidade da Parcialidade

Toda a “parcialidade” de uma função recursiva parcial está concentrada em uma única minimização ilimitada.

{13}------------------------------------------------
## Minimização e Totalidade
### Quando $\mu[g]$ é Total?

A função  $f(\vec{x}) = \mu y[g(\vec{x}, y) = 0]$  é total se e somente se:

$$\forall \vec{x} \exists y : g(\vec{x}, y) = 0 \text{ e } g(\vec{x}, 0), \dots, g(\vec{x}, y - 1) \text{ definidos}$$
### Condição Suficiente

Se  $g$  é recursiva primitiva (portanto total) e:

$$\forall \vec{x} \exists y : g(\vec{x}, y) = 0$$

então  $\mu[g]$  é total (e recursiva total, mas possivelmente não primitiva).
#### Observação

Verificar se  $\mu[g]$  é total é, em geral, **indecidível!**

{14}------------------------------------------------
### Hierarquia de Funções

A Venn diagram illustrating the hierarchy of recursive functions. It consists of three nested ellipses. The outermost ellipse is labeled "Recursivas Parciais". Inside it is a smaller ellipse labeled "Recursivas Totais". Inside that is the smallest ellipse, labeled "Recursivas Primitivas", which contains the symbols  $+, \times, !$ . To the right, within the "Recursivas Totais" ellipse but outside the "Recursivas Primitivas" ellipse, the word "Ackermann" is written in blue, with a blue "x" below it, indicating that the Ackermann function is a total recursive function but not a primitive recursive one.

Venn diagram showing the hierarchy of recursive functions: Recursivas Primitivas are a subset of Recursivas Totais, which are a subset of Recursivas Parciais. The Ackermann function is shown as an example of a total recursive function that is not primitive recursive.

- **Rec. Primitivas**  $\subset$  **Rec. Totais**  $\subset$  **Rec. Parciais**
- Todas as inclusões são **estritas**

{15}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-9ae17964ddd9b814c7d905b1af2fddf2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Venn diagram showing the hierarchy of recursive functions: Recursivas Primitivas are a subset of Recursivas Totais, which are a subset of Recursivas Parciais.
<!-- /IMAGE_DESCRIPTION -->
## Aplicação 1: Inversa de Funções
### Problema

Dada uma função  $g : \mathbb{N} \rightarrow \mathbb{N}$  injetora, encontrar  $g^{-1}$ .
### Solução

$$g^{-1}(y) = \mu x[g(x) = y] = \mu x[|g(x) - y| = 0]$$

Usando subtração truncada:

$$g^{-1}(y) = \mu x[(g(x) \dot{-} y) + (y \dot{-} g(x)) = 0]$$
### Parcialidade

$g^{-1}(y) \uparrow$  se  $y \notin \text{imagem}(g)$ .

Se  $g$  é bijetora, então  $g^{-1}$  é total.

{16}------------------------------------------------
## Aplicação 2: Logaritmo Discreto
### Definição

$\log_b(x) = \text{menor } y \text{ tal que } b^y \geq x \text{ (para } b > 1)$
### Usando Minimização

$$\log_b(x) = \mu y [b^{y+1} > x]$$

Ou equivalentemente:

$$\log_b(x) = \mu y [\text{sg}(b^{y+1} - x) = 1]$$
### Verificação

$$\log_2(8) = \mu y [2^{y+1} > 8]$$

- $y = 0: 2^1 = 2 \not> 8$
- $y = 1: 2^2 = 4 \not> 8$
- $y = 2: 2^3 = 8 \not> 8$
- $y = 3: 2^4 = 16 > 8 \checkmark$

{17}------------------------------------------------
## Aplicação 3: Números Primos
### O $n$ -ésimo Primo

Seja  $p(n)$  o  $n$ -ésimo número primo ( $p(0) = 2, p(1) = 3, \dots$ ).
### Construção Recursiva

$$p(0) = 2$$

$$p(n+1) = \mu y [y > p(n) \wedge \text{IsPrime}(y)]$$

onde  $\text{IsPrime}(y) = 1$  sse  $y$  é primo.
### Por que é Total?

Pelo postulado de Bertrand, sempre existe um primo entre  $n$  e  $2n$  para  $n > 1$ . Logo, a busca sempre termina.

{18}------------------------------------------------
## Aplicação 4: Função de Pareamento Inversa
### Recordando: Função de Pareamento de Cantor

$$\langle x, y \rangle = \frac{(x + y)(x + y + 1)}{2} + y$$
### Funções Inversas

$$\pi_1(z) = \mu x[\exists y \leq z : \langle x, y \rangle = z]$$

$$\pi_2(z) = \mu y[\langle \pi_1(z), y \rangle = z]$$

Ou usando a quantificação limitada (recursiva primitiva):

$$\pi_1(z) = (\mu x \leq z)[(\mu y \leq z)[\langle x, y \rangle = z] \leq z]$$
#### Observação

Como a função de pareamento é bijetora, as inversas são totais e, de fato, recursivas primitivas.

{19}------------------------------------------------
## Aplicação 5: Simulação de Máquinas de Turing
### Ideia

Podemos codificar:

- Uma Máquina de Turing  $M$  como um número  $e$
- Uma entrada  $w$  como um número  $x$
- Uma computação (sequência de configurações) como um número  $y$
### Predicado de Computação Válida

Existe predicado recursivo primitivo  $\text{Valid}(e, x, y)$  tal que:

$$\text{Valid}(e, x, y) = 1 \iff y \text{ codifica uma computação válida de } M_e \text{ em } x$$
### Resultado da Computação

$$\text{Result}(e, x) = U(\mu y[\text{Valid}(e, x, y)])$$

onde  $U$  extrai o resultado da computação codificada em  $y$ .

{20}------------------------------------------------
## Aplicação 6: O Problema da Parada
### Definição

O **problema da parada** pergunta: dado um programa  $e$  e entrada  $x$ ,  $\varphi_e(x)$  termina?
### Como Função

$$\text{HALT}(e, x) = \begin{cases} 1 & \text{se } \varphi_e(x) \downarrow \\ 0 & \text{se } \varphi_e(x) \uparrow \end{cases}$$
### Teorema (Turing, 1936)

HALT não é computável (não é recursiva parcial, nem total).
### Prova

Por diagonalização.

{21}------------------------------------------------
### Consequências do Problema da Parada
### Indecidibilidade

Muitos problemas são **indecidíveis** (não têm algoritmo):

- Determinar se um programa para em alguma entrada
- Determinar se dois programas computam a mesma função
- Determinar se um programa computa uma função total
- Verificar propriedades não-triviais de programas (Teorema de Rice)
### Teorema de Rice

Seja  $P$  uma propriedade não-trivial de funções recursivas parciais (i.e., algumas funções têm  $P$  e outras não).

Então o conjunto  $\{e : \varphi_e \text{ tem propriedade } P\}$  **não é decidível**.

{22}------------------------------------------------
## Resumo: O Poder da Minimização
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

{23}------------------------------------------------
## Exercício 1: Minimização Básica

Escreva as seguintes funções usando minimização e verifique se são totais:

- 1  $f(x) = \lfloor \sqrt{x} \rfloor$  (raiz quadrada inteira)
- 2  $g(x) = \lfloor \log_3 x \rfloor$  para  $x \geq 1$
- 3  $h(x, y) = \lfloor x/y \rfloor$  para  $y > 0$
- 4  $\text{prev\_prime}(x) = \text{maior primo} < x$  (para  $x > 2$ )
- 5  $\text{sqrt\_exact}(x) = \sqrt{x}$  se  $x$  é quadrado perfeito, indefinida caso contrário

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a cross and a star, surrounded by a ribbon with the Latin motto 'AD VERVM DVICIT'.

{24}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-082ba09313df59d76a7bfbdde8ec877d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a cross and a star, surrounded by a ribbon with the Latin motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
## Exercício 2: Verificação de Totalidade

Para cada função abaixo, determine se a minimização é regular (sempre encontra um zero) e, portanto, se a função resultante é total:

- 1  $f(x) = \mu y[y^2 \geq x]$
- 2  $g(x) = \mu y[2y = x]$
- 3  $h(x) = \mu y[y! > x]$
- 4  $p(x, y) = \mu z[x \cdot z = y]$
- 5  $q(x) = \mu y[\text{IsPrime}(x + y)]$

**Dica:** Para mostrar que é total, encontre um limitante para o valor de  $y$ .

A faint, stylized watermark of the coat of arms of the University of Coimbra is visible in the background. It features a shield with a cross and a crown, and the motto 'AD VERVM DVCT' written in a circular banner at the bottom.

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a cross and a crown, and the motto 'AD VERVM DVCT'.

{25}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-14bbaf9e8820aa362b68a5bc8d11a4c2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a cross and a crown, and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-70cae92d31b314bfb9688ed378706e86_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'D VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
## Exercício 3: Forma Normal de Kleene

- 1** **Desafio!** Explique por que toda função recursiva parcial pode ser escrita na forma:

$$f(\vec{x}) = g(\mu y[h(\vec{x}, y) = 0])$$

com  $g$  e  $h$  recursivas primitivas.

- 2** Dada  $f(x) = \mu y[y^2 > x] + \mu z[z^3 > x]$ , reescreva  $f$  usando apenas uma minimização.

**Dica:** Codifique o par  $(y, z)$  como um único número e busque o primeiro par válido.

- 3** Por que não podemos eliminar completamente a minimização e expressar todas as funções computáveis usando apenas funções recursivas primitivas?

{26}------------------------------------------------
### Exercício 4: Predicado T de Kleene

Considere uma linguagem de programação simples onde programas são sequências de instruções sobre registradores.

**1** Descreva informalmente como codificar:

- Um programa como um número natural
- Uma configuração (estado dos registradores) como um número
- Uma computação (sequência de configurações) como um número

**2** Explique por que o predicado “ $y$  codifica uma computação válida do programa  $e$  na entrada  $x$ ” é recursivo primitivo.

**3** Por que a função que extrai o resultado de uma computação codificada é recursiva primitiva?

A faint, semi-transparent watermark of the University of Coimbra's coat of arms is visible in the background. It features a shield with a cross and the motto 'D VERVM DVCT' (From truth, for truth) on a ribbon below.

Faint watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'D VERVM DVCT'.

{27}------------------------------------------------
## Exercício 5: Indecidibilidade

**Requer conhecimentos ainda não apresentados na disciplina!**

- 1 Prove que o conjunto  $\{e : \varphi_e(0) \downarrow\}$  não é decidível.  
**Dica:** Reduza ao problema da parada.
- 2 Prove que o conjunto  $\{e : \varphi_e \text{ é constante}\}$  não é decidível.  
**Dica:** Use o Teorema de Rice.
- 3 Prove que não existe função computável  $f$  tal que:

$$f(e) = \begin{cases} 1 & \text{se } \varphi_e \text{ é total} \\ 0 & \text{caso contrário} \end{cases}$$

{28}------------------------------------------------
## Desafio: Função de Ackermann via Minimização

A função de Ackermann é definida por:

$$A(m, n) = \begin{cases} n + 1 & \text{se } m = 0 \\ A(m - 1, 1) & \text{se } m > 0 \text{ e } n = 0 \\ A(m - 1, A(m, n - 1)) & \text{se } m > 0 \text{ e } n > 0 \end{cases}$$

- 1 Mostre que  $A$  é recursiva total (não primitiva, mas total).
- 2 Escreva  $A$  na forma:

$$A(m, n) = g(\mu y[h(m, n, y) = 0])$$

onde  $g$  e  $h$  são recursivas primitivas.

**Dica:**  $h$  verifica se  $y$  codifica uma “tabela” completa de valores  $A(i, j)$  para  $i \leq m$  e  $j$  suficientemente grande.

{29}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

A faint, grayscale watermark of a coat of arms is visible in the background. It features a shield with a cross and several smaller crosses. Above the shield is a crown, and below it is a ribbon with the Latin motto "AD VERVM DVOCIT".

Faint background watermark of a coat of arms featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

<!-- IMAGE_DESCRIPTION: datalab-c80dd550f724de455f5efebaed25198d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of a coat of arms featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-1d7527f4316cfe2d342b08d1653d1592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of Escola Politécnica PUCRS
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

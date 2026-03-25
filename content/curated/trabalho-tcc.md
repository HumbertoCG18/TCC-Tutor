---
entry_id: "trabalho-tcc"
title: "Trabalho Tcc"
backend: "pymupdf4llm"
source_pdf: "raw/pdfs/trabalhos/trabalho-tcc.pdf"
page_range: "1-5"
---
Trabalho T1 

Nomes: Humberto Corrêa Gomes, Gustavo Riffel dos Santos 

Data: 20/03/2026 

Turma:31 

Teoria da Computabilidade e Complexidade 

## **Parte 1** 

## **1) Sejam A = {1, 2, 3, 5} e B = {3, 4, 5}. Calcule A** $\cup$ **B, A $\cap$ B, A − B e B − A.** 

- a. A U B = {1,2,3,4,5} 

b. A $\cap$ B = {3, 5} 

c. A – B = {1, 2, 4} 

- d. B – A =  {4} 

## **2) Determine o conjunto das partes de C = {a, b} e informe sua cardinalidade** 

- a. P (C) = {$\emptyset$, {a}, {b}, {a,b}} 

- b. Cardinalidade: 


![](C:/Users/Humberto/Documents/GitHub/TCC-Tutor/staging/assets/inline-images/trabalho-tcc/trabalho-tcc.pdf-0001-14.png)


## **3) Explique a diferença entre conjunto finito, infinito enumerável e infinito não-enumerável.** 

- a.​ Conjunto Finito: Quantidade limitada de elementos​ 

- b.​ Conjunto Infinito Enumerável: Conjunto infinito que possui elementos que podem ser colocados em uma lista​ 

- c.​ Conjunto Infinito Não Numerável:Conjunto Infinito que possui elementos que não podem ser listados um a um como os naturais. 

--- end of page.page_number=1 ---

## **4) Considere a relação R = {(1, 2),(2, 4),(3, 6),(4, 8)}. Essa relação representa uma função de {1, 2, 3, 4} em N? Justifique.** 

- a.​ Cada elemento do domínio deve ter uma única imagem. ​ 

   - 1 – 2​ 

   - 2 - 4​ 

   - 3 - 6​ 

   - 4 - 8 

## **Parte 2** 

## **5) Mostre por que o conjunto dos números naturais pares é enumerável** 

- a.​ Para provar que P é enumerável, precisamos mostrar que existe uma função bijetora entre N e P. 

f(n) = 2n 

0 – 0 1 – 2 2 – 4 

## **6) Descreva uma estratégia de enumeração para Z.** 

- a.​ Uma maneira séria intercalar positivo e negativo ex: {0, 1, -1, 2, -2, $\ldots$} 

## **7) O conjunto Q é enumerável? Demonstre.** 

- a.​ Q é enumerável visto que {p/q : p, q $\in$ (N+) } pode ser visto como subconjunto de (N+) $\times$ (N+), (N+) $\times$ (N+) é enumerável (similar a N $\times$ N),  logo Q é enumerável 

## **8) Explique o argumento da diagonalização de Cantor e como ele prova que P(N) não é enumerável.** 

- a.​ Suponha que é enumerável 

- b.​ Liste subconjuntos 

- c.​ Crie novo conjunto diferente na diagonal 

- d.​ Esse conjunto não está na lista 

--- end of page.page_number=2 ---

## **9) Considere um alfabeto finito $\Sigma$. O conjunto $\Sigma$** ∗ **é finito, enumerável ou não-enumerável? Demonstre.** 

- a.​ Uma linguagem sobre um alfabeto $\Sigma$ ´é um subconjunto de $\Sigma$∗ . Logo é enumerável. 

## **Parte 3** 

## **10) Quais são as funções iniciais utilizadas na construção de funções recursivas primitivas?** 

- a.​ Função zero: Z 

- b.​ Função sucessor: S 

- c.​ Funções de projeção: P_i^k (LaTeX)​ 

## **11) Mostre como a multiplicação pode ser definida por recursão primitiva a partir das funções básicas. Assuma que a função add existe.** 

- a.​ mult(x, 0) = 0 = Z(x) 

- b.​ mult(x, y + 1) = mult(x, y) + x = add(P _3^3 (x, y,r), P _1^3 (x, y,r)) 

- c.​ mult(3, 0) = 0 ​ mult(3, 1) = mult(3, 0) + 3 = 0 + 3 = 3 

   - mult(3, 2) = mult(3, 1) + 3 = 3 + 3 = 6 

## **12) Explique o que significa dizer que “a classe das funções recursivas primitivas é fechada por composição e recursão primitiva”.** 

- a.​ Afirmar isso significa que essas operações, quando aplicadas a funções recursivas primitivas, produzem novamente funções recursivas primitivas. 

## **Parte 4** 

## **13) Diferencie função total de função parcial.** 

- a.​ Uma função é total quando está definida para todo x $\in$ A, isso é, cada elemento do domínio possui uma imagem em B. 

- b.​ Uma função é parcial quando não está definida para todos os elementos de A, logo, existe pelo menos um elemento do domínio para qual f(x) não existe. 

## **14) Explique o significado das notações $\phi$ₑ(x) $\downarrow$ e $\phi$ₑ(x) $\uparrow$** 

- a.​ Notação: $\phi$ₑ(x)$\downarrow$: ​ 

--- end of page.page_number=3 ---

A computação termina (para) Existe um resultado definido​ A função está definida naquele ponto ​ 

ex: Se um programa soma 2 + x: 

$\phi$ₑ(3) $\downarrow$ = 5 

Terminou → resultado existe 

- b.​ Notação: $\phi$ₑ(x) **$\uparrow$** 

A computação não termina Entra em loop infinito ou trava​ Não existe resultado 

ex: Um programa com loop infinito 

## **15) Explique porque o operador de minimização (µ) pode gerar funções parciais.** 

- a.​ Busca o menor y que satisfaz uma condição Expressar loops “while” que podem não terminar Capturar todas as funções computáveis 

## **16) Calcule µy [y 2 $\geq$ 20] e justifique o resultado encontrado.** 

a.​ µy [y² $\geq$ 20] y = 0 → 0 y = 1 → 1 y = 2 → 4 y = 3 → 9 y = 4 → 16 y = 5 → 25 

## **17) Para cada predicado abaixo, diga se a minimização é regular ou não-regular. Justifique cada classificação. (a) P1(x, y) : y $\geq$ x; (b) P2(x, y) : 2y = x + 1** 

- a.​ P1(x, y) : y $\geq$ x 

Sempre existe solução (y = x) 

Regular 

- b.​ P2(x, y) : 2y = x + 1 ==  y = (x + 1)/2 

Se x for par não existe número y inteiro. Não Regular 

--- end of page.page_number=4 ---

--- end of page.page_number=5 ---

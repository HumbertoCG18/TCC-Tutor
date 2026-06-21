<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Redução polinomial e provas de NP-completude**
- **Enunciado**
  - O que deve aparecer na apresentação
- **Critérios de avaliação**
  - Lista de problemas para escolha
- **Referências**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Trabalho T2: Seminário de NP-Compleitude
## Redução polinomial e provas de NP-completude

**Formato do grupo:** duplas ou trios (sem excessões).

**Formato da atividade:** apresentação oral em aula; todos os integrantes apresentam.

**Duração:** 15 minutos por grupo + perguntas.

**Data Entrega:** 12/06/2026 (data da apresentação).
## Enunciado

Cada grupo escolherá **um problema NP-completo** da lista fornecida e apresentará, de forma rigorosa e didática, a prova de NP-completude desse problema. O foco do trabalho não é apenas enunciar o problema, mas explicar a estrutura da redução, justificar sua correção (porque funciona) e mostrar que o problema pertence à classe NP.

O problema selecionado por cada grupo deve pertencer à lista abaixo. **Não é permitido repetir problemas e os problemas serão distribuídos por ordem de chegada.**
### O que deve aparecer na apresentação

1. Definição formal do problema-alvo e da versão de decisão estudada.
2. Explicação breve do problema-fonte usado na redução.
3. Argumento de que o problema-alvo pertence a NP.
4. Construção completa da redução, incluindo a transformação da instância.
5. Prova de correção da redução nas duas direções.
6. Justificativa de que a transformação executa em tempo polinomial.
7. Pelo menos um exemplo pequeno ilustrando a construção.
8. Bibliografia utilizada, com destaque para a **publicação original** da prova.
## Critérios de avaliação

25% Correção técnica da prova.

30% Clareza na explicação da redução e dos gadgets.

10% Organização da apresentação e respeito ao tempo.

10% Uso adequado de bibliografia.

{1}------------------------------------------------
### Lista de problemas para escolha

1. **3-Dimensional Matching (3DM)** *[Karp72]*  
Dadas três coleções disjuntas e um conjunto de triplas válidas, decidir se existe um subconjunto dessas triplas que emparelha exatamente uma vez cada elemento envolvido.
2. **Exact Cover** *[Karp72]*  
Dada uma família de subconjuntos, decidir se existe uma subfamília que cobre cada elemento do universo exatamente uma vez.
3. **Set Packing** *[Karp72]*  
Dada uma coleção de subconjuntos e um inteiro  $k$ , decidir se existem pelo menos  $k$  subconjuntos dois a dois disjuntos.
4. **Hitting Set** *[Karp72]*  
Dada uma família de subconjuntos e um inteiro  $k$ , decidir se existe um conjunto com no máximo  $k$  elementos que intersecta todos os subconjuntos da família.
5. **Clique Cover** *[Karp72]*  
Dado um grafo e um inteiro  $k$ , decidir se os vértices do grafo podem ser particionados em no máximo  $k$  cliques.
6. **Feedback Vertex Set** *[Karp72]*  
Dado um grafo e um inteiro  $k$ , decidir se é possível remover no máximo  $k$  vértices de modo que o grafo restante fique acíclico.
7. **Weighted Max Cut** *[Karp72]*  
Dado um grafo com pesos nas arestas e um limiar  $k$ , decidir se existe uma partição dos vértices em dois lados tal que o peso total das arestas que cruzam a partição seja pelo menos  $k$ .
8. **Feedback Arc Set** *[Karp72]*  
Dado um grafo dirigido e um inteiro  $k$ , decidir se é possível remover no máximo  $k$  arcos de modo que o grafo resultante fique acíclico.
9. **0/1 Integer Programming** *[Karp72]*  
Dado um sistema de desigualdades lineares, decidir se existe uma atribuição binária para as variáveis que satisfaça simultaneamente todas as restrições.
10. **Monotone 1-in-3 SAT** *[Schaefer78]*  
Dada uma fórmula booleana em que cada cláusula tem três variáveis sem negação, decidir se existe uma atribuição que torne exatamente uma variável verdadeira em cada cláusula.
11. **Planar 3-SAT** *[Lichtenstein82]*  
Dada uma instância de 3-SAT cujo grafo bipartido variável-cláusula é planar, decidir se a fórmula é satisfatível.
12. **3-Edge-Coloring de grafos cúbicos** *[Holyer81]*  
Dado um grafo cúbico, decidir se é possível colorir suas arestas com três cores de modo que arestas adjacentes recebam cores diferentes.

{2}------------------------------------------------
## Referências

- [Karp72] Richard M. Karp. *Reducibility Among Combinatorial Problems*. In Raymond E. Miller and James W. Thatcher (eds.), *Complexity of Computer Computations*, pp. 85–103. Plenum Press, 1972.
- [Schaefer78] Thomas J. Schaefer. *The Complexity of Satisfiability Problems*. In *Proceedings of the 10th Annual ACM Symposium on Theory of Computing (STOC)*, pp. 216–226, 1978.
- [Lichtenstein82] David Lichtenstein. *Planar Formulae and Their Uses*. *SIAM Journal on Computing*, 11(2):329–343, 1982.
- [Holyer81] Ian Holyer. *The NP-Completeness of Edge-Coloring*. *SIAM Journal on Computing*, 10(4):718–720, 1981.
- [GJ79] Michael R. Garey and David S. Johnson. *Computers and Intractability: A Guide to the Theory of NP-Completeness*. W. H. Freeman, 1979. Referência complementar para consultar formulações equivalentes, cadeias de reduções e comentários históricos.

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-29f586959675cafdf81cf934954908eb_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a Deterministic Finite Automaton (DFA) with three states: q0, q1, and q2.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-4ca62688976b4bef770a81683f9d9eef_img.jpg -->
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

<!-- IMAGE_DESCRIPTION: datalab-86b4670fc1a5a694821ee92b99c1209a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a Pushdown Automaton (PDA) for the language {0^n 1^n : n ≥ 0}.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-875c6f4f441fdd3ca7e1908fd1582983_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da Hierarquia de Chomsky mostrando a inclusão entre classes de linguagens.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-911a4f4b97be8e1dcf81e58b080dc0e2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9642ee15d719705144037077981aaa99_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-966c4b9785d85823782a007f3ecec1a7_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9911cc821dddfed7079ce56cbb907c9e_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9b77845519ed6ce33bab327fe59ace1c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9cc5ec27db4e35a26008bce9b9cd0bc8_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-b6cb8677b4ffb35c6468fa5c24091bff_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-c036e2540a94b31357ceb0002f0cacab_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da hierarquia das linguagens de Chomsky, mostrando cinco níveis concêntricos de complexidade crescente.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-f254a67565344d514e13763a4e556a70_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-fa6c61be003dfbb4ca5587e48a71de94_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-fb15f15a7d964c8490c9317e43e40c1a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of São Paulo (USP) coat of arms, featuring a shield with a star and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

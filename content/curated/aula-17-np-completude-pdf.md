<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Redução Polinomial**
  - Definição
  - Propriedades das Reduções
  - Transitividade
  - Implicação para Complexidade
  - Contrapositiva Importante
- **NP-Completeness: Definição**
  - Definição: NP-hard
  - Definição: NP-completo
  - Intuição
  - Importância de NP-Completo
  - Teorema Fundamental
  - Prova
  - Contrapositiva
- **Como Provar NP-Compleitude**
  - Método Padrão
  - O Primeiro Problema NP-Completo
  - Questão Fundamental
  - Mapa de NP-Completo
  - Anatomia de uma Redução
  - Estrutura Típica
  - Erro Comum
  - Ideia da Redução
  - Redução
  - Tempo
  - Redução
  - Correção
  - Dicas para Construir Reduções
  - Estratégias Comuns
  - Armadilhas
- **Lista de Problemas NP-Completo**
  - Problemas em Lógica
  - Problemas em Grafos
  - Mais Problemas NP-Completos
  - Problemas Numéricos
  - Outros Domínios
  - 3-SAT
  - Transformação de Cláusulas
  - Subset Sum
  - NP-Completeness
  - Caminho Hamiltoniano
  - NP-Completeness
  - 3-Coloração
  - Definição
  - Contraste
  - NP-Completo
- **Resumo da Aula**
  - Conceitos Principais
  - Problemas NP-Completos Vistos
- **Próxima Aula**
- **Exercício 1: Verdadeiro ou Falso?**
  - Objetivo
- **Exercício 2: Certificados e Verificadores**
  - Problemas
  - Dica
- **Exercício 3: Roteiro de prova de NP-completude**
  - Meta
- **Exercício 4: Reduções simples e clássicas**
  - Exercício 5: 3-SAT para CLIQUE
  - Exercício 7: De SAT para 3-SAT
  - Exercício 8: Classificando variantes
  - Exercício 9: SUBSET-SUM e pseudo-polinomialidade
- **Desafio 1: Prove NP-completude**
  - Problema DOMINATING-SET
- **Desafio 2: Comparando problemas difíceis**
  - Problema SUBGRAPH-ISOMORPHISM
- **Referências I**
- **Referências II**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Complexidade de Tempo: NP-Compleitude e Redução de Problemas

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 17

Teoria da Computabilidade e Complexidade  
Ciência da Computação

22 de maio de 2026

The logo of PUCRS, featuring a shield with a cross and a star, and the text 'PUCRS' below it.

Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

{1}------------------------------------------------

{2}------------------------------------------------
## Redução Polinomial
### Definição

Uma linguagem  $A$  é **reduzível em tempo polinomial** a  $B$ , denotada por  $A \leq_p B$ , se existe uma função  $f : \Sigma^* \rightarrow \Sigma^*$  tal que:

- 1  $f$  é computável em tempo polinomial
- 2  $\forall w : w \in A \iff f(w) \in B$

Diagram illustrating a polynomial-time reduction  $f$  from language  $A$  to language  $B$ . The diagram shows two ovals,  $A$  and  $B$ , connected by two horizontal arrows. The top arrow points from  $A$  to  $B$  and is labeled  $f$ . The bottom arrow points from  $B$  to  $A$  and is labeled "resposta". Below oval  $A$  is the text "instância  $w$ ", and below oval  $B$  is the text "instância  $f(w)$ ".

Diagram illustrating a polynomial-time reduction f from language A to language B. An oval labeled A is on the left, and an oval labeled B is on the right. A horizontal arrow points from A to B, labeled 'f' above it. A horizontal arrow points from B back to A, labeled 'resposta' below it. Below oval A is the text 'instância w', and below oval B is the text 'instância f(w)'.

[7, 6, 1]

{3}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-f89631cc38aa971e8d15cbffe28f1183_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram illustrating a polynomial-time reduction f from language A to language B.
<!-- /IMAGE_DESCRIPTION -->
### Propriedades das Reduções
### Transitividade

Se  $A \leq_p B$  e  $B \leq_p C$ , então  $A \leq_p C$ .

*Prova:* Composição de funções polinomiais é polinomial.
### Implicação para Complexidade

Se  $A \leq_p B$  e  $B \in P$ , então  $A \in P$ .

*Prova:* Compute-se  $f(w)$  em tempo polinomial e, em seguida, resolve-se  $B$  também em tempo polinomial. Logo, o custo total é polinomial.
### Contrapositiva Importante

Se  $A \leq_p B$  e  $A \notin P$ , então  $B \notin P$ .

Redução “transfere” dificuldade de  $A$  para  $B$ .

{4}------------------------------------------------
## NP-Completeness: Definição
### Definição: NP-hard

Um problema  $B$  é **NP-hard** se:

$$\forall A \in \text{NP} : A \leq_p B$$

Todo problema em NP se reduz polinomialmente a  $B$ .
### Definição: NP-completo

Um problema  $B$  é **NP-completo** se:

- 1  $B \in \text{NP}$
- 2  $B$  é NP-hard
### Intuição

Problemas NP-completos são os “mais difíceis” dentro de NP.  
Se qualquer um deles estiver em P, então  $P = \text{NP}$ .

{5}------------------------------------------------
### Importância de NP-Completo
### Teorema Fundamental

Se  $B$  é NP-completo e  $B \in P$ , então  $P = NP$ .
### Prova

- Seja  $A$  qualquer linguagem em NP
- Como  $B$  é NP-completo,  $A \leq_p B$
- Como  $B \in P$ , e reduções preservam  $P$ , temos  $A \in P$
- Portanto,  $NP \subseteq P$
- Como  $P \subseteq NP$  sempre, temos  $P = NP$
### Contrapositiva

Se  $P \neq NP$ , então nenhum problema NP-completo está em  $P$ .

{6}------------------------------------------------
## Como Provar NP-Compleitude
### Método Padrão

Para provar que  $B$  é NP-completo:

- 1 Mostrar que  $B \in \text{NP}$  (certificado + verificador)
- 2 Escolher um problema  $A$  já conhecido como NP-completo
- 3 Mostrar que  $A \leq_p B$
#### Por que funciona?

- Se  $A$  é NP-completo, todo problema em NP se reduz a  $A$
- Se  $A \leq_p B$ , por transitividade, todo problema em NP se reduz a  $B$
- Logo,  $B$  é NP-hard
- Combinando com  $B \in \text{NP}$ :  $B$  é NP-completo

{7}------------------------------------------------
### O Primeiro Problema NP-Completo
### Questão Fundamental

Como provar que o **primeiro** problema é NP-completo?  
Não podemos reduzir a partir de outro problema NP-completo!
#### Teorema de Cook-Levin (1971)

SAT (satisfatibilidade booleana) é NP-completo.  
A prova mostra diretamente que **todo** problema em NP se reduz a SAT, sem usar outro problema NP-completo.
#### Consequência

Uma vez estabelecido SAT como problema NP-completo, podemos provar a NP-completude de outros problemas por redução.

[2, 5, 7]

{8}------------------------------------------------
### Mapa de NP-Completo

```
graph TD; SAT[SAT] --> 3SAT[3-SAT]; 3SAT --> CLIQUE[CLIQUE]; 3SAT --> HAMPATH[HAMPATH]; 3SAT --> INDEPSET[INDEP-SET]; 3SAT --> SUBSETSUM[SUBSET-SUM]; 3SAT --> VERTEXCOVER[VERTEX-COVER]; 3SAT --> 3COLORING[3-COLORING]; CLIQUE --> INDEPSET; INDEPSET --> VERTEXCOVER;
```

Diagrama de redução de NP-completude mostrando a hierarquia de problemas. SAT (vermelho) reduz para 3-SAT (roxo). 3-SAT reduz para CLIQUE, HAMPATH, INDEP-SET, SUBSET-SUM, VERTEX-COVER e 3-COLORING. CLIQUE, INDEP-SET e VERTEX-COVER são verdes. HAMPATH, SUBSET-SUM e 3-COLORING são amarelos. Há também reduções entre CLIQUE, INDEP-SET e VERTEX-COVER.

Cada seta indica uma redução polinomial conhecida.

[2, 5, 3]

{9}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-dbe553cf16dd14073b89a8263a428664_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de redução de NP-completude mostrando a hierarquia de problemas.
<!-- /IMAGE_DESCRIPTION -->
### Anatomia de uma Redução
### Estrutura Típica

Para provar  $A \leq_p B$ :

- 1 Construção:** Dado  $w$  (instância de  $A$ ), construir  $f(w)$  (instância de  $B$ )
- 2 Correção (ida):** Provar que  $w \in A \Rightarrow f(w) \in B$
- 3 Correção (volta):** Provar que  $f(w) \in B \Rightarrow w \in A$
- 4 Eficiência:** Mostrar que  $f$  é computável em tempo polinomial
### Erro Comum

Provar apenas a “ida” não é suficiente! A equivalência  $w \in A \iff f(w) \in B$  requer ambas as direções.

[7, 6]

{10}------------------------------------------------
#### Exemplo: $3\text{-SAT} \leq_p \text{CLIQUE}$
#### Problema CLIQUE

**Entrada:** grafo  $G = (V, E)$  e inteiro  $k$ .

**Pergunta:**  $G$  contém clique de tamanho  $k$ ?
#### Problema 3-SAT

**Entrada:** fórmula  $\phi$  em 3-CNF.

**Pergunta:**  $\phi$  é satisfatível?
### Ideia da Redução

Dada fórmula  $\phi = C_1 \wedge C_2 \wedge \dots \wedge C_k$  com  $k$  cláusulas:

- Construir um grafo  $G$  em que uma clique de tamanho  $k$  corresponda a uma atribuição satisfatória

{11}------------------------------------------------
#### Redução $3\text{-SAT} \leq_p \text{CLIQUE}$ : Construção
#### Construção do Grafo $G$

Seja  $\phi = C_1 \wedge \dots \wedge C_k$  onde cada  $C_i = (\ell_{i1} \vee \ell_{i2} \vee \ell_{i3})$ .

**Vértices:** para cada literal  $\ell_{ij}$  na cláusula  $C_i$ , criar um vértice  $v_{ij}$ .

**Arestas:** conectar  $v_{ij}$  e  $v_{i'j'}$  se:

- $i \neq i'$  (cláusulas diferentes), e
- $\ell_{ij} \neq \overline{\ell_{i'j'}}$  (literais consistentes)
#### Exemplo

$\phi = (x_1 \vee \neg x_2 \vee x_3) \wedge (\neg x_1 \vee x_2 \vee x_3)$

- 6 vértices:  $\{x_1^1, \neg x_2^1, x_3^1, \neg x_1^2, x_2^2, x_3^2\}$
- Arestas entre literais consistentes de cláusulas distintas

[5, 3]

{12}------------------------------------------------
#### Redução $3\text{-SAT} \leq_p \text{CLIQUE}$ : Correção

Ida:  $\phi$  satisfatível  $\Rightarrow G$  tem clique de tamanho  $k$

- Seja  $\sigma$  uma atribuição satisfazendo  $\phi$
- Cada cláusula  $C_i$  tem pelo menos um literal verdadeiro; escolha um:  $\ell_{ij_i}$
- Os vértices  $\{v_{1j_1}, v_{2j_2}, \dots, v_{kj_k}\}$  formam clique:
  - São de cláusulas diferentes
  - São consistentes (todos verdadeiros sob  $\sigma$ )

Volta:  $G$  tem clique de tamanho  $k \Rightarrow \phi$  satisfatível

- Clique de tamanho  $k$  tem exatamente um vértice de cada cláusula
- Literais correspondentes são mutuamente consistentes
- Atribuição que torna esses literais verdadeiros satisfaz  $\phi$

{13}------------------------------------------------
#### Exemplo: $\text{CLIQUE} \leq_p \text{INDEPENDENT-SET}$
#### Problema INDEPENDENT-SET

**Entrada:** grafo  $G$  e inteiro  $k$ .

**Pergunta:** Existe conjunto de  $k$  vértices sem arestas entre si?
### Redução

Dado  $(G, k)$  para CLIQUE, construir  $(G', k)$  para INDEPENDENT-SET:

$$G' = \overline{G} \quad (\text{grafo complementar})$$

**Correção:**  $S$  é clique em  $G \iff S$  é conjunto independente em  $\overline{G}$
### Tempo

Construir  $\overline{G}$  custa  $O(|V|^2)$ , portanto é polinomial.

{14}------------------------------------------------
#### Exemplo: $\text{INDEPENDENT-SET} \leq_p \text{VERTEX-COVER}$
#### Problema VERTEX-COVER

**Entrada:** grafo  $G = (V, E)$  e inteiro  $k$ .

**Pergunta:** Existe  $S \subseteq V$  com  $|S| = k$  tal que toda aresta tenha pelo menos uma extremidade em  $S$ ?
### Redução

Dado  $(G, k)$  para INDEPENDENT-SET, construir  $(G, |V| - k)$  para VERTEX-COVER.
### Correção

$S$  é conjunto independente  $\iff V - S$  é cobertura de vértices.

*Prova:*  $S$  ser independente significa que nenhuma aresta tem ambas as extremidades em  $S$ ; logo, toda aresta tem pelo menos uma extremidade em  $V - S$ .

{15}------------------------------------------------
### Dicas para Construir Reduções
### Estratégias Comuns

- 1 **Componentes:** Criar “gadgets” que codificam variáveis, cláusulas, restrições
- 2 **Correspondência:** estabelecer uma bijeção entre soluções dos dois problemas
- 3 **Complemento:** às vezes a redução envolve complementar a estrutura
- 4 **Restrição:** mostrar que um caso especial de  $B$  captura  $A$
### Armadilhas

- Redução na direção errada ( $B \leq_p A$  em vez de  $A \leq_p B$ )
- Esquecer de provar a volta
- Construção não polinomial
- Assumir estrutura que a instância não necessariamente possui

{16}------------------------------------------------
## Lista de Problemas NP-Completo
### Problemas em Lógica

- SAT: Satisfatibilidade booleana
- 3-SAT: SAT com cláusulas de exatamente 3 literais
- CIRCUIT-SAT: Satisfatibilidade de circuitos
### Problemas em Grafos

- CLIQUE: Clique de tamanho  $k$
- INDEPENDENT-SET: Conjunto independente de tamanho  $k$
- VERTEX-COVER: Cobertura de vértices de tamanho  $k$
- HAMPATH / HAMCYCLE: Caminho/ciclo Hamiltoniano
- 3-COLORING: Coloração com 3 cores

{17}------------------------------------------------
### Mais Problemas NP-Completos
### Problemas Numéricos

- SUBSET-SUM: Subconjunto com soma igual a  $t$
- PARTITION: Particionar em dois subconjuntos de soma igual
- KNAPSACK (decisão): Mochila com valor  $\geq V$
- BIN-PACKING (decisão): Empacotar em  $k$  bins
### Outros Domínios

- TSP (decisão): Caixeiro viajante com custo  $\leq B$
- SET-COVER: Cobrir universo com  $k$  conjuntos
- SCHEDULING: Escalonamento com makespan  $\leq T$
- INTEGER-PROGRAMMING: Programação inteira

{18}------------------------------------------------
### 3-SAT
#### Definição

**Entrada:** Fórmula  $\phi$  em forma normal conjuntiva (CNF) onde cada cláusula tem **exatamente 3 literais**.

**Pergunta:** Existe atribuição que satisfaz  $\phi$ ?
#### Exemplo

$$\phi = (x_1 \vee \neg x_2 \vee x_3) \wedge (\neg x_1 \vee x_2 \vee \neg x_3) \wedge (x_1 \vee x_2 \vee x_3)$$

Satisfatível? Sim:  $x_1 = T, x_2 = T, x_3 = T$ .
#### Teorema

3-SAT é NP-completo.

*Prova:* Redução de SAT. Cláusulas com mais de 3 literais são divididas usando variáveis auxiliares.

{19}------------------------------------------------
#### Redução $SAT \leq_p 3\text{-SAT}$
### Transformação de Cláusulas

Cláusula  $C = (l_1 \vee l_2 \vee \dots \vee l_k)$ :

- $k = 1$ :  $(l_1) \rightarrow (l_1 \vee y_1 \vee y_2) \wedge (l_1 \vee y_1 \vee \neg y_2) \wedge \dots$
- $k = 2$ :  $(l_1 \vee l_2) \rightarrow (l_1 \vee l_2 \vee y) \wedge (l_1 \vee l_2 \vee \neg y)$
- $k = 3$ : Mantém como está
- $k > 3$ : Introduzir variáveis  $y_1, \dots, y_{k-3}$ :

$$\begin{aligned} & (l_1 \vee l_2 \vee y_1) \\ & \wedge (\neg y_1 \vee l_3 \vee y_2) \\ & \wedge (\neg y_2 \vee l_4 \vee y_3) \\ & \vdots \\ & \wedge (\neg y_{k-3} \vee l_{k-1} \vee l_k) \end{aligned}$$

{20}------------------------------------------------
### Subset Sum
#### Definição

**Entrada:** conjunto  $S = \{a_1, \dots, a_n\}$  de inteiros positivos e alvo  $t$ .

**Pergunta:** Existe  $S' \subseteq S$  tal que  $\sum_{a \in S'} a = t$ ?
#### Exemplo

$S = \{2, 3, 5, 7, 11\}$ ,  $t = 15$

Solução:  $S' = \{3, 5, 7\}$  pois  $3 + 5 + 7 = 15$ .
### NP-Completeness

Sua NP-completeness pode ser provada por redução de 3-SAT.

Ideia: números codificam variáveis e cláusulas de modo que uma soma correta corresponda a uma atribuição satisfatória.

[5, 3, 6]

{21}------------------------------------------------
### Caminho Hamiltoniano
#### Definição

**Entrada:** grafo direcionado  $G$  e vértices  $s$  e  $t$ .

**Pergunta:** existe um caminho de  $s$  a  $t$  que visita cada vértice exatamente uma vez?
#### Exemplo

```
graph LR; s((s)) --> a((a)); s((s)) --> b((b)); a((a)) --> t((t)); b((b)) --> t((t));
```

Diagrama de um grafo direcionado com vértices s, a, b e t. Há arestas direcionadas de s para a, s para b, a para t e b para t. Um caminho Hamiltoniano é destacado em vermelho, seguindo a sequência s -> a -> b -> t.

Caminho Hamiltoniano:  $s \rightarrow a \rightarrow b \rightarrow t$

<!-- IMAGE_DESCRIPTION: datalab-04dc3838022e96d8d5548bb1b777b38c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de um grafo direcionado com vértices s, a, b e t.
<!-- /IMAGE_DESCRIPTION -->
### NP-Completeness

Sua NP-completeness é demonstrada por redução de 3-SAT usando *gadgets*.

{22}------------------------------------------------
### 3-Coloração
### Definição

**Entrada:** grafo não direcionado  $G$ .

**Pergunta:** é possível colorir os vértices com 3 cores de modo que vértices adjacentes tenham cores diferentes?
### Contraste

- 2-COLORING: Em P (verificar se grafo é bipartido)
- 3-COLORING: NP-completo
- $k$ -COLORING para  $k \geq 3$ : NP-completo
### NP-Completo

Sua NP-completude pode ser obtida por redução de 3-SAT usando *gadgets* para variáveis e cláusulas.

{23}------------------------------------------------
## Resumo da Aula
### Conceitos Principais

- **NP-completo** = NP-hard + em NP
- **Redução polinomial**  $A \leq_p B$ : transfere dificuldade
- **Primeiro NP-completo**: SAT (Teorema de Cook-Levin)
- **Provar NP-completude**: reduzir a partir de um problema NP-completo conhecido
### Problemas NP-Completos Vistos

SAT, 3-SAT, CLIQUE, INDEPENDENT-SET, VERTEX-COVER, HAMPATH, SUBSET-SUM e 3-COLORING
## Próxima Aula

Teorema de Cook-Levin: prova de que SAT é NP-completo.

{24}------------------------------------------------
## Exercício 1: Verdadeiro ou Falso?

Classifique cada afirmação como verdadeira (V) ou falsa (F) e justifique.

- 1 Todo problema NP-completo pertence a NP.
- 2 Se  $A \leq_p B$  e  $B \in P$ , então  $A \in P$ .
- 3 Se um problema NP-hard estiver em P, então necessariamente  $P = NP$ .
- 4 Toda redução polinomial preserva a resposta SIM/NÃO.
- 5 Se um problema está em NP, então já sabemos um algoritmo polinomial para resolvê-lo.
### Objetivo

Fixar a diferença entre **estar em NP**, **ser NP-hard** e **ser NP-completo**.

[7, 6, 3]

{25}------------------------------------------------
## Exercício 2: Certificados e Verificadores

Para cada problema abaixo, descreva:

- 1 um certificado;
- 2 um verificador;
- 3 o tempo do verificador.
### Problemas

- SUBSET-SUM
- HAMCYCLE
- SET-COVER
- LONGEST-PATH
### Dica

Use sempre uma **solução candidata curta**; o verificador só precisa checar se ela funciona.

{26}------------------------------------------------
## Exercício 3: Roteiro de prova de NP-completude

Explique como provar que um problema  $B$  é NP-completo.

- 1 O que precisa ser mostrado para concluir  $B \in NP$ ?
- 2 Por que não basta reduzir  $B$  para um problema já conhecido?
- 3 Qual é a direção correta da redução?
- 4 Por que a escolha do problema de origem importa?
- 5 O que se conclui se  $A$  é NP-completo,  $A \leq_p B$  e  $B \in NP$ ?
### Meta

Este exercício é sobre o **método** da prova, não sobre um problema específico.

[7, 6, 3]

{27}------------------------------------------------
## Exercício 4: Reduções simples e clássicas

Prove as seguintes reduções.

- 1 CLIQUE  $\leq_p$  INDEP-SET
- 2 INDEP-SET  $\leq_p$  VERTEX-COVER
- 3 HAMPATH  $\leq_p$  HAMCYCLE
- 4 VERTEX-COVER  $\leq_p$  SET-COVER

[5, 3]

{28}------------------------------------------------
### Exercício 5: 3-SAT para CLIQUE

Considere a fórmula:

$$\phi = (x_1 \vee x_2 \vee \neg x_3) \wedge (\neg x_1 \vee x_2 \vee x_3) \wedge (x_1 \vee \neg x_2 \vee x_3)$$

- 1 Construa o grafo  $G$  da redução  $3\text{-SAT} \leq_p \text{CLIQUE}$ .
- 2 Quantos vértices  $G$  possui?
- 3 Qual deve ser o valor de  $k$ ?
- 4 Encontre uma clique válida e recupere a atribuição correspondente.
- 5 Verifique que a atribuição satisfaz  $\phi$ .

[5, 3]

{29}------------------------------------------------
### Exercício 7: De SAT para 3-SAT

1 Transforme a cláusula  $(x_1 \vee x_2 \vee x_3 \vee x_4 \vee x_5)$  em uma fórmula 3-CNF equissatisfatível.

2 Transforme a cláusula

$$(x_1 \vee x_2)$$

em uma fórmula 3-CNF equissatisfatível.

3 Explique por que não podemos simplesmente escrever

$$(x_1 \vee x_2 \vee x_3) \wedge (x_4 \vee x_5).$$

4 Para uma cláusula com  $k > 3$  literais, quantas cláusulas 3-CNF são geradas?
#### Observação

A transformação deve preservar **satisfatibilidade**, não equivalência lógica literal.

{30}------------------------------------------------
### Exercício 8: Classificando variantes

Determine a complexidade e justifique:

- 1 2-SAT
- 2 2-COLORING
- 3 CLIQUE em grafos bipartidos
- 4 HAMPATH em DAGs
- 5 SHORTEST-PATH-LEQ

![Coat of arms of the University of São Paulo (USP) with the text [7, 6, 3] overlaid.](011d7628370283ec23a24c1772507121_img.jpg)

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central vertical band containing a stylized 'M' and 'U' monogram, flanked by two vertical bands with a repeating pattern of small crosses. Above the shield is a crown, and on either side are crossed keys. A banner at the bottom reads 'AD VERVM DVCIT'. Overlaid on the lower right part of the shield is the text '[7, 6, 3]' in blue.

Coat of arms of the University of São Paulo (USP) with the text [7, 6, 3] overlaid.

{31}------------------------------------------------
### Exercício 9: SUBSET-SUM e pseudo-polinomialidade

- 1 Por que a redução  $3\text{-SAT} \leq_p \text{SUBSET-SUM}$  continua polinomial mesmo usando números grandes?
- 2 O que mudaria se a entrada estivesse em representação unária?
- 3 O que significa dizer que SUBSET-SUM é **fracamente NP-completo**?
- 4 O que é um algoritmo **pseudo-polinomial**?
- 5 Qual é a diferença entre ser polinomial em  $t$  e ser polinomial no tamanho binário de  $t$ ?
- 6 Por que isso é importante ao classificar problemas numéricos?

[3, 6, 1]

{32}------------------------------------------------
## Desafio 1: Prove NP-completude
### Problema DOMINATING-SET

**Entrada:** grafo  $G = (V, E)$  e inteiro  $k$ .

**Pergunta:** existe  $D \subseteq V$  com  $|D| \leq k$  tal que todo vértice está em  $D$  ou é adjacente a algum vértice de  $D$ ?

- 1 Mostre que DOMINATING-SET está em NP.
- 2 Reduza VERTEX-COVER a DOMINATING-SET.
- 3 Explique por que a redução mostra NP-hardness.
- 4 Conclua a prova de NP-completude.

[5, 3, 7]

{33}------------------------------------------------
## Desafio 2: Comparando problemas difíceis
### Problema SUBGRAPH-ISOMORPHISM

**Entrada:** grafos  $G$  e  $H$ .

**Pergunta:**  $G$  contém  $H$  como subgrafo?

- 1 Mostre que o problema pertence a NP.
- 2 Mostre que  $\text{CLIQUE} \leq_p \text{SUBGRAPH-ISOMORPHISM}$ .
- 3 Explique por que escolher  $H = K_k$  é natural nessa redução.
- 4 Discuta por que esse problema parece mais geral do que  $\text{CLIQUE}$ .
- 5 Conclua o que isso sugere sobre sua dificuldade.

[5, 3, 6]

{34}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] Stephen A. Cook. “The Complexity of Theorem-Proving Procedures”. Em: *Proceedings of the Third Annual ACM Symposium on Theory of Computing*. 1971, pp. 151–158.  
DOI: [10.1145/800157.805047](https://doi.org/10.1145/800157.805047).
- [3] Michael R. Garey e David S. Johnson. *Computers and Intractability: A Guide to the Theory of NP-Completeness*. W. H. Freeman, 1979.
- [4] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.

{35}------------------------------------------------
## Referências II

- [5] Richard M. Karp. “Reducibility Among Combinatorial Problems”. Em: *Complexity of Computer Computations*. Springer, 1972, pp. 85–103. DOI: [10.1007/978-1-4684-2001-2\\_9](https://doi.org/10.1007/978-1-4684-2001-2_9).
- [6] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [7] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-d3294dc879b451b369c0b06f42e9b39f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

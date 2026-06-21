<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Problema-alvo: o que é 3-Edge-Coloring?**
  - VERSÃO DE DECISÃO
  - 3-Edge-Coloring (cúbico)
- **Problema-fonte: o que é 3-SAT?**
  - EXEMPLO · FÓRMULA 3-SAT
- **Pertencimento a NP**
- **1**
  - O CERTIFICADO
- **2**
  - VERIFICAÇÃO LOCAL
- **3**
  - TEMPO POLINOMIAL
- **Construção da redução: codificação booleana**
  - REPRESENTAÇÃO VISUAL
  - VERDADEIRO
  - FALSO
  - GADGET INVERSOR ( $\neg$ )
- **Construção da redução: os três gadgets**
  - GADGET DE VARIÁVEL
  - GADGET INVERSOR ( $\neg$ )
  - GADGET DE CLÁUSULA
  - FECHAMENTO CÚBICO
  - RECEITA DE MONTAGEM
- **Correção da redução**
  - DA SATISFAÇÃO À COLORAÇÃO
  - DA COLORAÇÃO À SATISFAÇÃO
  - A redução executa em tempo polinomial
  - Gadgets criados.
  - ANÁLISE ASSINTÓTICA
  - Exemplo: $\Phi = (x \vee \neg y \vee z)$
  - FÓRMULA DE UMA ÚNICA CLÁUSULA
  - CONSTRUÇÃO CONCEITUAL DE $G_\Phi$
- **CONCLUSÃO**
- **Síntese da prova**
  - ① PERTENCIMENTO A NP
  - 3-Edge-Coloring $\in$ NP
  - ② CORREÇÃO DA REDUÇÃO
  - ③ REDUÇÃO POLINOMIAL $3\text{-SAT} \leq_P 3\text{-EDGE-COLORING}$
- **Referências**
  - PUBLICAÇÃO ORIGINAL
- **REFERÊNCIAS COMPLEMENTARES**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

---

TRABALHO 2 - TEORIA DA COMPUTABILIDADE E COMPLEXIDADE

# 3-Edge-Coloring *de grafos cúbicos*

A diagram of a complete graph K4 with 4 vertices and 6 edges. The vertices are arranged in a diamond shape with one vertex in the center (though it's actually a planar projection of K4 where the 'center' is an intersection of two edges). The edges are colored to show a 3-edge coloring: the outer boundary edges are blue (top-left and bottom-right) and red (top-right and bottom-left), while the two crossing internal edges are yellow/gold.

*A prova de NP-completude de Ian Holyer (1981) — redução polinomial a partir do 3-SAT, gadgets booleanos e a construção do grafo  $G_{\Phi}$ .*

---

*Pedro Jucewicz, João Medeiros, Calvin Silva*

{1}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-68d50e85fb8de4fae0e0eafaf20e63c0_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A diagram of a complete graph K4 with 4 vertices and 6 edges.
<!-- /IMAGE_DESCRIPTION -->
## Problema-alvo: o que é 3-Edge-Coloring?

**Grafo cúbico.** Grafo em que *todo vértice tem grau exatamente 3*, isto é, possui três arestas incidentes.

**Coloração própria de arestas.** Atribuição de cores às arestas de modo que *duas arestas adjacentes* — que compartilham um vértice — recebam *cores diferentes*.

**Índice cromático  $\chi'(G)$ .** Menor número de cores necessário para uma coloração própria de arestas de  $G$ .

**Teorema de Vizing.** Para um grafo simples,  $\chi'(G) \in \{\Delta(G), \Delta(G)+1\}$ . Em grafos cúbicos,  $\Delta = 3$ , logo  $\chi'(G) \in \{3, 4\}$ : o grafo é de *classe 1* ou *classe 2*.
### VERSÃO DE DECISÃO
### 3-Edge-Coloring (cúbico)

**Entrada:** um grafo cúbico  $G = (V, E)$ .

**Pergunta:** existe uma função  $c : E \rightarrow \{1, 2, 3\}$  tal que, para todo par de arestas adjacentes  $e, f$ , vale  $c(e) \neq c(f)$ ?

.....

*Equivalentemente:* decidir se  $\chi'(G) = 3$  (classe 1) ou  $\chi'(G) = 4$  (classe 2).

**RESULTADO DE HOLYER (1981)** » *Decidir se um grafo cúbico está na classe 1 é NP-completo* — apesar de a fronteira ser apenas entre 3 e 4 cores.

{2}------------------------------------------------
## Problema-fonte: o que é 3-SAT?

*O problema NP-completo clássico de satisfatibilidade booleana — referência da redução de Holyer.*

**Entrada.** Uma fórmula booleana  $\Phi$  em *forma normal conjuntiva* (CNF), em que cada cláusula contém exatamente três literais.

**Pergunta.** Existe uma atribuição de valores verdadeiro/falso às variáveis que torne  $\Phi$  verdadeira? Como  $\Phi$  é uma conjunção de cláusulas, isso significa que *cada cláusula deve ter ao menos um literal verdadeiro*.

**Cook-Levin (1971).** SAT é NP-completo; a forma restrita 3-SAT permanece NP-completa.

**Estratégia de Holyer.** Transformar  $\Phi$  em um grafo cúbico  $G_\Phi$  tal que

$\Phi$  é satisfazível  $\Leftrightarrow G_\Phi$  admite 3-edge-coloring
### EXEMPLO · FÓRMULA 3-SAT

$$\begin{aligned}\Phi = & (x \vee y \vee \neg z) \\ & \wedge (\neg x \vee y \vee w) \\ & \wedge (x \vee \neg y \vee \neg w)\end{aligned}$$

- **3 variáveis** distintas:  $x, y, z, w$
- **3 cláusulas**, cada uma com 3 literais
- **Literais** = variável ou sua negação
- Satisfazer  $\Phi$  = escolher  $x, y, z, w \in \{V, F\}$  de modo que *toda* cláusula tenha pelo menos um literal verdadeiro.

Como  $3\text{-SAT} \in \text{NP-completo}$ , basta construir uma redução polinomial  $3\text{-SAT} \leq_p 3\text{-Edge-Coloring}$  para concluir que o problema-alvo também é NP-completo.

{3}------------------------------------------------
## Pertencimento a NP

*Para mostrar que um problema está em NP, exibimos um certificado verificável em tempo polinomial.*
## 1
### O CERTIFICADO

Uma lista que informa, para cada aresta  $e \in E$ , a cor atribuída:

$$c : E \rightarrow \{1, 2, 3\}$$

O tamanho do certificado é  $O(|E|)$ , portanto polinomial no tamanho de  $G$ .
## 2
### VERIFICAÇÃO LOCAL

Para cada vértice  $v \in V$ , examinamos suas **3 arestas incidentes** e checamos se as três cores são *duas a duas distintas*.

Cada vértice exige apenas 3 comparações. Como  $G$  é cúbico, há  $|V|$  vértices e a verificação é puramente *local*.
## 3
### TEMPO POLINOMIAL

A verificação completa custa  $O(|V|) = O(|E|)$  operações constantes (em grafo cúbico,  $|E| = 3|V|/2$ ).

Linear no tamanho da entrada — portanto polinomial.

**CONCLUSÃO** » Existe certificado de tamanho polinomial e verificador de tempo polinomial. Logo, **3-Edge-Coloring de grafos cúbicos pertence a NP**.

{4}------------------------------------------------
## Construção da redução: codificação booleana

A redução de Holyer baseia-se em *gadgets*: pequenos sub-grafos cuidadosamente projetados para que sua coloração imponha um **comportamento lógico** específico.

Os gadgets se comunicam por **pares de arestas de interface**. A regra de codificação é puramente *relacional*:

```
mesma cor → verdadeiro
cores diferentes → falso
```

Observe: o significado *não depende* de qual cor específica é usada. Só importa se as duas arestas concordam ou divergem. Essa abstração permite encadear gadgets livremente.
### REPRESENTAÇÃO VISUAL
### VERDADEIRO

mesma cor

par = (vermelho, vermelho)
### FALSO

cores diferentes

par = (vermelho, azul)
### GADGET INVERSOR ( $\neg$ )

Diagram of the Inverter gadget. It shows two pairs of horizontal lines representing edges. The input on the left consists of two red lines, labeled 'entrada: V' (true). An arrow points from these lines to a black rectangular box labeled 'inversor'. Another arrow points from the box to two output lines on the right, one red and one blue, labeled 'saída: F' (false).

Força a saída a representar o valor contrário da entrada.  
usado em literais negados ( $\neg x$ )

{5}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-f11b8f19a9a2518acf8ea2482a5579d2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of the Inverter gadget. It shows two pairs of horizontal lines representing edges. The input on the left consists of two red lines, labeled 'entrada: V' (true). An arrow points from these lines to a black...
<!-- /IMAGE_DESCRIPTION -->
## Construção da redução: os três gadgets
### GADGET DE VARIÁVEL
#### Coerência entre ocorrências

Uma variável pode aparecer várias vezes em  $\Phi$ . O gadget garante que **todas as saídas associadas a uma mesma variável carreguem o mesmo valor**.

$V = \text{todas as saídas} = V$

Diagram of a variable gadget. A black box labeled 'x' has three red lines extending from it to the right, labeled 'ocorrência 1', 'ocorrência 2', and 'ocorrência 3'.

<!-- IMAGE_DESCRIPTION: datalab-1be8e9cad5f38fa47bdb81e549a3bec9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a variable gadget. A black box labeled 'x' has three red lines extending from it to the right, labeled 'ocorrência 1', 'ocorrência 2', and 'ocorrência 3'.
<!-- /IMAGE_DESCRIPTION -->
### GADGET INVERSOR ( $\neg$ )
#### Negação de um literal

Recebe um par de arestas de interface e produz o valor oposto. Usado sempre que um literal aparece **negado** ( $\neg x$ ) na fórmula  $\Phi$ .

mesma cor = V | cores diferentes = F

Diagram of an inverter gadget. Two examples are shown. The first shows two red lines entering a black box labeled 'inversor' from the left, and two blue lines exiting to the right, labeled 'saída: F'. The second shows two blue lines entering the box, and two red lines exiting, labeled 'saída: V'. Below the boxes, the logic is summarized: 'V entra -> F sai | F entra -> V sai'.

<!-- IMAGE_DESCRIPTION: datalab-43fec6623ab9cb223a9ff74e2d2a4402_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of an inverter gadget. Two examples are shown. The first shows two red lines entering a black box labeled 'inversor' from the left, and two blue lines exiting to the right, labeled 'saída: F'. The second shows...
<!-- /IMAGE_DESCRIPTION -->
### GADGET DE CLÁUSULA
#### Simula um OR de 3 entradas

Recebe **três pares de arestas** ( $l_1, l_2, l_3$ ). É 3-edge-colorable **se e somente se** pelo menos uma entrada é verdadeira.

| $l_1$ | $l_2$ | $l_3$ | colorível? |
|-------|-------|-------|------------|
| F     | F     | F     | x não      |
| V     | F     | F     | ✓ sim      |
| F     | V     | F     | ✓ sim      |
| F     | F     | V     | ✓ sim      |
| V     | V     | V     | ✓ sim      |

(demais combinações com ao menos um V também são coloríveis)
### FECHAMENTO CÚBICO

A montagem de gadgets (variáveis  $\rightarrow$  inversores  $\rightarrow$  cláusulas) gera o **pré-grafo**  $H_\Phi$  com *pontas soltas*. Para fechar e tornar todo vértice de grau 3, Holyer toma **duas cópias** de  $H_\Phi$  e identifica as pendências correspondentes, obtendo o grafo cúbico  $G_\Phi$ .
### RECEITA DE MONTAGEM

para cada variável  $\rightarrow$  1 gadget de variável  
 para cada  $\neg$ literal  $\rightarrow$  1 inversor  
 para cada cláusula  $\rightarrow$  1 gadget de cláusula  
 ao final  $\rightarrow$  duplicar  $H_\Phi = G_\Phi$  cúbico

{6}------------------------------------------------
## Correção da redução

A correção da redução exige verificar a equivalência nas duas direções ( $\Rightarrow$ ) e ( $\Leftarrow$ ).

Green arrow pointing right, indicating the direction of the proof from satisfiability to 3-edge-coloring.

<!-- IMAGE_DESCRIPTION: datalab-c1c7af7ea36be0323047962df57d75b0_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Green arrow pointing right, indicating the direction of the proof from satisfiability to 3-edge-coloring.
<!-- /IMAGE_DESCRIPTION -->
### DA SATISFAÇÃO À COLORAÇÃO

**Se  $\Phi$  é satisfazível,  $G_\Phi$  admite 3-edge-coloring.**

Tome uma atribuição V/F que satisfaz  $\Phi$ .

1. Configure cada *gadget de variável* de acordo com o valor escolhido para a variável. Todas as saídas passam a carregar o mesmo valor.
2. Para cada literal negado, o sinal passa por um *inversor*, trocando V por F e F por V.
3. Como a atribuição satisfaz  $\Phi$ , cada cláusula tem pelo menos um literal verdadeiro — portanto cada *gadget de cláusula* recebe ao menos uma entrada V e, pela sua propriedade, admite coloração.

Colorindo cada gadget de modo compatível, obtemos uma 3-coloração própria de  $G_\Phi$ . ■

Red arrow pointing left, indicating the direction of the proof from 3-edge-coloring to satisfiability.

<!-- IMAGE_DESCRIPTION: datalab-48d61f7cf40bacce4d63f9e98ea225fb_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Red arrow pointing left, indicating the direction of the proof from 3-edge-coloring to satisfiability.
<!-- /IMAGE_DESCRIPTION -->
### DA COLORAÇÃO À SATISFAÇÃO

**Se  $G_\Phi$  é 3-edge-colorable,  $\Phi$  é satisfazível.**

Tome uma 3-coloração própria de  $G_\Phi$ .

1. Leia o valor de cada par de arestas de interface: *mesma cor*  $\Rightarrow$  verdadeiro; *cores diferentes*  $\Rightarrow$  falso.
2. O gadget de variável garante coerência: todas as ocorrências de uma mesma variável recebem o mesmo valor; os inversores tratam corretamente as ocorrências negadas.
3. Cada gadget de cláusula só está colorido se pelo menos uma de suas três entradas for verdadeira — logo, cada cláusula de  $\Phi$  tem pelo menos um literal verdadeiro.

A atribuição extraída satisfaz  $\Phi$ . ■

**CONCLUSÃO** » as duas direções estabelecem a equivalência  $\Phi \in 3\text{-SAT} \Leftrightarrow G_\Phi \in 3\text{-Edge-Coloring}$ .

{7}------------------------------------------------
### A redução executa em tempo polinomial

*A transformação cria um número controlado de gadgets, e cada gadget tem tamanho constante ou linear em suas conexões.*

**Parâmetros da fórmula.** Seja  $\Phi$  com  $n$  variáveis e  $m$  cláusulas. Como cada cláusula tem 3 literais, há exatamente  **$3m$**  ocorrências de literais.
### Gadgets criados.

- **1 gadget de cláusula** por cláusula — total:  $m$ .
- **1 gadget de variável** por variável, com tamanho proporcional ao nº de ocorrências da variável — soma das ocorrências =  $3m$ .
- **1 inversor** por literal negado — no máximo  $3m$ .

A duplicação final para fechamento cúbico apenas multiplica o tamanho por 2, mantendo a complexidade polinomial.
### ANÁLISE ASSINTÓTICA

$$|\Phi| = O(n + m)$$

$$\#ocorrências = 3m$$

$$\#gadgets = O(n + m)$$

$$|G_\Phi| = O(n + m)$$

*Cada gadget tem tamanho constante ou linear no nº de ocorrências que conecta. A construção total cresce **linearmente** no tamanho da entrada.*

**PORTANTO** » a transformação  $\Phi \rightarrow G_\Phi$  é uma **redução polinomial**. Junto com  $\Phi \in 3\text{-SAT} \Leftrightarrow G_\Phi \in 3\text{-Edge-Coloring}$  e o pertencimento a NP, conclui-se que **3-Edge-Coloring de grafos cúbicos é NP-completo**.

{8}------------------------------------------------
### Exemplo: $\Phi = (x \vee \neg y \vee z)$
### FÓRMULA DE UMA ÚNICA CLÁUSULA

$$\Phi = (x \vee \neg y \vee z)$$
### CONSTRUÇÃO CONCEITUAL DE $G_\Phi$

Três gadgets de variável ( $x, y, z$ ), um inversor para  $y$  e um único gadget de cláusula  $C_1$ .

literal x (positivo)

literal z (positivo)

gadget de cláusula  $C_1$

inversor ( $\neg y$ )

$x$

$y$

$z$

$y$

$\neg y$

Diagrama conceitual da construção de G\_$\Phi$. Três gadgets de variável (x, y, z) e um inversor ($\neg$y) estão conectados a um único gadget de cláusula C1. O gadget x está conectado ao gadget C1 por uma aresta rotulada 'literal x (positivo)'. O gadget y está conectado ao inversor ($\neg$y) por uma aresta rotulada 'y'. O inversor ($\neg$y) está conectado ao gadget C1 por uma aresta rotulada '$\neg$y'. O gadget z está conectado ao gadget C1 por uma aresta rotulada 'literal z (positivo)'.

<!-- IMAGE_DESCRIPTION: datalab-dbe553cf16dd14073b89a8263a428664_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama conceitual da construção de G_Φ.
<!-- /IMAGE_DESCRIPTION -->
#### CASO A · ATRIBUIÇÃO SATISFAZ $\Phi$

$$x = F, \quad y = V, \quad z = V$$

$$\Rightarrow \text{literais: } x = F, \quad \neg y = F, \quad z = V$$

$$\Rightarrow (F \vee F \vee V) = V$$

O gadget de cláusula recebe ao menos uma entrada  $V \rightarrow G_\Phi$  é **3-edge-colorable**.
#### CASO B · ATRIBUIÇÃO FALHA

$$x = F, \quad y = V, \quad z = F$$

$$\Rightarrow \text{literais: } x = F, \quad \neg y = F, \quad z = F$$

$$\Rightarrow (F \vee F \vee F) = F$$

As três entradas são  $F \rightarrow$  pela construção, **o gadget de cláusula não admite 3-coloração própria**.

A satisfatibilidade de cada cláusula é traduzida diretamente em coloribilidade do gadget correspondente — esta é a alma da redução.

{9}------------------------------------------------

$$\Phi = (x \vee \neg y \vee z) \text{ com } x=V, y=F, z=V$$

ATRIBUIÇÃO:  $x=V, y=F, z=V$  LITERAIS:  $x=V, \neg y=V, z=V \rightarrow$  cláusula satisfeita ✓

literal  $x$  (positivo)

literal  $x$  (positivo)

$x=V$

**$x$**

PAR  $x$   
mesma cor = V ✓

literal  $y$  (negativo)

$y=F$

**$y$**

PAR  $y$   
cores diff. = F ✓

$y=F \rightarrow \neg y=V$

**inversor ( $\neg y$ )**

PAR  $\neg y$   
mesma cor = V ✓

literal  $z$  (positivo)

$z=V$

**$z$**

PAR  $z$   
mesma cor = V ✓

**gadget de cláusula  $C_1$**

3-EDGE-COLORABLE ✓

**LEGENDA**

- mesma cor → V
- cores diff. → F
- após inversor → V

Diagram illustrating the 3-edge-coloring of a clause gadget C1 for the formula $\Phi$ = (x $\lor$ $\neg$y $\lor$ z). The diagram shows three literals (x, y, z) connected to a clause gadget C1. Literal x is positive (x=V) and connects to a 'PAR x' box (mesma cor = V ✓). Literal y is negative (y=F) and connects to a 'PAR y' box (cores diff. = F ✓), which then connects to an 'inversor ($\neg$y)' box (y=F → $\neg$y=V), which connects to a 'PAR $\neg$y' box (mesma cor = V ✓). Literal z is positive (z=V) and connects to a 'PAR z' box (mesma cor = V ✓). All three 'PAR' boxes connect to the clause gadget C1 (3-EDGE-COLORABLE ✓). A legend explains the edge colors: red for 'mesma cor → V', blue for 'cores diff. → F', and yellow for 'após inversor → V'.

<!-- IMAGE_DESCRIPTION: datalab-b8661c6c54f72ecc7ff6cb05e47b2891_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram illustrating the 3-edge-coloring of a clause gadget C1 for the formula Φ = (x ∨ ¬y ∨ z).
<!-- /IMAGE_DESCRIPTION -->
## CONCLUSÃO

As 3 entradas chegam à cláusula como **V** (par de mesma cor em cada literal). Logo  $G_\Phi$  admite 3-edge-coloring  $\Rightarrow \Phi$  é satisfatível. ✓

{10}------------------------------------------------
## Síntese da prova
### ① PERTENCIMENTO A NP
### 3-Edge-Coloring $\in$ NP

A própria coloração é o certificado — verificável em **tempo linear**  $O(|V|)$  checando localmente as 3 arestas de cada vértice.
### ② CORREÇÃO DA REDUÇÃO
#### $\Phi$ satisfazível $\Leftrightarrow G_\Phi$ é 3-edge-colorable

( $\Rightarrow$ ) Atribuição satisfatória  $\rightarrow$  coloração válida de  $G_\Phi$ .

( $\Leftarrow$ ) Coloração válida  $\rightarrow$  atribuição extraída satisfaz  $\Phi$ .  
Construtiva nas duas direções.
### ③ REDUÇÃO POLINOMIAL $3\text{-SAT} \leq_P 3\text{-EDGE-COLORING}$

Pares de arestas codificam booleanos:

mesma cor  $\rightarrow V$  · cores diferentes  $\rightarrow F$

**Gadget de variável** — distribui um valor consistente a todas as ocorrências.

**Gadget inversor** — troca  $V \leftrightarrow F$  para literais negados.

**Gadget de cláusula** — 3-colorável sse ao menos uma entrada é  $V$  (simula OR).

**Fechamento cúbico** — duplicar  $H_\Phi$  fecha o grafo; construção é  $O(n+m)$ .

Portanto, **3-Edge-Coloring de grafos cúbicos é NP-completo.**

{11}------------------------------------------------
## Referências
### PUBLICAÇÃO ORIGINAL

**HOLYER, Ian.** *The NP-Completeness of Edge-Coloring.*

SIAM Journal on Computing, vol. 10, n. 4, pp. 718–720, 1981.

---

*Prova que determinar o índice cromático é NP-completo, e que o problema permanece NP-completo mesmo restrito a grafos cúbicos.*
## REFERÊNCIAS COMPLEMENTARES

**LEVEN, D.; GALIL, Z.** *NP Completeness of Finding the Chromatic Index of Regular Graphs.* Journal of Algorithms, 1983.

**KARP, R. M.** *Reducibility Among Combinatorial Problems.* Plenum Press, 1972.

**GAREY, M. R.; JOHNSON, D. S.** *Computers and Intractability.* W. H. Freeman, 1979.

**DOMINGUES, A. R. P.** *Enunciado do Trabalho 2 — Seminário de NP-Compleitude.* PUCRS, 2026.

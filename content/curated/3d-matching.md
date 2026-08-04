<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **A ideia do 3DM: casar trios perfeitos**
  - Uma analogia
- **Definição formal do 3DM**
  - Definição (3-Dimensional Matching)
  - 2 $3DM \in NP$ — certificado polinomial
- **3**
  - Problema-fonte: 3-SAT
  - Definição (3-SAT)
- **Visão geral da redução: três gadgets**
  - Gadget de Variável
  - Gadget de Cláusula
  - Gadget de Limpeza
  - Gadget de variável: o anel
  - Elementos e triplas (variável $x_i$ em $k$ cláusulas)
  - Gadgets de cláusula e de limpeza
- **6 Tempo polinomial da redução**
  - Exemplo: da fórmula ao matching
  - Instância 3DM construída
- **Flag icon Conclusão**
- **Referências**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

Teoria da Computabilidade e Complexidade

# 3-Dimensional Matching é NP-Completo

*Prova por redução polinomial a partir do 3-SAT*

---

Seminário T2 · Caetano Marasca, Gabriel Quintana e Gustavo Melleu

An abstract geometric logo located in the bottom right corner. It features three dark teal squares. One square is at the top left, another at the top right, and a third at the bottom center. They are connected by thin, dark teal lines: a horizontal line between the top two squares, and a line that descends from the bottom-left corner of the top-left square, connects to the top-left corner of the bottom-center square, and then continues horizontally to the top-right corner of the bottom-center square.

Abstract geometric logo consisting of three squares and connecting lines.

{1}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-5fb340ad68b0c71df0b56698b137e35b_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Abstract geometric logo consisting of three squares and connecting lines.
<!-- /IMAGE_DESCRIPTION -->
## A ideia do 3DM: casar trios perfeitos
### Uma analogia

Imagine 3 grupos do mesmo tamanho: **médicos (X)**, **enfermeiros (Y)** e **hospitais (Z)**.

Uma lista diz quais trios (médico, enfermeiro, hospital) podem trabalhar juntos.

**Pergunta:** dá para escalar trios de modo que cada pessoa e cada hospital seja usado **exatamente uma vez**?

The diagram shows three columns of circles representing the groups X (médicos), Y (enfermeiros), and Z (hospitais). Each column contains three circles labeled x1, x2, x3; y1, y2, y3; and z1, z2, z3 respectively. Three horizontal green lines connect the circles in a one-to-one fashion: x1 to y1 to z1, x2 to y2 to z2, and x3 to y3 to z3. This represents a perfect matching where every individual in group X is paired with exactly one individual in group Y, who is then paired with exactly one hospital in group Z.

Diagram illustrating a perfect matching between three groups: X (médicos), Y (enfermeiros), and Z (hospitais). Three horizontal lines connect x1 to y1 to z1, x2 to y2 to z2, and x3 to y3 to z3, representing a perfect matching.

*As linhas verdes mostram um "matching perfeito": ninguém de fora, ninguém repetido.*

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-895d588a848d9963890c938763de9ecf_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram illustrating a perfect matching between three groups: X (médicos), Y (enfermeiros), and Z (hospitais).
<!-- /IMAGE_DESCRIPTION -->
## Definição formal do 3DM
### Definição (3-Dimensional Matching)

Dados três conjuntos disjuntos  $X, Y, Z$  com  $|X| = |Y| = |Z| = q$  e um conjunto de triplas  $T \subseteq X \times Y \times Z$ : existe um matching perfeito  $M \subseteq T$  com  $|M| = q$  tal que todo elemento de  $X \cup Y \cup Z$  apareça em exatamente uma tripla?
#### ✓ Instância satisfável

$X = \{x_1, x_2\}$     $Y = \{y_1, y_2\}$     $Z = \{z_1, z_2\}$

$T = \{(x_1, y_1, z_1), (x_2, y_2, z_2), (x_1, y_2, z_1)\}$

$M = \{(x_1, y_1, z_1), (x_2, y_2, z_2)\}$  ← matching perfeito
#### ✗ Instância insatisfável

$X = \{x_1, x_2\}$     $Y = \{y_1, y_2\}$     $Z = \{z_1, z_2\}$

$T = \{(x_1, y_1, z_1), (x_1, y_2, z_2)\}$

$x_2$  nunca aparece em  $T$

→ nenhum  $M$  cobre  $X$

A versão de decisão (sim/não) é o que interessa para falar de NP-completude.

{3}------------------------------------------------
### 2 $3DM \in NP$ — certificado polinomial

**Estratégia:** exibir um verificador determinístico de tempo polinomial. Certificado:  $M \subseteq T$  com  $|M| = q$  triplas.

1 Verificar  $|M| = q$

$O(q)$

2 Verificar que toda tripla de  $M$  pertence a  $T$

$O(q \cdot |T|)$

3 Nenhum elemento de  $X$  se repete em  $M$

$O(q^2)$

4 Nenhum elemento de  $Y$  se repete em  $M$

$O(q^2)$

5 Nenhum elemento de  $Z$  se repete em  $M$

$O(q^2)$

**Complexidade total:  $O(q^2) \rightarrow$  polinomial  $\Rightarrow 3DM \in NP \checkmark$**

{4}------------------------------------------------
## 3
### Problema-fonte: 3-SAT
### Definição (3-SAT)

Dada uma fórmula booleana em FNC com  $m$  cláusulas e  $n$  variáveis, cada cláusula com exatamente 3 literais, existe uma atribuição que a satisfaça (toda cláusula com ao menos 1 literal verdadeiro)?

Exemplo

$$\phi = (x_1 \vee \neg x_2 \vee x_3) \wedge (\neg x_1 \vee x_2 \vee \neg x_3) \wedge (x_2 \vee x_3 \vee \neg x_4)$$

Satisfeita por:  $x_1=V, x_2=V, x_3=F, x_4=F$

Lightbulb icon indicating a key insight or definition.

**3-SAT é NP-completo (Cook, 1971)**  $\rightarrow$  é o nosso ponto de partida. Mostraremos  $3\text{-SAT} \leq_p 3\text{DM}$ : se soubéssemos resolver 3DM, resolveríamos 3-SAT. Como a redução preserva a resposta nos dois sentidos ( $\Leftrightarrow$ ), a prova de correção terá duas direções.

{5}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-764bb8d7c93b090e205d908e1a8cade4_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Lightbulb icon indicating a key insight or definition.
<!-- /IMAGE_DESCRIPTION -->
## Visão geral da redução: três gadgets

Dada  $\varphi$  do 3-SAT, construímos  $\langle X, Y, Z, T \rangle$  do 3DM em tempo polinomial.

Icon of a toggle switch, representing the Variable gadget.

<!-- IMAGE_DESCRIPTION: datalab-0e62b4ac2303ba5f3ff10123a7c0f273_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Icon of a toggle switch, representing the Variable gadget.
<!-- /IMAGE_DESCRIPTION -->
### Gadget de Variável

Para cada variável, um anel de triplas força a escolha V ou F (atribuição consistente).

Icon of a puzzle piece, representing the Clause gadget.

<!-- IMAGE_DESCRIPTION: datalab-35afbfc3c4a5c0fe01e91ba536605e09_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Icon of a puzzle piece, representing the Clause gadget.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-32a03202e95ff09a974e12e4be687885_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Puzzle piece icon representing a clause gadget.
<!-- /IMAGE_DESCRIPTION -->
### Gadget de Cláusula

Para cada cláusula, um elemento que só é coberto se ao menos um literal for verdadeiro.

Icon of a trash can, representing the Cleanup gadget.

<!-- IMAGE_DESCRIPTION: datalab-130ce5fbe21d11939cd4419d3e7ff044_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Icon of a trash can, representing the Cleanup gadget.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-f01b22e5bb303653828200595aece414_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Trash can icon representing a cleanup gadget.
<!-- /IMAGE_DESCRIPTION -->
### Gadget de Limpeza

Triplas coringa coletam os elementos de literal que sobraram, fechando o matching.

$\varphi \xrightarrow{\text{(construção polinomial)}} \langle X, Y, Z, T \rangle \quad \varphi \text{ satisfatível} \Leftrightarrow \langle X, Y, Z, T \rangle \text{ tem matching perfeito}$

{6}------------------------------------------------
#### 4
### Gadget de variável: o anel

The diagram shows a central structure with four internal nodes labeled  $a_{11}, a_{12}, a_{13}, a_{14}$  and four external nodes labeled  $b_{11}, b_{12}, b_{13}, b_{14}$ . These are connected by four triangles labeled  $t_{11}, t_{12}, t_{13}, t_{14}$ . The internal nodes are arranged in a cycle, and the external nodes are arranged in a cycle. The triangles connect the internal nodes to the external nodes in a specific pattern.

Diagram of a variable gadget (the ring) showing four internal nodes (a11, a12, a13, a14) and four external nodes (b11, b12, b13, b14) connected by four triangles (t11, t12, t13, t14).

Two diagrams showing the variable gadget with different internal nodes highlighted in green and orange, representing different truth assignments. The left diagram shows the internal nodes  $a_{11}, a_{12}, a_{13}, a_{14}$  highlighted in green, while the right diagram shows them highlighted in orange. The external nodes  $b_{11}, b_{12}, b_{13}, b_{14}$  and the triangles  $t_{11}, t_{12}, t_{13}, t_{14}$  are shown in gray.

Two diagrams showing the variable gadget with different internal nodes highlighted in green and orange, representing different truth assignments.

<!-- IMAGE_DESCRIPTION: datalab-a738993919a50143787084ee7ce6e2f2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a variable gadget (the ring) showing four internal nodes (a11, a12, a13, a14) and four external nodes (b11, b12, b13, b14) connected by four triangles (t11, t12, t13, t14).
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-997233d405f0d4b89ddeb7683e047f66_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Two diagrams showing the variable gadget with different internal nodes highlighted in green and orange, representing different truth assignments.
<!-- /IMAGE_DESCRIPTION -->
### Elementos e triplas (variável $x_i$ em $k$ cláusulas)

Núcleo  $a_{i1} \dots a_{i,2k}$  e pontas  $b_{i1} \dots b_{i,2k}$  (internos)

Triplas:  $t_{ij} = (a_{ij}, a_{i,j+1}, b_{ij})$

- índice  $j$  ímpar  $\rightarrow$  grupo "Verdadeiro"
- índice  $j$  par  $\rightarrow$  grupo "Falso"
#### Propriedade-chave

Os nós internos (cinza) só existem aqui  $\rightarrow$  precisam ser cobertos dentro do anel. As triplas se alternam: só dá para cobrir todos escolhendo **todas as verdes** ( $x_i = V$ ) ou **todas as laranjas** ( $x_i = F$ ). Os literais que sobram livres vão para as cláusulas.

Fonte: adaptado de captura de tela do vídeo "Proving that 3DM is np (animated)", YouTube, aos 3:42, disponível em:  
<https://www.youtube.com/watch?v=TtuNf6XMhiw>.

{7}------------------------------------------------
### Gadgets de cláusula e de limpeza

Puzzle piece icon representing a clause gadget.
#### Cláusula: teste de satisfação

The diagram shows a central node labeled 's' inside a dark grey circle. Three lines radiate from this node to three rectangular boxes on the right. The top two boxes are green and contain the text  $(s, p^1, x_1)$  and  $(s, p^2, x_2)$  respectively. The bottom box is red and contains the text  $(s, p^3, \neg x_3)$ . The line connecting 's' to the red box is also red, while the others are green.

Diagram of a clause gadget. A central node 's' is connected to three triplets: (s, p^1, x\_1), (s, p^2, x\_2), and (s, p^3, $\neg$x\_3). The first two connections are green, and the third is red.

Elemento  $s_j$  e 3 triplas, uma por literal. Cobrir  $s_j$  exige UMA tripla, e só serve a de um literal **livre (verdadeiro)**.

$\Rightarrow$  *cláusula fecha*  $\Leftrightarrow$  *tem literal verdadeiro*.

Trash can icon representing a cleanup gadget.

<!-- IMAGE_DESCRIPTION: datalab-35a7554182eb055209552843f341a1ae_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a clause gadget. A central node 's' is connected to three triplets: (s, p^1, x_1), (s, p^2, x_2), and (s, p^3, ¬x_3). The first two connections are green, and the third is red.
<!-- /IMAGE_DESCRIPTION -->
#### Limpeza: coletar as sobras

**Problema:** os anéis produzem mais elementos de literal do que as cláusulas consomem. As sobras precisam ser cobertas, senão não há matching perfeito.

**Solução:** pares coringa (g) com triplas (**g, literal livre**) que se ligam a qualquer literal restante.

**Nº de triplas de limpeza = nº de sobras**  $\rightarrow$  absorve tudo exatamente uma vez.

{8}------------------------------------------------
#### 5 Correção (ida): $\varphi$ satisfatível $\Rightarrow$ há matching

**Hipótese:** existe atribuição  $\alpha$  que satisfaz  $\varphi$ . Construimos o matching  $M$  a partir dela.
#### 1 Gadgets de variável

Para cada  $x_i$ , escolher o lado  $V$  (se  $\alpha(x_i)=V$ ) ou  $F$  (caso contrário). Isso cobre todos os elementos internos  $a$  e  $b$  do anel.
##### 2 Gadgets de cláusula

Cada  $C_j$  tem um literal verdadeiro; seu elemento ficou livre no passo 1. Escolher a tripla  $(s_j, \cdot, \text{literal})$  que o usa — cobre  $s_j$ .
##### 3 Gadgets de limpeza

Os elementos de literal restantes são cobertos pelas triplas coringa, cada um exatamente uma vez.

**Conclusão:**  $M$  cobre  $X \cup Y \cup Z$  sem repetição  $\rightarrow$  é um matching perfeito. ■

{9}------------------------------------------------
##### 5 Correção (volta): há matching $\Rightarrow \varphi$ satisfatível

**Hipótese:** existe matching perfeito  $M$ . Extraímos uma atribuição  $\alpha$  a partir dele.
#### 1 Extrair a atribuição

1 Cobrir os nós internos a obriga cada **anel** a escolher um único lado. Se foi o lado  $V$ , **definir**  $\alpha(x_i)=V$ ; senão  $\alpha(x_i)=F$ . Atribuição consistente, sem ambiguidade.
#### 2 Verificar as cláusulas

2 Cada  $s_j$  foi coberto por uma tripla  $(s_j, \cdot, \text{literal})$ . Esse literal só estava livre se for verdadeiro segundo  $\alpha$  — logo  $C_j$  está satisfeita.
#### 3 Conclusão

3 Como todo  $s_j$  é coberto, toda cláusula tem um literal verdadeiro. Portanto  $\alpha$  satisfaz  $\varphi$ .

**Conclusão:**  $\alpha$  é atribuição satisfatória  $\rightarrow$  matching perfeito  $\Rightarrow \varphi$  satisfatível. ■

{10}------------------------------------------------
## 6 Tempo polinomial da redução

O tamanho da instância 3DM é polinomial em  $|\varphi|$  (n variáveis, m cláusulas).

| Componente                              | Quantidade               | Ordem   |
|-----------------------------------------|--------------------------|---------|
| Elementos de variável (núcleo + pontas) | $\leq 2 \cdot n \cdot k$ | $O(nm)$ |
| Elementos de cláusula                   | m + posições             | $O(m)$  |
| Elementos de limpeza                    | sobras $\leq nm$         | $O(nm)$ |
| Triplas de variável                     | $2 \cdot n \cdot k$      | $O(nm)$ |
| Triplas de cláusula                     | 3m                       | $O(m)$  |
| Triplas de limpeza                      | = nº de sobras           | $O(nm)$ |

Total  $|X|,|Y|,|Z|,|T| = O(nm) \rightarrow$  a redução é computada em tempo polinomial ✓

{11}------------------------------------------------
### Exemplo: da fórmula ao matching

$$C = (x_1 \vee x_2 \vee \neg x_3)$$

1 cláusula, 3 variáveis

reduz
### Instância 3DM construída

Anéis (1 por variável):

- $x_1$  escolhe lado V  $\rightarrow$  deixa  $t_1$  livre
- $x_2$  escolhe lado V  $\rightarrow$  deixa  $t_2$  livre
- $x_3$  escolhe lado F  $\rightarrow$  deixa  $f_3$  livre

Cláusula:

- tripla  $(s, p^3, f_3)$  cobre  $s$  — literal  $\neg x_3$  verdadeiro

Limpeza:

- coringas absorvem  $t_1, t_2$  e os demais resíduos

1 Uma cláusula ( $m=1$ ); cada variável ocorre 1 vez  $\rightarrow$  anéis mínimos.

2 A atribuição  $x_1=V, x_3=F$  satisfaz  $C$ ; os anéis fixam esses lados.

3 A cláusula fecha pela tripla do literal  $\neg x_3$ , que ficou livre.

4 A limpeza absorve os literais restantes  $\rightarrow$  matching perfeito  $\checkmark$

{12}------------------------------------------------
## Flag icon Conclusão

**3DM  $\in$  NP**

Certificado M verificável em  $O(q^2)$ .

**3DM é NP-difícil**

3-SAT  $\leq_p$  3DM via redução  $O(nm)$ , com a redução correta nas duas direções.

**$\therefore$  3DM é NP-completo**

$NP \cap NP\text{-difícil} = NP\text{-completo}$ .
## Referências

**Garey & Johnson (1979)**

Computers and Intractability. Problema [SP1], p. 50 — a redução 3-SAT  $\rightarrow$  3DM (referência principal da prova).

**Karp (1972)**

Reducibility Among Combinatorial Problems — estabelece o 3DM como NP-completo (referência histórica).

**Cook (1971)**

The Complexity of Theorem-Proving Procedures — NP-completude de SAT, base da cadeia.

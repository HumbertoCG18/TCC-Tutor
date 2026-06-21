<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Problemas Clássicos em P: Grafos**
  - Mensagem
  - Exemplo Detalhado: PATH
  - BFS
  - Instância
  - Ideia do algoritmo
  - Critério
  - Pergunta
  - Moral
- **Propriedades Estruturais de P**
  - Fechamento
  - Robustez
  - Ponte para a próxima seção
  - NP não significa “não polinomial”
  - Cuidado com a sigla
  - Intuição
- **Definição Formal da Classe NP**
  - Definição por Não-Determinismo
  - Definição por Verificadores
  - Determinismo versus Não-Determinismo
  - P
  - NP
  - Leitura correta
  - Equivalência entre Não-Determinismo e Verificação
  - Leitura conceitual
  - Importante
- **Problemas Clássicos em NP**
  - Padrão comum
  - Exemplo Detalhado: SAT
  - Conclusão
  - Dois Exemplos de Certificados em NP
  - CLIQUE
- **SUBSET-SUM**
  - Mensagem
- **NP afirma**
- **NP não afirma**
- **Exemplo**
- **coNP, $NP \cap coNP$ e Exemplos Relevantes**
- **Definição**
- **Aberto**
- **Ponte conceitual para P versus NP**
- **Resumo até aqui**
- **A pergunta natural**
- **Relações Conhecidas entre P, NP e coNP**
  - Inclusões Provadas
- **Se $P = NP$ : Consequências**
  - Teóricas
  - Práticas
  - Impacto imediato
- **Se $P \neq NP$**
  - Contrastes clássicos
  - Mensagem
- **O que sabemos, o que suspeitamos, o que não provamos**
- **Ponto pedagógico**
  - Por que é tão difícil provar?
- **Conclusão**
- **Problemas NP-Intermediários**
- **Teorema de Ladner**
  - Leitura
  - Por que essa pergunta importa tanto?
- **Síntese**
- **Exercício 1: Verdadeiro ou Falso?**
  - Gabarito comentado
  - Exercício 2: Classificação de Problemas
  - Exercício 3: Projetando Verificadores
  - Comentários
  - Discussão
  - Exercício 4: Provas de pertinência em P
  - Comentários
  - Exercício 5: Relações entre as classes
  - Comentários
  - Exercício 6: Consequências estruturais
  - Comentários
  - Exercício 7: Verificar versus encontrar
  - Comentários
  - Discussão
  - Exercício 8: Contrastando problemas
  - Comentários
- **Comentários**
- **Leituras Sugeridas**
- **Livros**
- **Artigos clássicos**
  - Glossário: PATH
  - Glossário: 2-COLORING
  - Glossário: SHORTEST-PATH-LEQ
  - Glossário: MAX-FLOW-GEQ
  - Glossário: BIP-MATCHING-GEQ
  - Glossário: RELPRIME
  - Glossário: 2-SAT
  - Glossário: PRIMES
  - Glossário: LP-FEASIBILITY
  - Glossário: DFA-EMPTINESS
  - Glossário: DFA-EQUIVALENCE
  - Glossário: SAT
  - Glossário: 3-SAT
  - Glossário: CLIQUE
  - Glossário: INDEP-SET
  - Glossário: VERTEX-COVER
  - Glossário: HAMPATH
- **Glossário: HAMCYCLE**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: 3-COLORING**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: SUBSET-SUM**
- **Glossário: PARTITION**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: KNAPSACK**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: TSP-LEQ**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: SET-COVER**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: INTEGER-PROG**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: UNSAT**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: TAUTOLOGY**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: FACTOR**
  - Descrição em alto nível
  - Instância resolvida
- **Glossário: GRAPH-ISOMORPHISM**
  - Descrição em alto nível
  - Instância resolvida
- **Referências I**
- **Referências II**
- **Referências III**
- **Referências IV**
- **Referências V**
- **Referências VI**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
<!-- DATALAB_CHUNK 1: pages 1-20 -->

{0}------------------------------------------------

# Complexidade de Tempo: Classes P e NP

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 17

Teoria da Computabilidade e Complexidade  
Ciência da Computação

22 de maio de 2026

Logo of PUCRS (Universidade Federal do Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

{1}------------------------------------------------
## Sumário

- 1 A Classe P
- 2 A Classe NP
- 3 A Questão P vs NP
- 4 Exercícios
- 5 Glossário de Problemas

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central vertical band containing a stylized 'M' and stars, flanked by two vertical bands with a cross pattern. A large star is at the bottom of the shield. Above the shield is a crown, and on either side are crossed keys. A banner at the bottom reads 'AD VERVM DVCIT'.

Coat of arms of the University of São Paulo (USP)

{2}------------------------------------------------

{3}------------------------------------------------

A Classe P A Classe NP A Questão P vs NP Exercícios Glossário de Problemas Referências  
● ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○

# Definição Formal da Classe P

Definição

$$P = \bigcup_{k \ge 0} \text{DTIME}(n^k)$$

Uma linguagem  $L$  pertence a P se existe uma máquina de Turing determinística  $M$  e um polinômio  $p$  tais que  $M$  decide  $L$  em no máximo  $p(|w|)$  passos para toda entrada  $w$ .

Leitura conceitual

P reúne problemas para os quais conhecemos um algoritmo geral cujo tempo cresce como  $n, n^2, n^3, \dots$ , e não como  $2^n, n!$ , etc.

[20, 14, 3]

Prof. Anderson R. P. Domingues

Classes P e NP 4 / 78

{4}------------------------------------------------

{5}------------------------------------------------

{6}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-b6cb8677b4ffb35c6468fa5c24091bff_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->
## Problemas Clássicos em P: Grafos

| Problema          | Pergunta                      | Ferramenta            | Tempo          |
|-------------------|-------------------------------|-----------------------|----------------|
| PATH              | Existe caminho de $s$ a $t$ ? | BFS/DFS               | $O( V  +  E )$ |
| CONNECTED         | O grafo é conexo?             | BFS/DFS               | $O( V  +  E )$ |
| 2-COLORING        | O grafo é bipartido?          | BFS por níveis        | $O( V  +  E )$ |
| SHORTEST-PATH-LEQ | Caminho com custo $\leq B$ ?  | Dijkstra/Bellman–Ford | polinomial     |
| MAX-FLOW-GEQ      | Fluxo máximo $\geq B$ ?       | Edmonds–Karp          | polinomial     |
| BIP-MATCHING-GEQ  | Matching $\geq k$ ?           | Hopcroft–Karp         | polinomial     |
### Mensagem

P já contém problemas de conectividade, otimização em grafos, fluxo e emparelhamento: eficiência não significa simplicidade conceitual.

[20, 11, 13]

{7}------------------------------------------------

A Classe P A Classe NP A Questão P vs NP Exercícios Glossário de Problemas Referências  

# Problemas Clássicos em P: Lógica, Aritmética e Autômatos

| Problema        | Pergunta                               | Ferramenta         | Status |
|-----------------|----------------------------------------|--------------------|--------|
| RELPRIME        | $gcd(a, b) = 1?$                       | Euclides           | em P   |
| 2-SAT           | Fórmula $2\text{-CNF}$ é satisfatível? | CFCs               | em P   |
| PRIMES          | $n$ é primo?                           | AKS                | em P   |
| LP-FEASIBILITY  | Sistema linear viável?                 | Elipsoide/interior | em P   |
| DFA-EMPTINESS   | AFD aceita alguma palavra?             | Busca no grafo     | em P   |
| DFA-EQUIVALENCE | Dois AFDs são equivalentes?            | Produto + busca    | em P   |

**Observação pedagógica**

Estar em P não depende do "tema" do problema. Há problemas de lógica em P e problemas de grafos fora de P, dependendo da estrutura combinatória envolvida.

[14, 4, 16, 2]

|                                |                |        |
|--------------------------------|----------------|--------|
| Prof. Anderson R. P. Domingues | Classes P e NP | 8 / 78 |
|--------------------------------|----------------|--------|

{8}------------------------------------------------
### Exemplo Detalhado: PATH

```

graph LR
    s((s)) --- a((a))
    s --- b((b))
    a --- c((c))
    b --- c
    c --- t((t))
    style s fill:none,stroke:none
    style a fill:none,stroke:none
    style b fill:none,stroke:none
    style c fill:none,stroke:none
    style t fill:none,stroke:none
  
```

A graph with five vertices labeled s, a, b, c, and t. Vertex s is on the left, and vertex t is on the right. Vertices a and b are positioned above and below the edge between s and c, respectively. There are edges (s, a), (s, b), (a, c), (b, c), and (c, t). The edges (s, a), (a, c), and (c, t) are highlighted in red, representing a path from s to t.

<!-- IMAGE_DESCRIPTION: datalab-2ba086df3506f81bae3a9b53725dcfea_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A graph with five vertices labeled s, a, b, c, and t.
<!-- /IMAGE_DESCRIPTION -->
#### Instância

$$E = \{(s, a), (s, b), (a, c), (b, c), (c, t)\}$$
### BFS

- 1 começa em  $s$ ;
- 2 visita  $a$  e  $b$ ;
- 3 alcança  $c$ ;
- 4 alcança  $t$ .

**Resposta:** SIM, com caminho

$$s \rightarrow a \rightarrow c \rightarrow t.$$

**Complexidade:** cada vértice entra na fila no máximo uma vez e cada aresta é examinada um número constante de vezes; logo, o custo é  $O(|V| + |E|)$ .

{9}------------------------------------------------

A Classe P A Classe NP A Questão P vs NP Exercícios Glossário de Problemas Referências  
 ○ ○ ○ ○ ○ ○ ○ ● ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○ ○

# Exemplo Detalhado: 2-SAT
### Instância

$$\varphi = (x_1 \lor x_2) \land (\neg x_1 \lor x_3) \land (\neg x_2 \lor \neg x_3)$$
### Ideia do algoritmo

- cada cláusula  $(a \lor b)$  gera as implicações  $\neg a \Rightarrow b$  e  $\neg b \Rightarrow a$ ;
- constrói-se o grafo de implicação sobre  $x_i$  e  $\neg x_i$ ;
- calculam-se as componentes fortemente conexas.
### Critério

$\varphi$  é satisfatível  $\iff \forall i, x_i$  e  $\neg x_i$  não estão na mesma CFC.

Lição

Uma pequena mudança estrutural no enunciado pode mudar drasticamente a complexidade: 2-SAT está em P, enquanto 3-SAT é NP-complete.

◁ $\square$ ▷ ⊲ ⊳ ⊴ ⊵ [\[4, 18\]](#) ⟲ ⟳ ⟴

|                                |                |         |
|--------------------------------|----------------|---------|
| Prof. Anderson R. P. Domingues | Classes P e NP | 10 / 78 |
|--------------------------------|----------------|---------|

{10}------------------------------------------------
#### Exemplo Histórico: PRIMES
### Pergunta

Dado um inteiro  $n$  em binário, decidir se  $n$  é primo.

- por muito tempo conheciam-se apenas testes probabilísticos muito rápidos;
- Agrawal, Kayal e Saxena mostraram que  $\text{PRIMES} \in P$ ;
- o resultado ilustra que intuição informal de dificuldade nem sempre coincide com a classificação assintótica.
### Moral

Nem todo problema aritmético “sofisticado” está fora de  $P$ ;  
descobrir um algoritmo polinomial pode exigir uma ideia estrutural profunda.

{11}------------------------------------------------
## Propriedades Estruturais de P
### Fechamento

Se  $L, L_1, L_2 \in P$ , então também pertencem a P:

$$\bar{L}, \quad L_1 \cup L_2, \quad L_1 \cap L_2.$$
### Robustez

Máquinas multi-fita, RAMs e outros modelos razoáveis se simulam com overhead no máximo polinomial. Assim, “estar em P” é uma propriedade estável do problema, e não um artefato do modelo.
### Ponte para a próxima seção

P captura problemas que **resolvemos** eficientemente. Em seguida veremos NP, a classe dos problemas cujas respostas positivas sabemos **verificar** eficientemente.

{12}------------------------------------------------
### NP não significa “não polinomial”
### Cuidado com a sigla

NP significa **nondeterministic polynomial time**, e não “non-polynomial”.

- P e NP são classes de problemas decidíveis em tempo polinomial;
- a diferença está no modelo: determinístico em P, não-determinístico em NP;
- equivalentemente, NP é a classe dos problemas com **certificados curtos verificáveis em tempo polinomial**.
### Intuição

Em NP, encontrar uma solução pode ser difícil; conferir uma solução candidata pode ser fácil.

{13}------------------------------------------------
## Definição Formal da Classe NP
### Definição por Não-Determinismo

$$NP = \bigcup_{k \geq 0} NTIME(n^k)$$

NP é a classe das linguagens decididas por máquinas de Turing não-determinísticas em tempo polinomial.
### Definição por Verificadores

$L \in NP$  se existe um verificador polinomial  $V$  e um polinômio  $p$  tais que

$$w \in L \iff \exists c, |c| \leq p(|w|) \wedge V(w, c) = 1.$$

{14}------------------------------------------------
### Determinismo versus Não-Determinismo
### P

- algoritmo segue um único caminho;
- para cada entrada, computa a resposta diretamente;
- foco: **resolver**.
### NP

- máquina pode “adivinhar” um certificado;
- depois verifica essa adivinhação em tempo polinomial;
- foco: **verificar**.
### Leitura correta

O não-determinismo não é um recurso físico disponível na prática; ele serve como modelo matemático para formalizar a ideia de certificado verificável.

{15}------------------------------------------------
### Equivalência entre Não-Determinismo e Verificação
#### Teorema

As duas definições anteriores de NP são equivalentes.
#### Ideia da equivalência

- se uma MT não-determinística aceita em tempo polinomial, a sequência de escolhas não-determinísticas funciona como certificado;
- se existe verificador polinomial, uma MT não-determinística pode “adivinhar” o certificado e executá-lo.
### Leitura conceitual

NP é a classe dos problemas cujas instâncias positivas possuem **provas curtas e verificáveis eficientemente**.

{16}------------------------------------------------
#### Como é um verificador polinomial?
#### Formato geral

Entrada: instância  $w$  e certificado  $c$ .

- 1 verificar se  $c$  tem tamanho polinomial em  $|w|$ ;
- 2 checar localmente as condições que tornam  $c$  uma solução válida;
- 3 aceitar se todas as checagens passarem.
### Importante

Em NP, precisamos apenas de certificados para instâncias **SIM**. Não é exigido que instâncias **NÃO** tenham certificados curtos.

{17}------------------------------------------------
## Problemas Clássicos em NP

| Problema     | Pergunta                  | Certificado           | Classe      |
|--------------|---------------------------|-----------------------|-------------|
| SAT          | fórmula satisfatível?     | atribuição booleana   | NP-complete |
| CLIQUE       | clique de tamanho $k$ ?   | conjunto de vértices  | NP-complete |
| VERTEX-COVER | cobertura $\leq k$ ?      | conjunto de vértices  | NP-complete |
| HAMPATH      | caminho Hamiltoniano?     | sequência de vértices | NP-complete |
| SUBSET-SUM   | subconjunto soma $t$ ?    | subconjunto escolhido | NP-complete |
| TSP-LEQ      | tour com custo $\leq B$ ? | ordem das cidades     | NP-complete |
### Padrão comum

Em todos esses casos, alguém pode lhe entregar uma solução candidata e você consegue conferi-la em tempo polinomial.

{18}------------------------------------------------
### Exemplo Detalhado: SAT
#### Instância

$$\phi = (x_1 \vee \neg x_2 \vee x_3) \wedge (\neg x_1 \vee x_2) \wedge (x_2 \vee x_3)$$
#### Certificado

$$x_1 = 1, \quad x_2 = 1, \quad x_3 = 0$$
#### Verificação

- percorre-se a lista de cláusulas;
- cada cláusula é testada sob a atribuição dada;
- o custo é linear no tamanho da fórmula.
### Conclusão

Logo,  $\text{SAT} \in \text{NP}$ . Mais adiante veremos que ele é NP-complete.

[9, 20]

{19}------------------------------------------------
### Dois Exemplos de Certificados em NP
### CLIQUE

Entrada: grafo  $G$  e inteiro  $k$ .

Certificado: conjunto  $C$  com

$|C| = k$ .

Verificação:

- checar se  $|C| = k$ ;
- para todo par  $u, v \in C$ , testar se  $\{u, v\} \in E$ .

Custo:  $O(k^2)$  testes de adjacência.
## SUBSET-SUM

Entrada:  $S = \{3, 5, 6, 9, 11\}$  e  $t = 20$ .

Certificado:  $S' = \{3, 6, 11\}$ .

Verificação:

$$3 + 6 + 11 = 20$$

Custo: polinomial no tamanho da instância.
### Mensagem

O certificado não precisa explicar *como* foi encontrado; basta permitir verificação rápida.

[15, 18]

<!-- DATALAB_CHUNK 2: pages 21-40 -->

{20}------------------------------------------------

# O que NP afirma — e o que NP não afirma
## NP afirma

Há verificação eficiente para instâncias positivas.
## NP não afirma

- que sabemos encontrar a solução eficientemente;
- que a solução é única;
- que instâncias negativas tenham certificados curtos;
- que o problema seja “difícil na prática”.
## Exemplo

PRIMES está em P e, portanto, em NP. Logo, estar em NP não é sinônimo de ser difícil.

{21}------------------------------------------------
## coNP, $NP \cap coNP$ e Exemplos Relevantes
## Definição

$$coNP = \{L \mid \bar{L} \in NP\}$$

- UNSAT e TAUTOLOGY são problemas típicos de coNP;
- PRIMES está em P, portanto também em  $NP \cap coNP$ ;
- FACTOR e GRAPH-ISOMORPHISM são candidatos clássicos a problemas em NP que não parecem NP-complete.
## Aberto

Não sabemos se  $NP = coNP$ , nem se  $P = NP \cap coNP$ .

[20, 3, 5]

{22}------------------------------------------------
## Ponte conceitual para P versus NP
## Resumo até aqui

- $P =$  problemas que sabemos resolver eficientemente;
- $NP =$  problemas cujas respostas SIM sabemos verificar eficientemente;
- $P \subseteq NP$ .
## A pergunta natural

Toda solução verificável eficientemente também pode ser **encontrada** eficientemente?

$$P \stackrel{?}{=} NP$$

{23}------------------------------------------------
## Relações Conhecidas entre P, NP e coNP
### Inclusões Provadas

$$P \subseteq NP, \quad P \subseteq \text{coNP}, \quad P \subseteq NP \cap \text{coNP}.$$

A Venn diagram illustrating the relationships between complexity classes. It features two large overlapping ellipses: a light blue one on the left labeled 'NP' and a light red one on the right labeled 'coNP'. Inside the intersection of these two ellipses is a smaller green circle labeled 'P'. The region of the blue ellipse not overlapping with the red one is labeled 'SAT'. The region of the red ellipse not overlapping with the blue one is labeled 'UNSAT'. The label 'PATH' is placed just below the 'P' label within the green circle. In the background, a faint watermark of the University of Vienna seal is visible.

Venn diagram illustrating the relationships between complexity classes P, NP, and coNP.

**Ainda aberto:**  $P = NP?$ ,  $NP = \text{coNP}?$ ,  $P = NP \cap \text{coNP}?$

[20, 18]

{24}------------------------------------------------

A Classe P  A Classe NP  A Questão P vs NP  Exercícios  Glossário de Problemas  Referências

# Três leituras da pergunta P vs NP

**Leitura algorítmica**

Todo problema com verificação polinomial admite também algoritmo polinomial?

**Leitura estrutural**

Resolver é tão fácil quanto verificar?

**Leitura epistemológica**

Toda prova curta e verificável pode ser encontrada eficientemente?

**Importância**

A pergunta conecta algoritmos, lógica, otimização, criptografia e teoria da prova.

Prof. Anderson R. P. Domingues
Classes P e NP
25 / 78

{25}------------------------------------------------

{26}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-9167fa5ebcb66516d1bbb421ec9bba7b_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Venn diagram illustrating the relationships between complexity classes P, NP, and coNP.
<!-- /IMAGE_DESCRIPTION -->
## Se $P = NP$ : Consequências
### Teóricas

- todo problema NP-complete admitiria algoritmo polinomial;
- decisão, busca e otimização colapsariam em muitas famílias;
- NP-completude deixaria de ser evidência de intratabilidade.
### Práticas

- planejamento e otimização exata mudariam muito;
- várias premissas criptográficas perderiam força;
- ainda assim, o polinômio poderia ser impraticável.
### Impacto imediato

Mostrar SAT em P implicaria, via reduções, que 3-SAT, CLIQUE, VERTEX-COVER, SUBSET-SUM e muitos outros também estão em P.

[9, 15, 3]

{27}------------------------------------------------
## Se $P \neq NP$

- existirão problemas com certificados curtos e verificáveis, mas sem algoritmo polinomial geral;
- NP-completude se consolida como evidência formal de intratabilidade;
- aproximação, parametrização, aleatorização e heurísticas tornam-se respostas naturais.
### Contrastes clássicos

2-SAT está em P, mas 3-SAT é NP-completo.

2-COLORING está em P, mas 3-COLORING é NP-completo.
### Mensagem

Pequenas mudanças no enunciado podem deslocar um problema da tratabilidade para a aparente intratabilidade.

{28}------------------------------------------------
## O que sabemos, o que suspeitamos, o que não provamos

| Afirmação                    | Status           | Comentário                             |
|------------------------------|------------------|----------------------------------------|
| $P \subseteq NP$             | provado          | basta ignorar certificados             |
| $P \subseteq coNP$           | provado          | P é fechada por complemento            |
| $P = NP$                     | aberto           | problema do milênio                    |
| $NP = coNP$                  | aberto           | teria fortes consequências estruturais |
| “Provavelmente $P \neq NP$ ” | crença dominante | sem prova formal                       |
## Ponto pedagógico

Em complexidade, evidência empírica e consenso da comunidade não substituem demonstração matemática.

{29}------------------------------------------------
### Por que é tão difícil provar?

Relativização existem oráculos com  $P^A = NP^A$  e outros com  $P^B \neq NP^B$ ;

Natural proofs certas técnicas de lower bounds entram em conflito com a existência de geradores pseudoaleatórios fortes;

Algebrização mesmo extensões algébricas das técnicas relativizantes não bastam.
## Conclusão

Uma prova de P vs NP precisará escapar dessas três barreiras.

[6, 19, 1]

{30}------------------------------------------------
## Problemas NP-Intermediários
## Teorema de Ladner

Se  $P \neq NP$ , então existem problemas em NP que não estão em P e também não são NP-complete.

- FACTOR é um candidato clássico;
- GRAPH-ISOMORPHISM também;
- Babai mostrou algoritmo quase-polinomial para isomorfismo de grafos.
### Leitura

O mundo de NP pode ser mais rico do que apenas “fácil” versus “NP-complete”.

[17, 5, 3]

{31}------------------------------------------------
### Por que essa pergunta importa tanto?

- ela organiza a teoria moderna de algoritmos e reduções;
- ajuda a distinguir quando buscar algoritmos exatos e quando buscar aproximações ou heurísticas;
- dá linguagem formal para explicar por que certos problemas resistem a décadas de esforço algorítmico;
- conecta computação, matemática, lógica e criptografia.
## Síntese

P vs NP não pergunta apenas “o que é rápido?”, mas também “o que significa *descobrir* uma solução a partir de uma prova de que ela existe?”.

{32}------------------------------------------------
## Exercício 1: Verdadeiro ou Falso?

Classifique cada afirmação como verdadeira (V) ou falsa (F).

- 1 Todo problema em P também pertence a NP.
- 2 NP significa “não polinomial”.
- 3 Em NP, toda instância NÃO precisa ter certificado curto.
- 4 Se um problema NP-complete estiver em P, então  $P = NP$ .
### Gabarito comentado

1. Verdadeiro: basta usar certificado vazio e rodar o algoritmo de decisão. 2. Falso: NP significa *nondeterministic polynomial time*. 3. Verdadeiro: NP exige certificados curtos apenas para instâncias SIM. 4. Verdadeiro: esse é o mecanismo central da NP-completude.

{33}------------------------------------------------
### Exercício 2: Classificação de Problemas

Classifique cada problema e justifique brevemente.

| Problema          | Comentários                                          |
|-------------------|------------------------------------------------------|
| PATH              | P: BFS/DFS decide em tempo linear.                   |
| 2-SAT             | P: grafo de implicação + CFCs.                       |
| PRIMES            | P, logo também em $NP \cap coNP$ .                   |
| SAT               | NP-complete.                                         |
| UNSAT             | coNP-complete: complemento de SAT.                   |
| GRAPH-ISOMORPHISM | Em NP; não se sabe se está em P ou se é NP-complete. |

{34}------------------------------------------------
### Exercício 3: Projetando Verificadores

Descreva um verificador polinomial para: VERTEX-COVER, HAMPATH, SUBSET-SUM e SET-COVER.
### Comentários

VERTEX-COVER: certificado  $C$  com  $|C| \leq k$ ; checar se toda aresta toca  $C$ ; tempo  $O(|E|)$ . HAMPATH: certificado = sequência de vértices; checar unicidade e adjacência; tempo polinomial. SUBSET-SUM: certificado = subconjunto; somar e comparar com  $t$ . SET-COVER: certificado = subfamília com no máximo  $k$  conjuntos; checar se a união cobre  $U$ .
### Discussão

O padrão é sempre o mesmo: o certificado entrega a solução candidata, e o verificador só precisa confirmar localmente que ela funciona.

{35}------------------------------------------------
### Exercício 4: Provas de pertinência em P

Mostre que os problemas abaixo pertencem a P:

- 1 CONNECTED
- 2 2-COLORING
- 3 DFA-EQUIVALENCE
- 4 2-SAT
### Comentários

CONNECTED: BFS/DFS em  $O(|V| + |E|)$ . 2-COLORING: coloração por paridade de nível; funciona porque grafos bipartidos não têm ciclo ímpar.

DFA-EQUIVALENCE: produto dos autômatos e busca por estado alcançável com respostas diferentes. 2-SAT: satisfatível sse nenhum par  $x_i, \neg x_i$  pertence à mesma CFC do grafo de implicação.

{36}------------------------------------------------
### Exercício 5: Relações entre as classes

- 1 Prove  $P \subseteq NP$ .
- 2 Prove  $P \subseteq coNP$ .
- 3 Mostre que  $P = NP$  implica  $NP = coNP$ .
### Comentários

Determinístico polinomial = verificador com certificado vazio, então  $P \subseteq NP$ . Como  $P$  é fechada por complemento,  $P \subseteq coNP$ . Se  $P = NP$ , segue  $NP = coNP$ .

{37}------------------------------------------------
### Exercício 6: Consequências estruturais

- 1 Discuta por que a implicação inversa  $NP = coNP \Rightarrow P = NP$  não é conhecida.
- 2 Suponha SAT em coNP. O que segue?
### Comentários

A igualdade  $NP = coNP$ , sozinha, não produz algoritmo polinomial para todos os problemas de NP. Já se SAT estivesse em coNP, como SAT é NP-complete, obteríamos  $NP = coNP$ .

{38}------------------------------------------------
### Exercício 7: Verificar versus encontrar

Explique por que um algoritmo polinomial para SAT implicaria também um algoritmo polinomial para encontrar uma atribuição satisfatória.
### Comentários

Fixamos variáveis uma a uma e chamamos o decisor em fórmulas restringidas. Se  $\phi[x_1 := 0]$  ainda for satisfatível, mantemos  $x_1 = 0$ ; caso contrário, fixamos  $x_1 = 1$ . Repetindo o processo, reconstruímos uma atribuição completa com número polinomial de consultas ao decisor.
### Discussão

Esse argumento mostra por que, em muitos problemas de NP, decisão e busca têm dificuldade essencialmente equivalente.

{39}------------------------------------------------
### Exercício 8: Contrastando problemas

Discuta por que os pares abaixo são pedagogicamente importantes:

- 1 2-SAT versus 3-SAT
- 2 2-COLORING versus 3-COLORING
- 3 PATH versus HAMPATH
### Comentários

Os pares mostram que pequenas mudanças estruturais no enunciado podem alterar drasticamente a complexidade. Em PATH, basta alcançar o destino; em HAMPATH, é preciso visitar todos os vértices exatamente uma vez. Em 2-SAT e 2-COLORING, há estrutura suficiente para algoritmos polinomiais; em 3-SAT e 3-COLORING, a liberdade combinatória explode.

<!-- DATALAB_CHUNK 3: pages 41-60 -->

{40}------------------------------------------------

# Exercício 9: P vs NP em profundidade

- 1 Enuncie o teorema de Ladner.
- 2 O que significa dizer que uma técnica relativiza?
- 3 Resuma, em poucas linhas, as barreiras de natural proofs e algebrização.
- 4 Por que experimentos computacionais não resolvem P vs NP?
## Comentários

Ladner: se  $P \neq NP$ , existem problemas em NP que não estão em P nem são NP-complete. Uma técnica relativiza quando continua válida na presença de oráculos. Natural proofs limitam certas estratégias de lower bounds; algebrização amplia essa barreira. Experimentos observam apenas famílias finitas de instâncias e não substituem prova universal.

{41}------------------------------------------------
## Leituras Sugeridas
## Livros

- Sipser, cap. 7 e 8: definição de P, NP, verificadores e SAT.
- Papadimitriou, cap. 2 a 8: tratamento formal das classes e reduções.
- Arora–Barak, cap. 1 a 3: visão moderna de P, NP e barreiras.
## Artigos clássicos

- Cobham e Edmonds para a tese de tratabilidade polinomial;
- Cook e Karp para NP-completude;
- Agrawal–Kayal–Saxena para primalidade em P;
- Baker–Gill–Solovay, Razborov–Rudich e Aaronson–Wigderson para as barreiras em P vs NP.

{42}------------------------------------------------
### Glossário: PATH

**Nome:** PATH

**Complexidade do problema:**  $O(|V| + |E|)$

**Classe:** P

**Conferência do certificado:** um caminho candidato pode ser conferido em  $O(|V|)$  com consultas de adjacência
#### Descrição em alto nível

Dado um grafo  $G$  e vértices  $s, t$ , perguntar se existe um caminho de  $s$  até  $t$ .
#### Instância resolvida

Em  $G$  com arestas  $\{(s, a), (a, c), (c, t)\}$ , a instância  $(G, s, t)$  tem resposta SIM, com caminho  $s \rightarrow a \rightarrow c \rightarrow t$ .

{43}------------------------------------------------

{44}------------------------------------------------
### Glossário: 2-COLORING

**Nome:** 2-COLORING

**Complexidade do problema:**  $O(|V| + |E|)$

**Classe:** P

**Conferência do certificado:** uma coloração candidata é conferida em  $O(|V| + |E|)$
#### Descrição em alto nível

Dado um grafo, decidir se ele é bipartido, isto é, se admite coloração própria com duas cores.
#### Instância resolvida

No caminho  $a - b - c - d$ , a coloração  $\{a, c\}$  em azul e  $\{b, d\}$  em vermelho é válida; portanto a resposta é SIM.

{45}------------------------------------------------
### Glossário: SHORTEST-PATH-LEQ

**Nome:** SHORTEST-PATH-LEQ

**Complexidade do problema:** polinomial; por exemplo, Dijkstra em  $O((|V| + |E|) \log |V|)$

**Classe:** P

**Conferência do certificado:** um caminho candidato e seu custo total são conferidos em tempo linear no caminho
#### Descrição em alto nível

Dados um grafo com pesos, vértices  $s$ ,  $t$  e limite  $B$ , perguntar se existe caminho de  $s$  a  $t$  com custo no máximo  $B$ .
#### Instância resolvida

Se  $s \rightarrow a$  custa 2,  $a \rightarrow t$  custa 3 e  $B = 5$ , a resposta é SIM pelo caminho  $s \rightarrow a \rightarrow t$  com custo total 5.

{46}------------------------------------------------
### Glossário: MAX-FLOW-GEQ

**Nome:** MAX-FLOW-GEQ

**Complexidade do problema:** polinomial; Edmonds–Karp em  $O(|V||E|^2)$

**Classe:** P

**Conferência do certificado:** um fluxo candidato é conferido em  $O(|V| + |E|)$
#### Descrição em alto nível

Dada uma rede com capacidades, origem  $s$ , sorvedouro  $t$  e limite  $B$ , perguntar se o fluxo máximo é pelo menos  $B$ .
#### Instância resolvida

Se há dois caminhos disjuntos  $s \rightarrow a \rightarrow t$  e  $s \rightarrow b \rightarrow t$ , ambos com capacidade 1, então para  $B = 2$  a resposta é SIM.

{47}------------------------------------------------
### Glossário: BIP-MATCHING-GEQ

**Nome:** BIP-MATCHING-GEQ

**Complexidade do problema:** polinomial; Hopcroft–Karp em  $O(|E|\sqrt{|V|})$

**Classe:** P

**Conferência do certificado:** um matching candidato é conferido em  $O(|E|)$
#### Descrição em alto nível

Dado um grafo bipartido e um inteiro  $k$ , decidir se existe emparelhamento de tamanho pelo menos  $k$ .
#### Instância resolvida

Com bipartição  $\{u_1, u_2\}$  e  $\{v_1, v_2\}$ , arestas  $\{(u_1, v_1), (u_1, v_2), (u_2, v_2)\}$  e  $k = 2$ , a resposta é SIM pelo matching  $\{(u_1, v_1), (u_2, v_2)\}$ .

{48}------------------------------------------------
### Glossário: RELPRIME

**Nome:** RELPRIME

**Complexidade do problema:**  $O(\log \min(a, b))$

**Classe:** P

**Conferência do certificado:** coeficientes de Bézout podem ser conferidos em tempo polinomial em  $\log a + \log b$

**Descrição em alto nível**

Dados inteiros  $a, b$ , decidir se  $\gcd(a, b) = 1$ .

**Instância resolvida**

Para  $(14, 25)$ , temos  $\gcd(14, 25) = 1$ ; portanto a resposta é SIM.

{49}------------------------------------------------
### Glossário: 2-SAT

**Nome:** 2-SAT

**Complexidade do problema:**  $O(n + m)$  para  $n$  variáveis e  $m$  cláusulas

**Classe:** P

**Conferência do certificado:** uma atribuição candidata é conferida em  $O(|\varphi|)$
#### Descrição em alto nível

Dada uma fórmula 2-CNF, decidir se existe atribuição booleana que a satisfaça.
#### Instância resolvida

Para  $\varphi = (x_1 \vee x_2) \wedge (\neg x_1 \vee x_3) \wedge (\neg x_2 \vee \neg x_3)$ , a atribuição  $x_1 = 1, x_2 = 0, x_3 = 1$  satisfaz a fórmula; resposta SIM.

{50}------------------------------------------------
### Glossário: PRIMES

**Nome:** PRIMES

**Complexidade do problema:** polinomial em  $\log n$ ; AKS

**Classe:** P; em particular,  $\text{NP} \cap \text{coNP}$

**Conferência do certificado:** certificados de primalidade são conferíveis em tempo polinomial em  $\log n$
#### Descrição em alto nível

Dado um inteiro  $n$  em binário, decidir se  $n$  é primo.
#### Instância resolvida

Para  $n = 13$ , não há divisores não triviais; a resposta é SIM.

{51}------------------------------------------------
### Glossário: LP-FEASIBILITY

**Nome:** LP-FEASIBILITY

**Complexidade do problema:** polinomial no tamanho da entrada

**Classe:** P

**Conferência do certificado:** um vetor racional candidato é conferido em tempo polinomial
#### Descrição em alto nível

Dado um sistema linear, decidir se existe solução real que satisfaça todas as restrições.
#### Instância resolvida

Para  $x + y \leq 4$ ,  $x \geq 1$ ,  $y \geq 1$ , a solução  $(1, 1)$  satisfaz o sistema; resposta SIM.

{52}------------------------------------------------
### Glossário: DFA-EMPTINESS

**Nome:** DFA-EMPTINESS

**Complexidade do problema:**  $O(|Q| + |\delta|)$

**Classe:** P

**Conferência do certificado:** uma palavra aceita candidata é conferida em tempo linear no comprimento da palavra

**Descrição em alto nível**

Dado um AFD, decidir se sua linguagem é vazia.

**Instância resolvida**

Se o estado inicial alcança um estado final pela palavra *ab*, então a linguagem não é vazia; logo a resposta é SIM.

{53}------------------------------------------------
### Glossário: DFA-EQUIVALENCE

**Nome:** DFA-EQUIVALENCE

**Complexidade do problema:**  $O(|Q_1||Q_2||\Sigma|)$

**Classe:** P

**Conferência do certificado:** uma palavra distinguidora é conferida em tempo linear no comprimento da palavra

**Descrição em alto nível**

Dados dois AFDs, decidir se reconhecem a mesma linguagem.

**Instância resolvida**

Se ambos aceitam exatamente palavras com número par de 1s, então são equivalentes; a resposta é SIM.

{54}------------------------------------------------
### Glossário: SAT

**Nome:** SAT

**Complexidade do problema:** exponencial no pior caso para algoritmos gerais conhecidos

**Classe:** NP-complete

**Conferência do certificado:**  $O(|\varphi|)$
#### Descrição em alto nível

Dada uma fórmula booleana, decidir se existe atribuição que a torne verdadeira.
#### Instância resolvida

Para  $\phi = (x_1 \vee \neg x_2) \wedge (x_2 \vee x_3)$ , a atribuição  $x_1 = 1, x_2 = 1, x_3 = 0$  satisfaz  $\phi$ ; resposta SIM.

{55}------------------------------------------------
### Glossário: 3-SAT

**Nome:** 3-SAT

**Complexidade do problema:** exponencial no pior caso para algoritmos gerais conhecidos

**Classe:** NP-complete

**Conferência do certificado:**  $O(m)$ , onde  $m$  é o número de cláusulas

**Descrição em alto nível**

Variante de SAT em que cada cláusula tem exatamente três literais.

**Instância resolvida**

Para  $\phi = (x \vee y \vee z) \wedge (\neg x \vee y \vee \neg z)$ , a atribuição  $x = 0, y = 1, z = 0$  satisfaz a fórmula; resposta SIM.

{56}------------------------------------------------
### Glossário: CLIQUE

**Nome:** CLIQUE

**Complexidade do problema:** exponencial/combinatorial no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(k^2)$
#### Descrição em alto nível

Dado um grafo e um inteiro  $k$ , decidir se há subconjunto de  $k$  vértices mutuamente adjacentes.
#### Instância resolvida

Se  $a, b, c$  formam um triângulo e  $k = 3$ , a resposta é SIM pela clique  $\{a, b, c\}$ .

{57}------------------------------------------------
### Glossário: INDEP-SET

**Nome:** INDEP-SET

**Complexidade do problema:** exponencial/combinatorial no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(k^2)$  ou  $O(|E|)$
#### Descrição em alto nível

Dado um grafo e um inteiro  $k$ , decidir se há conjunto independente de tamanho pelo menos  $k$ .
#### Instância resolvida

No caminho  $a - b - c$ , para  $k = 2$  a resposta é SIM com conjunto independente  $\{a, c\}$ .

{58}------------------------------------------------
### Glossário: VERTEX-COVER

**Nome:** VERTEX-COVER

**Complexidade do problema:** exponencial/combinatorial no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(|E|)$
#### Descrição em alto nível

Dado um grafo e um inteiro  $k$ , decidir se existe conjunto de no máximo  $k$  vértices que cobre todas as arestas.
#### Instância resolvida

No triângulo  $\{a, b, c\}$ , para  $k = 2$  a resposta é SIM com cobertura  $\{a, b\}$ .

{59}------------------------------------------------
### Glossário: HAMPATH

**Nome:** HAMPATH

**Complexidade do problema:** exponencial no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(|V| + |E|)$
#### Descrição em alto nível

Dado um grafo, decidir se existe caminho simples que visita todos os vértices exatamente uma vez.
#### Instância resolvida

No grafo com arestas  $\{(s, a), (a, b), (b, t)\}$ , o caminho  $s \rightarrow a \rightarrow b \rightarrow t$  é Hamiltoniano; resposta SIM.

<!-- DATALAB_CHUNK 4: pages 61-78 -->

{60}------------------------------------------------
## Glossário: HAMCYCLE

**Nome:** HAMCYCLE

**Complexidade do problema:** exponencial no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(|V| + |E|)$
### Descrição em alto nível

Dado um grafo, decidir se existe ciclo simples que visita todos os vértices exatamente uma vez.
### Instância resolvida

No ciclo  $a - b - c - d - a$ , a instância tem resposta SIM com ciclo Hamiltoniano  $a \rightarrow b \rightarrow c \rightarrow d \rightarrow a$ .

{61}------------------------------------------------
## Glossário: 3-COLORING

**Nome:** 3-COLORING

**Complexidade do problema:** exponencial no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(|E|)$
### Descrição em alto nível

Dado um grafo, decidir se seus vértices podem ser coloridos com três cores sem conflito em arestas.
### Instância resolvida

O triângulo  $K_3$  é 3-colorível: basta usar três cores distintas; resposta SIM.

{62}------------------------------------------------
## Glossário: SUBSET-SUM

**Nome:** SUBSET-SUM

**Complexidade do problema:** pseudo-polinomial em  $t$ ; exponencial no tamanho binário no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(n)$  somas aritméticas sobre o subconjunto

**Descrição em alto nível**

Dados inteiros e alvo  $t$ , decidir se algum subconjunto soma exatamente  $t$ .

**Instância resolvida**

Para  $S = \{3, 5, 6, 9, 11\}$  e  $t = 20$ , a resposta é SIM com subconjunto  $\{3, 6, 11\}$ .

{63}------------------------------------------------
## Glossário: PARTITION

**Nome:** PARTITION

**Complexidade do problema:** pseudo-polinomial; exponencial no tamanho binário no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(n)$  para somar cada lado da partição
### Descrição em alto nível

Dado um multiconjunto de inteiros, decidir se ele pode ser separado em duas partes de soma igual.
### Instância resolvida

Para  $\{1, 5, 6\}$ , temos soma total 12 e partição  $\{1, 5\}$  e  $\{6\}$ ; logo a resposta é SIM.

{64}------------------------------------------------
## Glossário: KNAPSACK

**Nome:** KNAPSACK

**Complexidade do problema:** pseudo-polinomial; exponencial no tamanho binário no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(n)$  para somar pesos e valores
### Descrição em alto nível

Dados itens com pesos e valores, limite de peso  $B$  e meta de valor  $V$ , decidir se existe subconjunto viável.
### Instância resolvida

Itens  $(p, v) = (2, 3), (3, 4), (4, 5)$ , com  $B = 5$  e  $V = 7$ : escolhendo os dois primeiros, temos peso 5 e valor 7; resposta SIM.

{65}------------------------------------------------
## Glossário: TSP-LEQ

**Nome:** TSP-LEQ

**Complexidade do problema:** exponencial no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(n)$  para conferir um tour e seu custo
### Descrição em alto nível

Dadas cidades, distâncias e um limite  $B$ , decidir se há ciclo Hamiltoniano de custo total no máximo  $B$ .
### Instância resolvida

Num quadrado com quatro cidades e arestas do perímetro de custo 1, para  $B = 4$  a resposta é SIM pelo tour do perímetro.

{66}------------------------------------------------
## Glossário: SET-COVER

**Nome:** SET-COVER

**Complexidade do problema:** exponencial/combinatorial no pior caso

**Classe:** NP-complete

**Conferência do certificado:**  $O(|U| + \sum |S_i|)$
### Descrição em alto nível

Dados universo  $U$ , família  $\mathcal{S}$  e inteiro  $k$ , decidir se  $U$  pode ser coberto com no máximo  $k$  conjuntos.
### Instância resolvida

Se  $U = \{1, 2, 3, 4\}$  e  $\mathcal{S} = \{\{1, 2\}, \{2, 3\}, \{3, 4\}, \{1, 4\}\}$ , para  $k = 2$  a resposta é SIM com  $\{1, 2\}$  e  $\{3, 4\}$ .

{67}------------------------------------------------
## Glossário: INTEGER-PROG

**Nome:** INTEGER-PROG

**Complexidade do problema:** exponencial no pior caso em sua forma geral

**Classe:** NP-complete

**Conferência do certificado:** uma atribuição inteira candidata é conferida em tempo polinomial
### Descrição em alto nível

Dado um sistema de inequações lineares com exigência de integridade, decidir se existe solução inteira viável.
### Instância resolvida

Para  $x + y = 3$ ,  $x \geq 0$ ,  $y \geq 0$ ,  $x, y \in \mathbb{Z}$ , a solução  $(1, 2)$  mostra que a resposta é SIM.

{68}------------------------------------------------
## Glossário: UNSAT

**Nome:** UNSAT

**Complexidade do problema:** não se conhece algoritmo polinomial geral; problema completo para coNP

**Classe:** coNP-complete

**Conferência do certificado:** para instâncias NÃO, um certificado do complemento é conferido em  $O(|\varphi|)$
### Descrição em alto nível

Dada uma fórmula booleana, decidir se nenhuma atribuição a satisfaz.
### Instância resolvida

Para  $\phi = (x) \wedge (\neg x)$ , não existe atribuição satisfatória; resposta SIM.

{69}------------------------------------------------
## Glossário: TAUTOLOGY

**Nome:** TAUTOLOGY

**Complexidade do problema:** não se conhece algoritmo polinomial geral; problema completo para coNP

**Classe:** coNP-complete

**Conferência do certificado:** para instâncias NÃO, uma atribuição falsificadora é conferida em  $O(|\varphi|)$
### Descrição em alto nível

Dada uma fórmula booleana, decidir se ela é verdadeira sob toda atribuição.
### Instância resolvida

Para  $\phi = (x \vee \neg x)$ , a fórmula é verdadeira para qualquer valor de  $x$ ; logo a resposta é SIM.

{70}------------------------------------------------
## Glossário: FACTOR

**Nome:** FACTOR

**Complexidade do problema:** desconhecida como polinomial ou NP-completa

**Classe:**  $NP \cap coNP$ ; candidato a NP-intermediário

**Conferência do certificado:** um fator candidato é conferido em tempo polinomial em  $\log n$
### Descrição em alto nível

Versão de decisão: dados  $n$  e um limite  $k$ , decidir se  $n$  possui fator não trivial de tamanho apropriado.
### Instância resolvida

Para  $n = 91$  e  $k = 10$ , a resposta é SIM, pois 7 divide 91 e  $7 \leq 10$ .

{71}------------------------------------------------
## Glossário: GRAPH-ISOMORPHISM

**Nome:** GRAPH-ISOMORPHISM

**Complexidade do problema:** quase-polinomial no melhor algoritmo geral conhecido

**Classe:** NP; não se sabe se está em P ou se é NP-complete

**Conferência do certificado:**  $O(|V|^2)$  para conferir uma bijeção candidata
### Descrição em alto nível

Dados dois grafos, decidir se existe renomeação dos vértices que preserve adjacências.
### Instância resolvida

Dois ciclos com quatro vértices são isomorfos. A bijeção  $a \mapsto 1$ ,  $b \mapsto 2$ ,  $c \mapsto 3$ ,  $d \mapsto 4$  preserva as arestas; resposta SIM.

{72}------------------------------------------------
## Referências I

- [1] Scott Aaronson e Avi Wigderson. “Algebrization: A New Barrier in Complexity Theory”. Em: *ACM Transactions on Computation Theory* 1.1 (2009), pp. 1–54. DOI: [10.1145/1490270.1490272](https://doi.org/10.1145/1490270.1490272).
- [2] Manindra Agrawal, Neeraj Kayal e Nitin Saxena. “PRIMES Is in P”. Em: *Annals of Mathematics* 160.2 (2004), pp. 781–793. DOI: [10.4007/annals.2004.160.781](https://doi.org/10.4007/annals.2004.160.781).
- [3] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009. ISBN: 978-0521424264.

{73}------------------------------------------------
## Referências II

[4] Bengt Aspvall, Michael F. Plass e Robert Endre Tarjan. “A Linear-Time Algorithm for Testing the Truth of Certain Quantified Boolean Formulas”. Em: *Information Processing Letters* 8.3 (1979), pp. 121–123. DOI: [10.1016/0020-0190\(79\)90002-4](#).

[5] László Babai. “Graph Isomorphism in Quasipolynomial Time”. Em: *Proceedings of the Forty-Eighth Annual ACM Symposium on Theory of Computing*. 2016, pp. 684–697. DOI: [10.1145/2897518.2897542](#).

[6] Theodore Baker, John Gill e Robert Solovay. “Relativizations of the  $P \stackrel{?}{=} NP$  Question”. Em: *SIAM Journal on Computing* 4.4 (1975), pp. 431–442. DOI: [10.1137/0204037](#).

{74}------------------------------------------------
## Referências III

- [7] Clay Mathematics Institute. *P vs NP Problem*. URL: <https://www.claymath.org/millennium/p-vs-np/> (acesso em 20/05/2026).
- [8] Alan Cobham. “The Intrinsic Computational Difficulty of Functions”. Em: *Proceedings of the 1964 International Congress for Logic, Methodology, and Philosophy of Science* (1965), pp. 24–30.
- [9] Stephen A. Cook. “The Complexity of Theorem-Proving Procedures”. Em: *Proceedings of the Third Annual ACM Symposium on Theory of Computing*. 1971, pp. 151–158. DOI: [10.1145/800157.805047](https://doi.org/10.1145/800157.805047).

{75}------------------------------------------------
## Referências IV

- [10] Jack Edmonds. “Paths, Trees, and Flowers”. Em: *Canadian Journal of Mathematics* 17 (1965), pp. 449–467. DOI: [10.4153/CJM-1965-045-4](https://doi.org/10.4153/CJM-1965-045-4).
- [11] Jack Edmonds e Richard M. Karp. “Theoretical Improvements in Algorithmic Efficiency for Network Flow Problems”. Em: *Journal of the ACM* 19.2 (1972), pp. 248–264. DOI: [10.1145/321694.321699](https://doi.org/10.1145/321694.321699).
- [12] Michael R. Garey e David S. Johnson. *Computers and Intractability: A Guide to the Theory of NP-Completeness*. W. H. Freeman, 1979. ISBN: 978-0716710455.

{76}------------------------------------------------
## Referências V

- [13] John E. Hopcroft e Richard M. Karp. “An  $n^{5/2}$  Algorithm for Maximum Matchings in Bipartite Graphs”. Em: *SIAM Journal on Computing* 2.4 (1973), pp. 225–231. DOI: [10.1137/0202019](https://doi.org/10.1137/0202019).
- [14] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006. ISBN: 978-0321455369.
- [15] Richard M. Karp. “Reducibility Among Combinatorial Problems”. Em: *Complexity of Computer Computations*. Springer, 1972, pp. 85–103. DOI: [10.1007/978-1-4684-2001-2\\_9](https://doi.org/10.1007/978-1-4684-2001-2_9).

{77}------------------------------------------------
## Referências VI

- [16] Leonid G. Khachiyan. “A Polynomial Algorithm in Linear Programming”. Em: *Soviet Mathematics Doklady* 20 (1979), pp. 191–194.
- [17] Richard E. Ladner. “On the Structure of Polynomial Time Reducibility”. Em: *Journal of the ACM* 22.1 (1975), pp. 155–171. DOI: [10.1145/321864.321877](https://doi.org/10.1145/321864.321877).
- [18] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994. ISBN: 978-0201530827.
- [19] Alexander A. Razborov e Steven Rudich. “Natural Proofs”. Em: *Journal of Computer and System Sciences* 55.1 (1997), pp. 24–35. DOI: [10.1006/jcss.1997.1494](https://doi.org/10.1006/jcss.1997.1494).
- [20] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012. ISBN: 978-1133187790.

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-4b6451a59338bba97433c43461a5c372_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Universidade Federal do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

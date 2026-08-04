<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Da Computabilidade à Complexidade**
  - O Que Já Sabemos
  - Nova Pergunta
  - Teoria da Complexidade
  - Recursos Computacionais
  - Principais Recursos
  - Na Prática
- **Medindo Complexidade**
  - Tamanho da Entrada
  - Análise de Pior Caso
  - Notação Assintótica
- **Classes de Crescimento**
  - Divisão Fundamental
  - Sobre a Classe Polinomial (**P**)
  - Sobre Classes Super-Polinomiais
  - Características
  - Intratabilidade
  - Problemas de Decisão
- **Classes de Complexidade de Tempo**
  - Classes de Complexidade de Tempo
  - Definições Básicas
  - Classes Determinísticas
  - Classes Não-determinísticas
  - Sobre a classe NP...
- **Classes de Complexidade de Espaço**
  - Definição Básica
  - Classes Determinísticas
  - Classes Não-determinísticas
  - Classes de Complexidade de Espaço - Hierarquia
  - Relações entre Tempo e Espaço
  - Teoremas
  - Comparando Tempo e Espaço
  - Hierarquia de Classes
  - Reduções
  - Intuição
- **Hard e Complete**
  - Definições para uma Classe $\mathcal{C}$
- **Intratabilidade**
  - O que é “Intratável”?
  - Evidências de Intratabilidade
  - Lidando com Intratabilidade
  - Estratégias Práticas
- **Mapa das Classes**
- **Resumo**
- **Conceitos Principais**
  - Importância
  - Leituras Recomendadas
  - Livros-base
  - Artigos clássicos
  - Exercício 1: Notação Assintótica
  - Exercício 2: Classificação de Complexidade
  - Exercício 3: Relações entre Classes
  - Exercício 4: Hard e Complete
  - Exercício 5: Roteiro de Redução
  - Exercício 6: Hierarquia
  - Exercício 7: Problemas Práticos
  - Exercício 8: Intratabilidade na Prática
- **Referências I**
- **Referências II**
- **Referências III**
- **Referências IV**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Classes de Problemas e Complexidade Computacional

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 16

Teoria da Computabilidade e Complexidade  
Ciência da Computação

15 de maio de 2026

The logo of PUCRS, featuring a shield with a cross and a star, and the text "PUCRS" below it.

Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

{1}------------------------------------------------
## Sumário

- 1 Introdução

- 2 Tempo vs. Espaço

- 3 Teoremas de Hierarquia

- 4 Complete vs. Hard e Intratabilidade

- 5 Exercícios

Faded coat of arms of the Holy See (Vatican City) featuring a shield with a cross and star, surmounted by a papal tiara and crossed keys, with the motto 'AD VERVM DVCIT' below.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-b6cb8677b4ffb35c6468fa5c24091bff_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faded coat of arms of the Holy See (Vatican City) featuring a shield with a cross and star, surmounted by a papal tiara and crossed keys, with the motto 'AD VERVM DVCIT' below.
<!-- /IMAGE_DESCRIPTION -->
## Da Computabilidade à Complexidade
### O Que Já Sabemos

- Existem problemas **indecidíveis** (Halting, Entscheidungsproblem)
- Máquinas de Turing definem o que é “computável”
- Alguns problemas simplesmente não podem ser resolvidos
### Nova Pergunta

Para problemas que **podem** ser resolvidos:

*Quão difíceis são?*

*Quantos recursos são necessários?*
### Teoria da Complexidade

Classifica problemas decidíveis de acordo com os **recursos computacionais** necessários para resolvê-los.

{3}------------------------------------------------
### Recursos Computacionais
### Principais Recursos

**Tempo** Número de passos (operações) até a resposta

**Espaço** Quantidade de memória utilizada

**Aleatoriedade** Bits aleatórios necessários para fazer escolhas não-determinísticas (ex: em algoritmos randomizados)

**Paralelismo** Número de processadores

**Comunicação** Bits trocados entre partes
### Na Prática

**Tempo e espaço** são os mais importantes para a maioria das aplicações.

{4}------------------------------------------------
## Medindo Complexidade
### Tamanho da Entrada

A complexidade é medida como **função do tamanho da entrada**  $n = |w|$ .

- Entrada: string  $w$  de  $n$  bits/símbolos
- Complexidade de tempo:  $T(n)$  = máximo de passos para entradas de tamanho  $n$
- Complexidade de espaço:  $S(n)$  = máximo de células usadas
### Análise de Pior Caso

Consideramos o **pior caso**: a entrada que requer mais recursos.

$$T(n) = \max_{|w|=n} \{\text{tempo para processar } w\}$$

{5}------------------------------------------------
### Notação Assintótica
#### Notação $O$ (Big-O)

$f(n) = O(g(n))$  se existem  $c > 0$  e  $n_0$  tais que:

$$\forall n \geq n_0 : f(n) \leq c \cdot g(n)$$

“ $f$  cresce no máximo tão rápido quanto  $g$ ”
#### Outras Notações

- $f(n) = \Omega(g(n))$ :  $f$  cresce pelo menos tão rápido quanto  $g$
- $f(n) = \Theta(g(n))$ :  $f$  cresce na mesma taxa que  $g$
- $f(n) = o(g(n))$ :  $f$  cresce estritamente mais devagar que  $g$
#### Exemplo

- $3n^2 + 5n + 7 = O(n^2)$

{6}------------------------------------------------
## Classes de Crescimento

| Nome         | Função        | Exemplo                      |
|--------------|---------------|------------------------------|
| Constante    | $O(1)$        | Acesso a array               |
| Logarítmica  | $O(\log n)$   | Busca binária                |
| Linear       | $O(n)$        | Busca sequencial             |
| Linearítmica | $O(n \log n)$ | Merge sort                   |
| Quadrática   | $O(n^2)$      | Bubble sort                  |
| Cúbica       | $O(n^3)$      | Multiplicação de matrizes    |
| Polinomial   | $O(n^k)$      | Fluxo máximo, matching, etc. |
| Exponencial  | $O(2^n)$      | Força bruta em subconjuntos  |
| Fatorial     | $O(n!)$       | Força bruta em permutações   |
### Divisão Fundamental

**Polinomial** ( $O(n^k)$ ) vs. **Super-polinomial** ( $\omega(n^k)$ ) é a fronteira clássica entre “tratável” e “intratável”. “Polinomial” é usado como aproximação formal de “eficiente”, mas isso não significa necessariamente “rápido” na prática.

{7}------------------------------------------------
### Sobre a Classe Polinomial (**P**)
#### Argumentos a Favor

- **Fechamento:** Polinômios são fechados sob composição
- **Robustez:** Independe de modelo de máquina (até polinômio)
- **Prático:** Para  $n$  grande, diferença entre  $n^2$  e  $2^n$  é enorme
#### Comparação para $n = 100$

|       |                    |
|-------|--------------------|
| $n$   | 100                |
| $n^2$ | 10.000             |
| $n^3$ | 1.000.000          |
| $2^n$ | $\approx 10^{30}$  |
| $n!$  | $\approx 10^{158}$ |
#### Tese de Cobham-Edmonds

Problemas “eficientemente computáveis” pertencem à classe **P**.

[3, 5]

A set of small, faint navigation icons typically found in Beamer presentations, including symbols for back, forward, and search.

Navigation icons

{8}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-528d839f704da63e4162ae966073e5c6_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Navigation icons
<!-- /IMAGE_DESCRIPTION -->
### Sobre Classes Super-Polinomiais
### Características

- Crescimento **mais rápido** que qualquer polinômio
- Formalmente:  $f(n) = \omega(n^k)$  para todo  $k \geq 0$
- Incluem funções como  $2^n$ ,  $n!$ ,  $2^{2^n}$ , etc.
### Intratabilidade

Problemas com complexidade super-polinomial são **intratáveis**:

- Impossível resolver para entradas de tamanho moderado
- Mesmo para  $n = 100$ , podem requerer  $10^{30}$  operações
- Não é viável a força bruta ou algoritmos exponenciais ingênuos
#### Exemplos

- Busca exaustiva em  $2^n$  subconjuntos
- Enumeração de  $n!$  permutações

{9}------------------------------------------------
### Problemas de Decisão
#### Definição

Um **problema de decisão** é uma pergunta com resposta SIM/NÃO. Formalmente: uma linguagem  $L \subseteq \Sigma^*$ :

- $w \in L$ : SIM,  $w \notin L$ : NÃO
#### Exemplos

- PRIMES: “ $n$  é primo?”
- CAMINHO: “Existe caminho de  $s$  a  $t$  em  $G$ ?”
- SAT: “Esta fórmula booleana é satisfatível?”
- CLIQUE: “ $G$  contém “clique” de tamanho  $k$ ?”
#### Por que Decisão?

P e NP são definidas sobre linguagens, então decisão é “natural”.

{10}------------------------------------------------
## Classes de Complexidade de Tempo

A Venn diagram illustrating the relationship between complexity classes. A large blue circle is labeled "EXPTIME". Inside this circle, there are two smaller circles that overlap each other. The left circle is green and labeled "NP". The right circle is red and labeled "coNP". The intersection of the "NP" and "coNP" circles is labeled "P".

Venn diagram showing the relationship between complexity classes EXPTIME, NP, and coNP.

- **P**: problemas decididos em tempo polinomial (determinístico)
- **NP**: problemas verificáveis em tempo polinomial e resolvidos em tempo polinomial por MT não-determinística
- **coNP**: problemas cujos “não” podem ser verificados em tempo polinomial

{11}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8e14350b4b669119a3bdfca7869110ca_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Venn diagram showing the relationship between complexity classes EXPTIME, NP, and coNP.
<!-- /IMAGE_DESCRIPTION -->
### Classes de Complexidade de Tempo
### Definições Básicas

- **DTIME** $(f(n)) = \{L \mid \exists \text{ MT determinística decide } L \text{ em tempo } O(f(n))\}$
- **NTIME** $(f(n)) = \{L \mid \exists \text{ MT não-determinística decide } L \text{ em tempo } O(f(n))\}$
### Classes Determinísticas

- $P = \bigcup_{k \geq 0} \text{DTIME}(n^k)$  tempo polinomial
- $\text{EXPTIME} = \bigcup_{k \geq 0} \text{DTIME}(2^{n^k})$  tempo exponencial
### Classes Não-determinísticas

$$\text{NP} = \bigcup_{k \geq 0} \text{NTIME}(n^k) \quad (\text{tempo polinomial não-determinístico})$$

{12}------------------------------------------------
### Sobre a classe NP...
#### Leitura Correta de NP

Problemas decididos em tempo polinomial por MT não-determinística, ou equivalentemente, problemas com certificados verificáveis em tempo polinomial.

[11]
#### Alerta!

A definição de NP é sobre o tipo de máquina e o tempo de execução, não sobre o crescimento da função. Muitos problemas em NP têm algoritmos polinomiais conhecidos, então NP inclui problemas com tempo de execução polinomial.

**Nunca dizer:** “NP é o conjunto de problemas que não têm algoritmos polinomiais”.

{13}------------------------------------------------
## Classes de Complexidade de Espaço
### Definição Básica

$\text{DSPACE}(f(n)) = \{L \mid \exists \text{ MT determinística } M$   
que decide  $L$  usando espaço  $O(f(n))\}$
### Classes Determinísticas

- $L = \text{DSPACE}(\log n)$  (espaço logarítmico)
- $\text{PSPACE} = \bigcup_{k \geq 0} \text{DSPACE}(n^k)$  (espaço polinomial)
- $\text{EXPSPACE} = \bigcup_{k \geq 0} \text{DSPACE}(2^{n^k})$  (espaço exponencial)
### Classes Não-determinísticas

- $\text{NL} = \text{NSPACE}(\log n)$  (espaço log não-determinístico)
- $\text{NPSPACE} = \bigcup_{k \geq 0} \text{NSPACE}(n^k)$  (espaço polinomial não-determinístico)

{14}------------------------------------------------
### Classes de Complexidade de Espaço - Hierarquia

A Venn diagram illustrating the hierarchy of space complexity classes. It consists of five nested circles. The outermost circle is blue and labeled 'EXPSPACE'. Inside it is a red circle labeled 'PSPACE'. Inside 'PSPACE' are two overlapping circles: a green one labeled 'NL' on the left and a purple one labeled 'NPSPACE' on the right. The intersection of 'NL' and 'NPSPACE' is labeled 'L'.

Venn diagram showing the hierarchy of space complexity classes: L, NL, NPSPACE, PSPACE, and EXPSPACE.

- **L**: problemas decididos em espaço logarítmico (DMT)
- **NL**: problemas decididos em espaço logarítmico (NMT)
- **PSPACE**: problemas decididos em espaço polinomial (DMT)
- **NPSPACE**: prob. decididos em espaço polinomial (NMT)
- **EXPSPACE**: problemas decididos em espaço exponencial

{15}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-bffdddb47fced140f8d17fdc2a29f592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Venn diagram showing the hierarchy of space complexity classes: L, NL, NPSPACE, PSPACE, and EXPSPACE.
<!-- /IMAGE_DESCRIPTION -->
### Relações entre Tempo e Espaço
### Teoremas

**1**  $\text{DTIME}(f(n)) \subseteq \text{DSpace}(f(n))$

*Justificativa:* Em  $f(n)$  passos, não podemos usar mais que  $f(n)$  células. [11]

**2**  $\text{DSpace}(f(n)) \subseteq \text{DTIME}(2^{O(f(n))})$

*Justificativa:* Número de configurações é no máximo exponencial em espaço. [11]

**3**  $\text{NTIME}(f(n)) \subseteq \text{DSpace}(f(n))$

*Justificativa:* Simular não-determinismo usando espaço para backtracking. [1]

**4**  $\text{NSpace}(f(n)) \subseteq \text{DSpace}(f(n)^2)$  **(Savich)**

*Justificativa:* Espaço não-determinístico pode ser simulado deterministicamente com o quadrado do espaço. [10]

{16}------------------------------------------------
#### Hierarquia de Classes

Diagrama da hierarquia de classes de complexidade computacional, representado por círculos concêntricos:

- EXPSPACE (rosa)
- EXPTIME (laranja)
- PSPACE (amarelo)
- NP/coNP (azul)
- P (verde)

As classes são contidas uma dentro da outra:  $P \subseteq NP/coNP \subseteq PSPACE \subseteq EXPTIME \subseteq EXPSPACE$ .

Diagrama de Venn da hierarquia de classes de complexidade computacional

<!-- IMAGE_DESCRIPTION: datalab-36117e9cb27c58484cd8d3e5f9dc7ac3_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de Venn da hierarquia de classes de complexidade computacional
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-55136bc716146672fc680fa05989f1d2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama das classes de complexidade computacional
<!-- /IMAGE_DESCRIPTION -->
#### Questões em Aberto

$P \stackrel{?}{=} NP$ ,  $NP \stackrel{?}{=} coNP$ ,  $NP \stackrel{?}{=} PSPACE$

{17}------------------------------------------------
#### Teorema da Hierarquia de Tempo

Se  $f(n) \log f(n) = o(g(n))$ , então:

$$\text{DTIME}(f(n)) \subsetneq \text{DTIME}(g(n))$$
##### O que significa?

- Se  $g(n)$  cresce significativamente mais que  $f(n) \log f(n)$ , então existem problemas resolúveis em tempo  $O(g(n))$  que **não** são resolúveis em tempo  $O(f(n))$  [6, 1].
- Exemplo:  $\text{DTIME}(n^2) \subsetneq \text{DTIME}(n^3)$  (pois  $n^2 \log n = o(n^3)$ )
##### Problemas fora de P existem...

Deixar a máquina rodar mais tempo (sob a condição  $f(n) \log f(n) = o(g(n))$ ) permite resolver problemas **estritamente mais difíceis**. O fator  $\log f(n)$  é o overhead de simulação.

$$P = \bigcup_k \text{DTIME}(n^k) \subsetneq \text{EXPTIME} = \bigcup_k \text{DTIME}(2^{n^k})$$

{18}------------------------------------------------
#### Teorema da Hierarquia de Espaço

Se  $f(n) = o(g(n))$ , então:

$$\text{DSPACE}(f(n)) \subsetneq \text{DSPACE}(g(n))$$
##### O que significa?

- Mais espaço disponível  $\Rightarrow$  estritamente mais problemas resolúveis.
- Diferente do tempo: não há fator logarítmico (overhead é menor).
- Exemplo:  $\text{DSPACE}(n) \subsetneq \text{DSPACE}(n^2)$  (pois  $n = o(n^2)$ )
##### Por que diferente do tempo?

A simulação de espaço é mais eficiente que a de tempo. Não precisamos recomputar, apenas ler/escrever a fita.

{19}------------------------------------------------
#### Consequências dos Teoremas de Hierarquia
#### Hierarquias Estritas Estabelecidas

- $P \subsetneq \text{EXPTIME}$  (tempo: gaps hierárquicos)
- $\text{PSPACE} \subsetneq \text{EXPSPACE}$  (espaço: gaps hierárquicos)
- $L \subsetneq \text{PSPACE}$  (log ; polinomial)
#### O que NÃO sabemos?

- $P \stackrel{?}{=} \text{NP}$  (um dos Millennium Prize Problems do Clay Mathematics Institute, com prêmio de US\$ 1 milhão [2])
- $\text{NP} \stackrel{?}{\subsetneq} \text{PSPACE}$
- $\text{NL} \stackrel{?}{=} L$  (não-determinismo em espaço log)

{20}------------------------------------------------
#### Teorema de Savitch
##### Teorema de Savitch (1970)

Para  $f(n) \geq \log n$ :

$$\text{NSPACE}(f(n)) \subseteq \text{DSPACE}(f(n)^2)$$

[10]
##### Consequência Importante

$$\text{PSPACE} = \text{NPSPACE}$$

Não-determinismo não ajuda significativamente para espaço!  
(Contraste com P vs NP para tempo.)
#### Ideia da Prova

Usar busca recursiva para verificar se existe caminho de uma configuração a outra, usando espaço quadrático para armazenar a recursão.

{21}------------------------------------------------
### Comparando Tempo e Espaço
### Hierarquia de Classes

$$L \subseteq NL \subseteq P \subseteq NP \subseteq PSPACE \subseteq EXPTIME \subseteq EXPSPACE$$

Relações-chave:

- $DTIME(f(n)) \subseteq DSPACE(f(n))$  (tempo  $\leq$  espaço)
- $DSPACE(f(n)) \subseteq DTIME(2^{O(f(n))})$  (espaço implica tempo exponencial)
- $NP \subseteq PSPACE$  (Savitch)
#### Tabela Resumida

| Classe  | Definição                 | Intuição                         |
|---------|---------------------------|----------------------------------|
| L       | Espaço logarítmico (det.) | Muito pouca memória              |
| NL      | Espaço logarítmico (ND)   | Pouca memória + não-determinismo |
| P       | Tempo polinomial (det.)   | Tratável (em sentido clássico)   |
| NP      | Tempo polinomial (ND)     | Certificados verificáveis        |
| PSPACE  | Espaço polinomial         | Memória controlada               |
| EXPTIME | Tempo exponencial (det.)  | Custo explode com $n$            |

{22}------------------------------------------------
### Reduções
#### Redução Polinomial (Karp)

Uma linguagem  $A$  é **redutível em tempo polinomial** a  $B$ , escrito  $A \leq_p B$ , se existe função  $f$  computável em tempo polinomial tal que:

$$w \in A \iff f(w) \in B$$

[8, 11]

The diagram shows a horizontal flow from left to right. On the left, a box labeled 'Instância de A' is positioned above the text  $w \in A$ . An arrow points from this box to a box on the right labeled 'Instância de B'. Above the arrow is the text  $f$  (polinomial). Below the right box is the text  $f(w) \in B$ .

Diagram illustrating a polynomial-time reduction f from an instance of A to an instance of B.

<!-- IMAGE_DESCRIPTION: datalab-86d30a7d5a9cd4ee5456b5962ae3420a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram illustrating a polynomial-time reduction f from an instance of A to an instance of B.
<!-- /IMAGE_DESCRIPTION -->
### Intuição

Se  $A \leq_p B$ : resolver  $B$  é pelo menos tão difícil quanto resolver  $A$ .

{23}------------------------------------------------
## Hard e Complete
### Definições para uma Classe $\mathcal{C}$

$\mathcal{C}$ -hard Um problema  $B$  é  $\mathcal{C}$ -hard se:

$$\forall A \in \mathcal{C} : A \leq_p B$$

Todo problema em  $\mathcal{C}$  se reduz a  $B$ .

$\mathcal{C}$ -complete Um problema  $B$  é  $\mathcal{C}$ -complete se:

- 1  $B \in \mathcal{C}$  (está na classe)
- 2  $B$  é  $\mathcal{C}$ -hard (é tão difícil quanto qualquer problema na classe)
#### Intuição

- **Hard:** pelo menos tão difícil quanto a classe inteira
- **Complete:** representante “mais difícil” da classe

{24}------------------------------------------------
#### Visualização: Hard vs Complete

Classe  $\mathcal{C}$

$\mathcal{C}$ -complete

Hard

Hard

$\mathcal{C}$ -hard

Diagram illustrating the relationship between a complexity class C and its complete and hard problems. A large light blue oval labeled 'Classe C' contains a smaller red oval labeled 'C-complete'. Two dashed arrows point from the 'C-complete' oval to two separate orange circles, each labeled 'Hard'. To the right of these circles is the label 'C-hard'.

<!-- IMAGE_DESCRIPTION: datalab-8d325fc12b494e42c9ea7ed2a7f327a6_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram illustrating the relationship between a complexity class C and its complete and hard problems.
<!-- /IMAGE_DESCRIPTION -->
#### Relação

$$\mathcal{C}\text{-complete} = \mathcal{C}\text{-hard} \cap \mathcal{C}$$

Problemas complete estão “no topo” da classe.

{25}------------------------------------------------
#### Por que Complete é Importante?
#### Propriedade Fundamental

Se  $B$  é  $\mathcal{C}$ -complete e  $B \in \mathcal{D}$  (outra classe), então:

$$\mathcal{C} \subseteq \mathcal{D}$$
#### Exemplo: P vs NP

Se algum problema NP-complete estiver em P:

$$\text{NP} = \text{P}$$

Resolver **um** problema NP-complete eficientemente resolve **todos**.  
[4, 8]
#### Consequência Prática

Provar que um problema é NP-complete é forte evidência de que não existe algoritmo polinomial para ele **assumindo que  $\text{P} \neq \text{NP}$** .

{26}------------------------------------------------
## Intratabilidade
### O que é “Intratável”?

Em teoria da complexidade, chamamos de **intratável** um problema para o qual não conhecemos algoritmo polinomial geral e há forte evidência de que ele não exista.
### Evidências de Intratabilidade

- 1 Problema é NP-hard (sob a hipótese  $P \neq NP$ )
- 2 Problema é PSPACE-hard
- 3 Problema é EXPTIME-complete
- 4 Problema requer tempo/espço super-polinomial (provado)
#### “Intratável” não significa “impossível”!

- Instâncias pequenas podem ser resolvidas
- Aproximações podem ser eficientes
- Casos especiais podem ser tratáveis

{27}------------------------------------------------
### Lidando com Intratabilidade
### Estratégias Práticas
#### 1 Algoritmos Aproximados

- Encontrar solução “boa o suficiente”
- Garantias de qualidade (ex: 2-aproximação)
#### 2 Heurísticas

- Funcionam bem na prática, sem garantias
- Ex: algoritmos genéticos, simulated annealing
#### 3 Parametrização

- Algoritmos FPT:  $O(f(k) \cdot n^c)$  para parâmetro  $k$
- Tratável se  $k$  é pequeno
#### 4 Casos Especiais

- Restrições na entrada podem tornar tratável
- Ex: 2-SAT é em P, mas 3-SAT é NP-complete

{28}------------------------------------------------
## Mapa das Classes

O diagrama mostra uma hierarquia de classes de complexidade computacional representada por quatro ovais concêntricos. O maior oval amarelo no exterior é rotulado 'Decidíveis' e 'EXPTIME'. Dentro dele, um oval verde é rotulado 'PSPACE'. Dentro do verde, um oval azul é rotulado 'NP'. O menor oval no centro, em rosa, é rotulado 'P'.

Diagrama das classes de complexidade computacional

EXPTIME-complete: xadrez/damas

PSPACE-complete: QBF

NP-complete: SAT, TSP (decisão)

P: Ordenação, Caminho mínimo

QBF = Quantified Boolean Formula

SAT = Satisfiability

TSP = Traveling Salesman Problem

{29}------------------------------------------------
## Resumo
## Conceitos Principais

- **Complexidade** mede recursos necessários para computação
- **Tempo** e **espaço** são os recursos fundamentais
- Classes: P, NP, PSPACE, EXPTIME, L, NL, ...
- **Hard**: tão difícil quanto toda a classe
- **Complete**: hard + está na classe
- **Intratabilidade**: ausência de algoritmo polinomial
### Importância

Entender a complexidade e as classes de problemas é crucial para:

- Avaliar a viabilidade de algoritmos
- Escolher abordagens práticas
- Avançar na teoria da computação

{30}------------------------------------------------
### Leituras Recomendadas
### Livros-base

- **Sipser [11]**: introdução clara para P, NP, reduções e indecidibilidade.
- **Hopcroft–Motwani–Ullman [7]**: base formal em linguagens, autômatos e complexidade.
- **Arora–Barak [1]**: tratamento moderno e mais profundo de complexidade computacional.
- **Papadimitriou [9]**: referência clássica para classes e completude.
### Artigos clássicos

- Hierarquia de tempo: Hartmanis e Stearns [6]
- Cobham–Edmonds e tratabilidade polinomial: Cobham [3], Edmonds [5]

{31}------------------------------------------------
### Exercício 1: Notação Assintótica

Classifique as seguintes funções em ordem crescente de crescimento assintótico:

$$n^2, \quad 2^n, \quad n \log n, \quad n!, \quad \log n, \quad n^3, \quad n, \quad 2^{2^n}$$

Para cada par consecutivo  $f(n)$  e  $g(n)$  na sua ordenação, determine:

- $f(n) = O(g(n))$ ?
- $f(n) = o(g(n))$ ?
- $f(n) = \Theta(g(n))$ ?

Lembre:  $f(n) = O(g(n))$  significa que  $f$  cresce no máximo tão rápido quanto  $g$ , enquanto  $f(n) = o(g(n))$  significa que  $f$  cresce estritamente mais devagar que  $g$ .

{32}------------------------------------------------
### Exercício 2: Classificação de Complexidade

Determine a complexidade de tempo (em notação  $O$ ) dos seguintes algoritmos:

- 1 Verificar se um número  $n$  é primo testando divisores até  $\sqrt{n}$
- 2 Encontrar o elemento máximo em um array de  $n$  elementos
- 3 Multiplicar duas matrizes  $n \times n$  pelo algoritmo ingênuo
- 4 Calcular  $a^n \bmod m$  usando exponenciação binária
- 5 Gerar todas as permutações de  $n$  elementos

{33}------------------------------------------------
### Exercício 3: Relações entre Classes

- 1 Prove que  $DTIME(n) \subseteq DSPACE(n)$ .
- 2 Por que  $DSPACE(n) \subseteq DTIME(2^{O(n)})$ ? Quantas configurações distintas uma MT pode ter usando espaço  $n$ ?
- 3 Mostre que  $P \subseteq PSPACE$ .
- 4 Use o Teorema de Savitch para mostrar que  $NPSPACE = PSPACE$ .
- 5 Por que não podemos usar um argumento similar para provar  $P = NP$ ?

{34}------------------------------------------------
### Exercício 4: Hard e Complete

- 1 Explique a diferença entre NP-hard e NP-complete com um exemplo.
- 2 Se um problema é NP-hard mas não está em NP, ele pode ser NP-complete?
- 3 Suponha que descobrimos que um problema NP-complete  $A$  pode ser resolvido em tempo  $O(n^{100})$ . O que isso implica?
- 4 Se  $A \leq_p B$  e  $B \leq_p A$ , o que podemos concluir sobre a dificuldade relativa de  $A$  e  $B$ ?

{35}------------------------------------------------
### Exercício 5: Roteiro de Redução
#### Objetivo

Queremos mostrar que **CLIQUE** é NP-complete a partir de um problema já conhecido difícil, como 3-SAT.

- 1 Qual problema deve ser usado como **fonte** da redução: um problema fácil ou um problema já conhecido NP-hard?
- 2 Qual deve ser o formato da transformação: uma fórmula  $\varphi$  deve virar que tipo de instância  $(G, k)$ ?
- 3 Que equivalência precisa ser provada para a redução funcionar?

$$\varphi \in 3\text{-SAT} \iff (G, k) \in \text{CLIQUE}$$

- 4 Por que a transformação precisa ser computável em tempo polinomial?
- 5 Depois de provar NP-hardness, o que ainda falta mostrar para concluir que **CLIQUE** é NP-complete?

{36}------------------------------------------------
### Exercício 6: Hierarquia

- 1 O Teorema da Hierarquia de Tempo garante que  $P \neq \text{EXPTIME}$ . Por quê?
- 2 Sabemos que  $P \subseteq NP \subseteq \text{PSPACE} \subseteq \text{EXPTIME}$ . Quais dessas inclusões são conhecidas como **estritas**?
- 3 Se  $P = \text{PSPACE}$ , o que isso implicaria sobre  $P$  vs  $NP$ ?
- 4 Por que acreditamos que  $P \neq NP$ , mesmo sem prova?

{37}------------------------------------------------
### Exercício 7: Problemas Práticos

Para cada problema abaixo, indique em qual classe você acredita que ele está (P, NP-complete, PSPACE-complete, EXPTIME-complete, ou indecidível) e justifique:

- 1 Verificar se um grafo é bipartido
- 2 Verificar se um grafo possui uma clique de tamanho pelo menos  $k$
- 3 Determinar o vencedor em um jogo de Damas generalizado
- 4 Verificar se uma fórmula booleana quantificada (QBF) é verdadeira
- 5 Verificar se duas gramáticas livres de contexto geram a mesma linguagem

{38}------------------------------------------------
### Exercício 8: Intratabilidade na Prática

- 1 Um algoritmo tem complexidade  $O(2^n)$ . Para  $n = 40$ , quantas operações ele faz? Se cada operação leva 1 nanosegundo, quanto tempo o algoritmo leva?
- 2 O mesmo algoritmo com entrada  $n = 100$ . Isso é viável?
- 3 Um algoritmo  $O(n^3)$  versus um algoritmo  $O(2^n)$ : para qual valor de  $n$  eles levam aproximadamente o mesmo tempo?
- 4 Discuta: por que algoritmos exponenciais às vezes são usados na prática (ex: SAT solvers)?

{39}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009. ISBN: 978-0521424264.
- [2] Clay Mathematics Institute. *P vs NP*. URL: <https://www.claymath.org/millennium/p-vs-np/> (acesso em 15/05/2026).
- [3] Alan Cobham. “The Intrinsic Computational Difficulty of Functions”. Em: *Proceedings of the 1964 International Congress for Logic, Methodology, and Philosophy of Science* (1965), pp. 24–30.

{40}------------------------------------------------
## Referências II

- [4] Stephen A. Cook. “The Complexity of Theorem-Proving Procedures”. Em: *Proceedings of the Third Annual ACM Symposium on Theory of Computing* (1971), pp. 151–158. DOI: [10.1145/800157.805047](https://doi.org/10.1145/800157.805047).
- [5] Jack Edmonds. “Paths, Trees, and Flowers”. Em: *Canadian Journal of Mathematics* 17 (1965), pp. 449–467. DOI: [10.4153/CJM-1965-045-4](https://doi.org/10.4153/CJM-1965-045-4).
- [6] Juris Hartmanis e Richard E. Stearns. “On the Computational Complexity of Algorithms”. Em: *Transactions of the American Mathematical Society* 117 (1965), pp. 285–306. DOI: [10.2307/1994208](https://doi.org/10.2307/1994208).

{41}------------------------------------------------
## Referências III

- [7] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006. ISBN: 978-0321455369.
- [8] Richard M. Karp. “Reducibility Among Combinatorial Problems”. Em: *Complexity of Computer Computations* (1972), pp. 85–103. DOI: [10.1007/978-1-4684-2001-2\\_9](https://doi.org/10.1007/978-1-4684-2001-2_9).
- [9] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994. ISBN: 978-0201530827.
- [10] Walter J. Savitch. “Relationships Between Nondeterministic and Deterministic Tape Complexities”. Em: *Journal of Computer and System Sciences* 4.2 (1970), pp. 177–192. DOI: [10.1016/S0022-0000\(70\)80006-X](https://doi.org/10.1016/S0022-0000(70)80006-X).

{42}------------------------------------------------
## Referências IV

- [11] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012. ISBN: 978-1133187790.

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central panel containing a stylized 'M' and 'U' monogram, flanked by two panels with a repeating pattern of pine trees. Above the shield is a crown, and below it is a banner with the Latin motto 'AD VERVM DVCT'. The entire emblem is rendered in a light gray, semi-transparent style.

Coat of arms of the University of São Paulo (USP)

<!-- IMAGE_DESCRIPTION: datalab-9642ee15d719705144037077981aaa99_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-fa6c61be003dfbb4ca5587e48a71de94_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifícia Universidade Católica do Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->

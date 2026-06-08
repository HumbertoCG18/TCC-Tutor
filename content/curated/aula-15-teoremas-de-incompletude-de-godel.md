<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Kurt Gödel (1906–1978)**
  - Impacto
- **O Programa de Hilbert (Revisitado)**
  - Objetivo de Hilbert
  - Desfechos
- **Sistemas Formais**
  - Definição
  - Exemplo: Aritmética de Peano (PA)
  - Axiomas de Peano
  - Propriedades de Sistemas Formais
  - Definições
  - Relação
  - Números de Gödel
  - Ideia Central
  - Esquema de Codificação
  - Consequência
  - Autoreferência via Numeração
- **O Truque de Gödel**
  - Analogia: Paradoxo do Mentiroso
- **Enunciado do Primeiro Teorema**
- **Primeiro Teorema da Incompletude (Gödel, 1931)**
  - Corolário
- **A Sentença de Gödel**
  - Construção (Informal)
  - Sentença de Gödel
  - Lema da Diagonalização
  - Prova do Primeiro Teorema
  - Análise de $G$
  - Prova do Primeiro Teorema (Continuação)
  - Conclusão
- **Versão "Melhorada" (Rosser, 1936)**
  - Teorema de Rosser
  - Ideia
  - Sentença de Rosser
  - Implicações do Primeiro Teorema
  - Para a Matemática
  - Para a Computação
  - Exemplos de Sentenças Indecidíveis
  - Relação com Computabilidade
  - Teorema
  - Prova (Esboço)
  - Hierarquia
- **Enunciado do Segundo Teorema**
- **Segundo Teorema da Incompletude (Gödel, 1931)**
  - Consistência: Formulação
  - Implicação
  - Prova do Segundo Teorema (Esboço)
  - Ideia
  - Implicações
  - O Segundo Teorema
  - Fim do Programa de Hilbert
  - Exemplo
  - Provas de Consistência Conhecidas
  - Consistência de PA
  - Hierarquia de Teorias
  - Relação entre os Teoremas
  - Conexão
  - Visão Unificada
  - Teoremas de Gödel e Computação
  - Paralelos
  - Conexão Profunda
- **Resumo**
  - Primeiro Teorema da Incompletude
  - Segundo Teorema da Incompletude
- **Consequências**
- **Exercício 1: Conceitos Básicos**
  - Exercício 2: A Sentença de Gödel
- **Exercício 3: Implicações**
- **Exercício 4: Segundo Teorema**
  - Exercício 5: Relação com Computabilidade
  - Exercício 6: Questões Filosóficas
  - Exercício 7: Explorando Limites
- **Desafio**
  - O Problema de Goodstein
  - Desafio: Lema da Diagonalização
- **Enunciado**
- **Referências I**
- **Referências II**
- **Referências III**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Teoremas de Incompletude de Gödel

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 15

Teoria da Computabilidade e Complexidade  
Ciência da Computação

28 de abril de 2026

The logo of the Escola Politécnica of PUCRS, featuring a crest with a star and the text "PUCRS" and "ESCOLA POLITÉCNICA".

Logo of ESCOLA POLITÉCNICA PUCRS

{1}------------------------------------------------

{2}------------------------------------------------
## Kurt Gödel (1906–1978)

- Lógico austro-americano, nascido em **1906** em Brno
- Formou-se em Viena e tornou-se uma figura central da lógica do século XX
- Em **1930**, provou o **Teorema da Completude** da lógica de primeira ordem
- Em **1931**, publicou os **Teoremas da Incompletude**
- Em **1940**, mostrou a consistência relativa do Axioma da Escolha e da Hipótese do Contínuo com ZF
- A partir de **1940**, trabalhou em Princeton, onde conviveu com Einstein
### Impacto

Os resultados de Gödel redefiniram os limites da formalização matemática no século XX.

A black and white portrait of Kurt Gödel. He is an older man with short, light-colored hair, wearing round-rimmed glasses. He is dressed in a dark suit jacket over a light-colored shirt and a dark tie. He is looking directly at the camera with a serious expression. The background is slightly out of focus, showing what appears to be a library or study with bookshelves.

Black and white portrait of Kurt Gödel, an older man with glasses, wearing a suit and tie, standing in front of a bookshelf.

{3}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-9d71890acd754a1325e9415e44a7dacb_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Black and white portrait of Kurt Gödel, an older man with glasses, wearing a suit and tie, standing in front of a bookshelf.
<!-- /IMAGE_DESCRIPTION -->
## O Programa de Hilbert (Revisitado)
### Objetivo de Hilbert

Estabelecer fundamentos sólidos para **toda** a matemática:

- 1 **Formalização:** Expressar matemática em linguagem formal
- 2 **Completude:** Toda verdade é provável
- 3 **Consistência:** Nenhuma contradição é provável
- 4 **Decidibilidade:** Algoritmo para verificar provas
### Desfechos

- **1931:** Gödel prova que os itens 2 e 3 são impossíveis de serem alcançados
- **1936:** Church e Turing provam que o item 4 é impossível

{4}------------------------------------------------
## Sistemas Formais
### Definição

Um **sistema formal**  $S$  consiste de:

- 1 **Linguagem:** símbolos e regras de formação de fórmulas
- 2 **Axiomas:** fórmulas assumidas como verdadeiras
- 3 **Regras de inferência:** formas de derivar novas fórmulas
### Exemplo: Aritmética de Peano (PA)

- Linguagem:  $0, S, +, \cdot, =$ , quantificadores
- Axiomas: propriedades de  $0$ , sucessor, indução
- Regras: modus ponens, generalização

{5}------------------------------------------------
### Axiomas de Peano
#### Axiomas Básicos

- 1  $\forall x : \neg(S(x) = 0)$  (zero não é sucessor)
- 2  $\forall x \forall y : S(x) = S(y) \rightarrow x = y$  (sucessor é injetivo)
- 3  $\forall x : x + 0 = x$  (neutro da adição)
- 4  $\forall x \forall y : x + S(y) = S(x + y)$  (definição recursiva de +)
- 5  $\forall x : x \cdot 0 = 0$  (elemento absorvente)
- 6  $\forall x \forall y : x \cdot S(y) = x \cdot y + x$  (definição recursiva de ·)
#### Indução

Para cada fórmula  $\phi(x)$ :

$$[\phi(0) \wedge \forall x(\phi(x) \rightarrow \phi(S(x)))] \rightarrow \forall x\phi(x)$$

{6}------------------------------------------------
### Propriedades de Sistemas Formais
### Definições

**Consistente**  $S$  é consistente se não existe  $\phi$  tal que  $S \vdash \phi$  e  $S \vdash \neg\phi$

**Completo**  $S$  é completo se para toda sentença  $\phi$ :  $S \vdash \phi$  ou  $S \vdash \neg\phi$

**$\omega$ -consistente**  $S$  é  $\omega$ -consistente se não existe  $\phi(x)$  tal que  $S \vdash \exists x \neg\phi(x)$  mas  $S \vdash \phi(0), \phi(1), \phi(2), \dots$  para todo numeral
### Relação

$\omega$ -consistência  $\Rightarrow$  consistência (mas não o contrário)

{7}------------------------------------------------
### Números de Gödel
### Ideia Central

Codificar fórmulas, provas e teoremas como **números naturais**. Isso permite que a aritmética possa “referenciar a si mesma”.
### Esquema de Codificação

- Cada símbolo recebe um código numérico
- Sequências são codificadas usando potências de primos:

$$\langle a_1, a_2, \dots, a_n \rangle = 2^{a_1} \cdot 3^{a_2} \cdot 5^{a_3} \dots p_n^{a_n}$$

- Fórmulas, provas e programas tornam-se números
### Consequência

“ $\phi$  é provável em  $S$ ” torna-se uma afirmação sobre números!

{8}------------------------------------------------
### Autoreferência via Numeração
## O Truque de Gödel

Usando a numeração, podemos construir uma fórmula que “fala sobre si mesma”:

$G$ : “A fórmula com número de Gödel  $\#G$  não é provável em  $S$ ”

Ou seja:  $G$  diz “Eu não sou provável”.
### Analogia: Paradoxo do Mentiroso

“Esta frase é falsa.”

Mas  $G$  não é um paradoxo; é uma sentença **bem-formada** com valor-verdade definido.

{9}------------------------------------------------
## Enunciado do Primeiro Teorema
## Primeiro Teorema da Incompletude (Gödel, 1931)

Para qualquer sistema formal  $S$  que seja:

- **Consistente**
- **Efetivamente axiomatizável** (axiomas são decidíveis)
- Capaz de expressar **aritmética básica**

Existem sentenças aritméticas que são **verdadeiras** mas **não prováveis** em  $S$ .

Em particular, existe uma sentença  $G$  tal que nem  $G$  nem  $\neg G$  são prováveis em  $S$ .
### Corolário

Nenhum sistema formal consistente e suficientemente expressivo pode ser **completo**.

{10}------------------------------------------------
## A Sentença de Gödel
### Construção (Informal)

Seja  $Prov_S(x)$  uma fórmula aritmética que significa “ $x$  é o número de Gödel de uma fórmula provável em  $S$ ”.

Usando o **Lema da Diagonalização**, construímos  $G$  tal que:

$$G \leftrightarrow \neg Prov_S(\#G)$$
### Sentença de Gödel

“Eu não sou provável em  $S$ ”
### Lema da Diagonalização

Para qualquer fórmula  $\phi(x)$ , existe uma sentença  $\psi$  tal que:

$$S \vdash \psi \leftrightarrow \phi(\# \psi)$$

{11}------------------------------------------------
### Prova do Primeiro Teorema
### Análise de $G$

Lembre:  $G \leftrightarrow \neg \text{Prov}_S(\#G)$ , i.e.,  $G$  diz “Eu não sou provável”.
#### Caso 1: Suponha $S \vdash G$

- Se  $G$  é provável, então  $\text{Prov}_S(\#G)$  é verdade
- Mas  $G$  afirma  $\neg \text{Prov}_S(\#G)$
- Logo,  $G$  é falsa, mas provável
- Isso significa que  $S$  prova uma falsidade
- Se  $S$  é  $\omega$ -**consistente**, isso é contradição

{12}------------------------------------------------
### Prova do Primeiro Teorema (Continuação)
#### Caso 2: Suponha $S \vdash \neg G$

- $\neg G$  afirma  $Prov_S(\#G)$ , i.e., “ $G$  é provável”
- Se  $S$  prova  $\neg G$ , então  $S$  afirma que  $G$  é provável
- Mas assumimos que  $S \not\vdash G$
- $S$  estaria afirmando algo falso sobre si mesmo
- Com  $\omega$ -consistência, isso é contradição
### Conclusão

Se  $S$  é  $\omega$ -consistente, então:

$$S \not\vdash G \quad \text{e} \quad S \not\vdash \neg G$$

$G$  é **indecidível** em  $S$ , mas **verdadeira** (pois realmente não é provável).

{13}------------------------------------------------
## Versão "Melhorada" (Rosser, 1936)
### Teorema de Rosser

O primeiro teorema de Gödel vale assumindo apenas **consistência** (não precisa de  $\omega$ -consistência).
### Ideia

Rosser construiu uma sentença  $R$  mais engenhosa, que permite obter incompletude apenas com consistência simples.
### Sentença de Rosser

"Se existe prova de mim, então existe prova menor de minha negação."

{14}------------------------------------------------
### Implicações do Primeiro Teorema
### Para a Matemática

- Existem verdades aritméticas **inacessíveis** por prova formal
- Não importa quantos axiomas adicionemos: **sempre haverá lacunas**
- A “lista completa de verdades matemáticas” é impossível
### Para a Computação

- Provabilidade é semi-decidível (enumerar provas)
- Verdade aritmética não é nem mesmo semi-decidível
### Exemplos de Sentenças Indecidíveis

- A própria sentença de Gödel  $G$
- Hipótese do Contínuo (em ZFC)
- Certas propriedades de equações Diofantinas

{15}------------------------------------------------
### Relação com Computabilidade
### Teorema

O conjunto das sentenças verdadeiras da aritmética ( $Th(\mathbb{N})$ ) não é Turing-reconhecível.
### Prova (Esboço)

- O Problema da Parada pode ser codificado em aritmética
- “MT  $M$  para em  $w$ ” é equivalente a uma sentença aritmética  $\phi_{M,w}$
- Se  $Th(\mathbb{N})$  fosse reconhecível,  $HALT$  seria decidível
### Hierarquia

Prováveis  $\subset$  Verdadeiros  $\subset$  Sentenças

i.e. a diferença “Verdadeiros — Prováveis” é não-vazia!

{16}------------------------------------------------
## Enunciado do Segundo Teorema
## Segundo Teorema da Incompletude (Gödel, 1931)

Para qualquer sistema formal  $S$  que seja:

- **Consistente**
- **Efetivamente axiomatizável**
- Capaz de expressar **aritmética básica**

**$S$  não pode provar sua própria consistência.**

Formalmente:  $S \not\vdash Con(S)$

onde  $Con(S)$  é a fórmula aritmética que expressa “ $S$  é consistente”.

{17}------------------------------------------------
### Consistência: Formulação

O que significa “ $S$  é consistente”?

- Não existe fórmula  $\phi$  tal que  $S \vdash \phi$  e  $S \vdash \neg\phi$
- Equivalentemente:  $S \not\vdash (0 = 1)$

Usando numeração de Gödel:

$$Con(S) \equiv \neg Prov_S(\#(0 = 1))$$

“Não existe prova de  $0 = 1$  em  $S$ ”
### Implicação

Se  $S$  pudesse provar  $Con(S)$ , então  $S$  poderia provar que  $G$  (sentença de Gödel) é verdadeira, o que é impossível pelo primeiro teorema.

{18}------------------------------------------------
### Prova do Segundo Teorema (Esboço)
### Ideia

Mostrar que dentro de  $S$ :

$$S \vdash \text{Con}(S) \rightarrow G$$

onde  $G$  é a sentença de Gödel (“Eu não sou provável”).
#### Argumento

- 1 Se  $S$  é consistente, então  $G$  é verdadeira (pelo primeiro teorema)
- 2 Esta implicação pode ser **formalizada** dentro de  $S$
- 3 Logo,  $S \vdash \text{Con}(S) \rightarrow G$
- 4 Se  $S \vdash \text{Con}(S)$ , então  $S \vdash G$
- 5 Mas sabemos que  $S \not\vdash G$  (primeiro teorema)
- 6 Portanto,  $S \not\vdash \text{Con}(S)$

{19}------------------------------------------------
### Implicações
### O Segundo Teorema

- A matemática não pode “justificar a si mesma”
- Precisamos de um sistema **mais forte** para provar consistência. Porém, esse sistema maior também não pode provar sua própria consistência
### Fim do Programa de Hilbert

Hilbert queria provar consistência da matemática usando métodos “finitários” (mais fracos). Gödel mostrou que isso é impossível.
### Exemplo

- **PA** (Peano Arithmetic) = Aritmética de Peano
- **ZFC** (Zermelo-Fraenkel + Choice) = Teoria axiomática de conjuntos

PA não prova  $Con(PA)$ , mas ZFC (teoria de conjuntos) pode.

{20}------------------------------------------------
### Provas de Consistência Conhecidas
### Consistência de PA

Gentzen (1936) provou a consistência de PA usando:

- Indução transfinita até  $\varepsilon_0$
- Este método vai além do que PA pode expressar
- Confirma o segundo teorema (precisa de sistema mais forte)
### Hierarquia de Teorias

Diagrama hierárquico de teorias matemáticas:

- PA
- $\uparrow$ prova  $Con(PA)$
- ZFC
- $\uparrow$ prova  $Con(ZFC)$
- ZFC + Grandes Cardinais
- $\vdots$

Diagrama hierárquico de teorias matemáticas mostrando a relação de consistência entre elas.

{21}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-7ede87328f6b696dcffa65ebc4570cc8_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama hierárquico de teorias matemáticas mostrando a relação de consistência entre elas.
<!-- /IMAGE_DESCRIPTION -->
### Relação entre os Teoremas
### Conexão

- **Primeiro Teorema:** Existem verdades não-prováveis
- **Segundo Teorema:** Consistência é uma delas
- O segundo teorema é “mais forte”, porém o primeiro já mostra a incompletude
### Visão Unificada

Ambos os teoremas derivam da **autoreferência**: capacidade de um sistema “falar de si mesmo”.

- Sistemas suficientemente expressivos podem falar sobre si mesmos, mas acabam criando “pontos cegos”
- Nenhum **sistema finito** captura toda a verdade

{22}------------------------------------------------
### Teoremas de Gödel e Computação
### Paralelos

| Lógica (Gödel)        | Computação (Turing)             |
|-----------------------|---------------------------------|
| Sentença de Gödel $G$ | Máquina $D$ (diagonal)          |
| Numeração de Gödel    | Codificação $\langle M \rangle$ |
| Provabilidade         | Decidibilidade                  |
| Incompletude          | Indecidibilidade                |
| Autoreferência        | Auto-aplicação                  |
### Conexão Profunda

Os resultados de Gödel (1931) precederam e inspiraram os de Turing (1936). A indecidibilidade do Problema da Parada é, em essência, uma “versão computacional” da incompletude.

{23}------------------------------------------------
## Resumo
### Primeiro Teorema da Incompletude

Todo sistema formal consistente e suficientemente expressivo contém sentenças verdadeiras não-prováveis.
### Segundo Teorema da Incompletude

Tal sistema não pode provar sua própria consistência.
## Consequências

- A matemática não pode ser completamente formalizada
- Verdade  $\neq$  Provabilidade
- Existem limites fundamentais para sistemas formais
- Relaciona-se profundamente com limites da computação

{24}------------------------------------------------
## Exercício 1: Conceitos Básicos

- 1 Explique a diferença entre **consistência** e **completude** de um sistema formal.
- 2 O que significa um sistema ser  $\omega$ -**consistente**? Por que essa propriedade é mais forte que consistência simples?
- 3 Por que a numeração de Gödel é essencial para a prova dos teoremas de incompletude?
- 4 Qual é a diferença entre “verdadeiro” e “provável” no contexto dos teoremas de Gödel?

{25}------------------------------------------------
### Exercício 2: A Sentença de Gödel

- 1 A sentença de Gödel  $G$  afirma “Eu não sou provável em  $S$ ”. Se  $S$  é consistente,  $G$  é verdadeira ou falsa? Justifique.
- 2 Por que  $G$  não é um paradoxo como o “Paradoxo do Mentiroso” (“Esta frase é falsa”)?
- 3 Se adicionarmos  $G$  como axioma a  $S$ , obtemos um sistema  $S' = S + G$ . O sistema  $S'$  é completo? Há uma nova sentença de Gödel para  $S'$ ?
- 4 Considere adicionar  $\neg G$  como axioma. O que acontece com o sistema resultante?

{26}------------------------------------------------
## Exercício 3: Implicações

- 1 O primeiro teorema de Gödel implica que existem infinitas sentenças indecidíveis em PA? Justifique.
- 2 Se um sistema  $S$  é **inconsistente**, os teoremas de Gödel se aplicam? Por quê?
- 3 A aritmética de Presburger (adição sem multiplicação) é completa e decidível. Por que os teoremas de Gödel não se aplicam a ela?
- 4 Dê um exemplo de sistema formal que é completo e consistente. Por que os teoremas de Gödel não se aplicam?

{27}------------------------------------------------
## Exercício 4: Segundo Teorema

- 1 Explique informalmente por que  $S \vdash \text{Con}(S) \rightarrow G$ .
- 2 Se PA não pode provar  $\text{Con}(PA)$ , como sabemos que PA é consistente?
- 3 ZFC pode provar  $\text{Con}(PA)$ . Isso contradiz o segundo teorema? Explique.
- 4 Se alguém encontrar uma prova de  $\text{Con}(ZFC)$  dentro de ZFC, o que isso implicaria sobre ZFC?

{28}------------------------------------------------
### Exercício 5: Relação com Computabilidade

- 1 Compare a sentença de Gödel  $G$  com a máquina diagonal  $D$  na prova da indecidibilidade do Problema da Parada.
- 2 Por que o conjunto de sentenças verdadeiras da aritmética não é Turing-reconhecível?
- 3 O conjunto de sentenças **prováveis** em PA é decidível? É reconhecível?
- 4 Relacione o Teorema de Rice com o primeiro teorema de incompletude.

{29}------------------------------------------------
### Exercício 6: Questões Filosóficas

- 1** Os teoremas de Gödel mostram que existem verdades matemáticas que humanos nunca poderão conhecer?
- 2** Alguns argumentam que os teoremas de Gödel mostram que a mente humana é superior a máquinas. Critique este argumento.
- 3** O segundo teorema implica que nunca teremos certeza absoluta de que a matemática é livre de contradições?
- 4** Hilbert disse “Wir müssen wissen. Wir werden wissen.” (Devemos saber. Saberemos.) Como os teoremas de Gödel respondem a esta afirmação?

{30}------------------------------------------------
### Exercício 7: Explorando Limites

- 1** O Teorema da Completude de Gödel (1930) diz que a lógica de primeira ordem é completa. Como isso é compatível com os teoremas de incompletude (1931)?  
*Dica:* Há uma diferença entre completude da lógica e completude de uma teoria específica.
- 2** Considere a “teoria verdadeira da aritmética”  $Th(\mathbb{N})$  = todas as sentenças verdadeiras sobre  $\mathbb{N}$ . Esta teoria é completa? É efetivamente axiomatizável?
- 3** Por que não podemos “escapar” da incompletude simplesmente adicionando todas as sentenças verdadeiras como axiomas?

{31}------------------------------------------------
## Desafio
### O Problema de Goodstein

A sequência de Goodstein de um número  $n$  é definida por um processo que envolve representação em bases e operações específicas.

**Teorema de Goodstein (1944):** Toda sequência de Goodstein eventualmente chega a zero.

- 1 Este teorema é uma sentença aritmética (sobre números naturais).
- 2 Kirby e Paris (1982) mostraram que o Teorema de Goodstein é **verdadeiro mas não provável em PA**.
- 3 Como isso exemplifica o primeiro teorema de Gödel?
- 4 O teorema pode ser provado em ZFC. O que isso nos diz sobre a “força” de diferentes sistemas?

{32}------------------------------------------------
### Desafio: Lema da Diagonalização
## Enunciado

Para qualquer fórmula  $\phi(x)$  com uma variável livre, existe uma sentença  $\psi$  tal que:

$$PA \vdash \psi \leftrightarrow \phi(\# \psi)$$

- 1 Explique intuitivamente o que este lema permite fazer.
- 2 Use o lema para construir uma sentença que diz “Eu tenho uma prova com menos de 1000 símbolos.”
- 3 Por que este lema é chamado de “diagonalização”? Relacione com o argumento diagonal de Cantor.
- 4 O lema é a ferramenta chave para construir  $G$ . Mostre como usá-lo com  $\phi(x) = \neg Prov(x)$ .

{33}------------------------------------------------
## Referências I

- [1] Martin Davis, ed. *The Undecidable: Basic Papers on Undecidable Propositions, Unsolvable Problems and Computable Functions*. Raven Press, 1965.
- [2] Torkel Franzén. *Gödel's Theorem: An Incomplete Guide to Its Use and Abuse*. A K Peters, 2005. ISBN: 978-1568812380.
- [3] Gerhard Gentzen. “Die Widerspruchsfreiheit der reinen Zahlentheorie”. Em: *Mathematische Annalen* 112.1 (1936), pp. 493–565. DOI: [10.1007/BF01565428](https://doi.org/10.1007/BF01565428).
- [4] Kurt Gödel. “Die Vollständigkeit der Axiome des logischen Funktionenkalküls”. Em: *Monatshefte für Mathematik und Physik* 37.1 (1930), pp. 349–360. DOI: [10.1007/BF01696781](https://doi.org/10.1007/BF01696781).

{34}------------------------------------------------
## Referências II

- [5] Kurt Gödel. “Über formal unentscheidbare Sätze der Principia Mathematica und verwandter Systeme I”. Em: *Monatshefte für Mathematik und Physik* 38.1 (1931), pp. 173–198. DOI: [10.1007/BF01700692](https://doi.org/10.1007/BF01700692).
- [6] David Hilbert e Wilhelm Ackermann. *Grundzüge der theoretischen Logik*. Berlin: Springer, 1928.
- [7] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006. ISBN: 978-0321455369.
- [8] Ernest Nagel e James R. Newman. *Gödel's Proof*. Revised. New York University Press, 2001. ISBN: 978-0814758168.

{35}------------------------------------------------
## Referências III

- [9] J. Barkley Rosser. “Extensions of Some Theorems of Gödel and Church”. Em: *The Journal of Symbolic Logic* 1.3 (1936), pp. 87–91. DOI: [10.2307/2269028](https://doi.org/10.2307/2269028).
- [10] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012. ISBN: 978-1133187790.
- [11] Raymond M. Smullyan. *Gödel's Incompleteness Theorems*. Oxford University Press, 1992. ISBN: 978-0195046724.
- [12] Alan M. Turing. “On Computable Numbers, with an Application to the Entscheidungsproblem”. Em: *Proceedings of the London Mathematical Society* s2-42.1 (1937), pp. 230–265. DOI: [10.1112/plms/s2-42.1.230](https://doi.org/10.1112/plms/s2-42.1.230).

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-d3294dc879b451b369c0b06f42e9b39f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of ESCOLA POLITÉCNICA PUCRS
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->
